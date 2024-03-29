# Potion 段移动

# Potion 段移动

既然知道了段移动的工作原理，让我们重新映射这些命令来使得它们对于 Potion 文件起作用。

首先我们要决定 Potion 文件中"段"的意义。 有两对段移动命令，所以我们可以总结出两套组合，我们的用户可以选择自己喜欢的一个。

让我们使用下面两个组合来决定哪里是 Potion 中的段：

1.  任何在空行之后的，第一个字符为非空字符的行，以及文件首行。
2.  任何第一个字符为非空字符，包括一个等于号，并以冒号结尾的行。

稍微拓展我们的`factorial.pn`例子，这就是那些规则当作段头的地方：

```
:::text
# factorial.pn                              1
# Print some factorials, just for fun.

factorial = (n):                            1 2
    total = 1

    n to 1 (i):
        total *= i.

    total.

print_line = ():                            1 2
    "-=-=-=-=-=-=-=-\n" print.

print_factorial = (i):                      1 2
    i string print
    '! is: ' print
    factorial (i) string print
    "\n" print.

"Here are some factorials:\n\n" print       1

print_line ()                               1
10 times (i):
    print_factorial (i).
print_line () 
```

我们的第一个定义更加自由。它定义一个段为一个"顶级的文本块"。

第二个定义则严格一点。它定义一个段为一个函数定义。

## 自定义映射

在你的插件的 repo 中创建`ftplugin/potion/sections.vim`。 这将是我们放置段移动代码的地方。记得一旦一个缓冲区的`filetype`设置为`potion`，这里的代码就会执行。

我们将重新映射全部四个段移动命令，所以继续并创建一个骨架：

```
:::vim
noremap <script> <buffer> <silent> [[ <nop>
noremap <script> <buffer> <silent> ]] <nop>

noremap <script> <buffer> <silent> [] <nop>
noremap <script> <buffer> <silent> ][ <nop> 
```

Notice that we use `noremap` commands instead of `nnoremap`, because we want these to work in operator-pending mode too. That way you'll be able to do things like `d]]` to "delete from here to the next section". 注意我们使用`noremap`而不是`nnoremap`，因为我们想要这些命令也能在 operator-pending 模式下工作。 这样你就能使用`d]]`命令来删除从这到下一段之间的内容。

我们设置映射生效于 buffer-local，所以它们只对 Potion 文件起作用，不会替换全局选项。

我们也设置了 silent，因为用户不应关心我们实现段移动的细节。

## 使用一个函数

每个命令中实现段移动的代码会是非常相似的，所以让我们把它抽象出供映射调用的一个函数。

你将在那些创建了一些相似的映射的 Vim 插件中频繁看到这种策略。 比起把所有的功能堆砌于各个映射中，这样做不仅更易读，而且更易维护。

在`sections.vim`文件中加上下面内容：

```
:::vim
function! s:NextSection(type, backwards)
endfunction

noremap <script> <buffer> <silent> ]]
        \ :call <SID>NextSection(1, 0)<cr>

noremap <script> <buffer> <silent> [[
        \ :call <SID>NextSection(1, 1)<cr>

noremap <script> <buffer> <silent> ][
        \ :call <SID>NextSection(2, 0)<cr>

noremap <script> <buffer> <silent> []
        \ :call <SID>NextSection(2, 1)<cr> 
```

这里我用到了 Vimscript 的断行特性，因为我不想看到又长又臭的代码。 注意反斜杠是放在第二行前面进行转义的。阅读`:help line-continuation`以了解更多。

注意我们使用`<SID>`和一个脚本本地命名空间内定义的函数来避免污染全局空间。

每个映射简单地以适当参数调用`NextSection`实现对应的移动。 现在我们可以开始实现`NextSection`了。

## 基本移动

让我们考虑下我们的函数需要做什么。 我们想要移动光标到下一段，而移动光标，有一个简单的办法就是利用`/`和`?`命令。

编辑`NextSection`成这样：

```
:::vim
function! s:NextSection(type, backwards)
    if a:backwards
        let dir = '?'
    else
        let dir = '/'
    endif

    execute 'silent normal! ' . dir . 'foo' . "\r"
endfunction 
```

现在这个函数使用我们之前见过的`execute normal!`来执行`/foo`或`?foo`，取决于`backwards`的值。 这将是个好的开始。

继续前进，我们显然需要搜索`foo`以外的东西，是什么则取决于用的是段头的第一个还是第二个定义。

把`NextSection`改成这样：

```
:::vim
function! s:NextSection(type, backwards)
    if a:type == 1
        let pattern = 'one'
    elseif a:type == 2
        let pattern = 'two'
    endif

    if a:backwards
        let dir = '?'
    else
        let dir = '/'
    endif

    execute 'silent normal! ' . dir . pattern . "\r"
endfunction 
```

现在只需要补上匹配的模式了(pattern)，让我们继续完成它吧。

## 顶级文本段

用下面一行替换掉第一个`let pattern = '...'`：

```
:::vim
let pattern = '\v(\n\n^\S|%^)' 
```

如果不理解这个正则表达式是干什么的，请回忆我们正在实现的"段"的定义。

> 任何在空行之后的，第一个字符为非空字符的行，以及文件首行。

开头的`\v`强制切换为"very magic"模式，一如之前的几次。

剩下的正则表达式由两个选项组成。第一个，`\n\n^\S`，搜索"两个换行符，接着之后是一个非空字符"。 这正好是我们的定义中的第一种情况。

另一个是`%^`，在 Vim 中，这是一个代表文件开头的特殊正则符号。

我们现在已经到了尝试前两个映射的时机了。 保存`ftplugin/potion/sections.vim`并在你的 Potion 例子缓冲区中执行`:set filetype=potion`。 `[[`和`]]`命令应该可以工作，但会显得古怪。

## 搜索标记

你大概注意到了，在段之间移动时光标会位于真正想要移动到的地方上方的空行。 在继续阅读之前，先想想为什么会这样。

问题在于我们使用`/`(或`?`)进行搜索，而在默认情况下 Vim 会把光标移动到匹配开始处。 举个例子，当你执行`/foo`光标会位于`foo`中的`f`。

为了让 Vim 把光标移动到匹配结束处而不是开始处，我们可以使用搜索标记(search flag)。 试试在 Potion 文件中这么搜索：

```
:::vim
/factorial/e 
```

Vim 将找到`factorial`并带你到那。按下几次`n`来在匹配处之间移动。 `e`标记将使得 Vim 把光标移动到到匹配结束处而不是开始处。在另一个方向也试试：

```
:::vim
?factorial?e 
```

让我们来修改我们的函数，用搜索标记来放置光标到匹配的段头的另一端。

```
:::vim
function! s:NextSection(type, backwards)
    if a:type == 1
        let pattern = '\v(\n\n^\S|%^)'
        let flags = 'e'
    elseif a:type == 2
        let pattern = 'two'
        let flags = ''
    endif

    if a:backwards
        let dir = '?'
    else
        let dir = '/'
    endif

    execute 'silent normal! ' . dir . pattern . dir . flags . "\r"
endfunction 
```

我们这里改动了两处。首先，我们依照段移动的类型设置`flags`变量的值。 现在我们仅需处理第一种情况，所以设置了标记`e`。

其次，我们在搜索字符串中连接`dir`和`flags`。这将依照我们搜索的方向加入`?e`或`/e`。

保存文件，切换回 Potion 示例文件，并执行`:set ft=potion`来让改动生效。 现在尝试`[[`和`]]`来看看我们的成果吧！

## 函数定义

是时候处理我们对"段"的第二个定义了，幸运的是这个比起第一个简单多了。 重新说一下我们需要实现的定义：

> 任何第一个字符为非空字符，包括一个等于号，并以冒号结尾的行。

我们可以使用一个简单的正则表达式来查找这样的行。 修改函数中第二个`let pattern = '...'`成这样：

```
:::vim
let pattern = '\v^\S.*\=.*:$' 
```

这个正则表达式比上一个没那么吓人多了。我把指出它是怎么工作的任务作为你的练习 -- 它只是我们的定义的一个直白的翻译。

保存文件，在`factorial.pn`处执行`:set filetype=potion`，然后试试新的`][`和`[]`映射。它们应该能如期工作。

在这里我们不需要搜索标记，因为默认的移动到匹配处开头正是我们想要的。

## 可视模式

我们的段移动命令在 normal 模式下一切正常，但要让它们也能在 visual 模式下工作，我们还需要增加一些东西。 首先，把函数改成这样：

```
:::vim
function! s:NextSection(type, backwards, visual)
    if a:visual
        normal! gv
    endif

    if a:type == 1
        let pattern = '\v(\n\n^\S|%^)' 
        let flags = 'e'
    elseif a:type == 2
        let pattern = '\v^\S.*\=.*:$'
        let flags = ''
    endif

    if a:backwards
        let dir = '?'
    else
        let dir = '/'
    endif

    execute 'silent normal! ' . dir . pattern . dir . flags . "\r"
endfunction 
```

Two things have changed. First, the function takes an extra argument so it knows whether it's being called from visual mode or not. Second, if it's called from visual mode we run `gv` to restore the visual selection. 两个地方改变了。首先，函数接受的参数多了一个，这样它能知道自己是否是在 visual 模式下调用的。 其次，如果它是在 visual 模式下调用的，我们执行`gv`来恢复可视选择区域。

为什么我们要这么做？来，让我展示给你看。 在 visual 模式下随意选择一些文本并执行下面命令：

```
:::vim
:echom "hello" 
```

Vim 将显示`hello`，但可视模式下选择的范围也随之清空！

当用`:`执行一个 ex 模式下的命令，可视选择的范围总会被清空。 `gv`命令重新选择之前的可视选择范围，相当于撤销了清空。 这是个有用的命令，你会在日常工作中因此受益的。

现在我们需要更新前面的映射，传递`0`给新的`visual`参数：

```
:::vim
noremap <script> <buffer> <silent> ]]
        \ :call <SID>NextSection(1, 0, 0)<cr>

noremap <script> <buffer> <silent> [[
        \ :call <SID>NextSection(1, 1, 0)<cr>

noremap <script> <buffer> <silent> ][
        \ :call <SID>NextSection(2, 0, 0)<cr>

noremap <script> <buffer> <silent> []
        \ :call <SID>NextSection(2, 1, 0)<cr> 
```

这里没什么是过于复杂的。现在让我们加上 visual 模式映射，作为最后一块拼图。

```
:::vim
vnoremap <script> <buffer> <silent> ]]
        \ :<c-u>call <SID>NextSection(1, 0, 1)<cr>

vnoremap <script> <buffer> <silent> [[
        \ :<c-u>call <SID>NextSection(1, 1, 1)<cr>

vnoremap <script> <buffer> <silent> ][
        \ :<c-u>call <SID>NextSection(2, 0, 1)<cr>

vnoremap <script> <buffer> <silent> []
        \ :<c-u>call <SID>NextSection(2, 1, 1)<cr> 
```

这些映射都设置`visual`参数的值为`1`，来告诉 Vim 在移动之前重新选择上一次的选择范围。 这里也用到了我们在 Grep Operator 那几章学到的`<c-u>`技巧。

保存文件，在 Potion 文件中`set ft=potion`，大功告成！尝试一下你的新映射吧。 像`v]]`和`d[]`这样的命令现在应该可以正常地工作了。

## 我们得到了什么？

这是冗长的一章，尽管我们只实现了一些看上去简单的功能，但是你学到了(并充分地练习了)下列有用的知识：

*   使用`noremap`而不是`nnoremap`来创建可以作为移动和动作使用的命令。
*   在创建相关联的映射时，使用一个单一的接受多个参数的函数来简化你的工作。
*   逐渐增强一个 Vimscript 函数的能力。
*   动态地组建一个`execute 'normal! ...'字符串。
*   结合正则表达式，使用简单的搜索来实现移动。
*   使用特殊的正则符号，比如`%^`(文件开头) 。
*   使用搜索标记来改变搜索的行为。
*   实现不会改变可视选择范围的 visual 模式映射

坚持下并完成练习(不过是阅读一些文档)，然后赏自己一些冰激凌。你值得拥有！

## 练习

阅读`:help search()`。这是一个值得了解的函数，不过你也可以使用跟`/`和`?`列在一起的标记。

阅读`:help ordinary-atom`来认识能在搜索模式(pattern)中用到的更多有趣的东西。