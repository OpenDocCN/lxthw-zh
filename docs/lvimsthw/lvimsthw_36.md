# 实例研究：Grep 运算符(Operator)，第二部分

# 实例研究：Grep 运算符(Operator)，第二部分

目前为止，我们已经完成了一个原型，是时候扩充它，让它更加强大。

记住：我们初始目标是创建"grep 运算符"。我们还需要做一大堆新的东西来达成目标， 但要像前一章的过程一样：从简单的东西开始，并逐步改进直到它满足我们的需求。

在开始之前，注释掉`~/.vimrc`中在前一章创建的映射。我们还要用同样的快捷键来映射新的运算符。

## 新建一个文件

创建一个新的运算符需要许多命令，把它们手工打出来将很快变成一种折磨。 你可以把它附加到`~/.vimrc`，但让我们为这个运算符创建一个独立的文件。我们有足够的必要这么做。

首先，找到你的 Vim`plugin`文件夹。在 Linux 或 OS X，这将会是`~/.vim/plugin`。 如果你是 Windows 用户，它将位于你的主目录下的`vimfiles`文件夹。(如果你找不到，在 Vim 里使用`:echo $HOME 命令) 如果这个文件夹不存在，创建一个。

在`plugin/`下新建文件`grep-operator.vim`。这就是你放置新运算符的代码的地方。 一旦文件被修改，你可以执行`:source %`来重新加载代码。 每次你打开 Vim，这个文件也会被重新加载，就像`~/.vimrc`。

不要忘了，在你 source 之前，你*必须*先保存文件，这样才能看到变化！

## 骨架(Skeleton)

要创建一个新的 Vim 运算符，你需要从两个组件开始：一个函数还有一个映射。 先添加下面的代码到`grep-operator.vim`:

```
:::vim
nnoremap <leader>g :set operatorfunc=GrepOperator<cr>g@

function! GrepOperator(type)
    echom "Test"
endfunction 
```

保存文件并用`:source %`source 它。尝试通过按下`<leader>giw`来执行"grep 整个词"。 Vim 将在接受`iw`动作(motion)后，输出`Test`，意味着我们已经搭起了骨架。

函数部分是简单的，没有什么是我们没讲过的。不过映射部分比较复杂。 我们首先对函数设置了`operatorfunc`选项，然后执行`g@`来以运算符的方式调用这个函数。 看起来这有点绕，不过这就是 Vim 工作的原理。

暂时把这个映射看作黑魔法吧。稍后你可以到文档里一探究竟。

## 可视模式

我们已经在 normal 模式下加入了这个运算符，但还想要在 visual 模式下用到它。 在之前的映射下面添加多一个：

```
:::vim
vnoremap <leader>g :<c-u>call GrepOperator(visualmode())<cr> 
```

保存并 source 文件。现在在 visual 模式下选择一些东西并按下`<leader>g`。 什么也没发生，但 Vim 确实输出了`Test`，所以我们的函数已经运行了。

之前我们就见过`<c-u>`，但是还没有解释它是做什么的。试一下在可视模式下选中一些文本并按下`:`。 Vim 将打开一个命令行就像平时按下了`:`一样，但是命令行的开头自动添加了`'<,'>`！

Vim 为了提高效率，插入了这些文本来让你的命令在被选择的范围内执行。 但是这次，我们不需要它添倒忙。我们用`<c-u>`来执行"从光标所在处删除到行首的内容"，移除多余文本。 最后剩下一个孤零零的`:`，为调用`call`命令作准备。

我们传递过去的`visualMode()`参数还没有讲过呢。 这个函数是 Vim 的内置函数，它返回一个单字符的字符串来表示 visual 模式的类型： `"v"`代表字符宽度(characterwise)，`"V"`代表行宽度(linewise)，`Ctrl-v`代表块宽度(blockwise)。

## 动作类型

我们定义的函数接受一个`type`参数。我们知道在 visual 模式下它将会是`visualmode()`的返回值， 但是在 normal 模式下呢？

编辑函数体部分，让代码像这样：

```
:::vim
nnoremap <leader>g :set operatorfunc=GrepOperator<cr>g@
vnoremap <leader>g :<c-u>call GrepOperator(visualmode())<cr>

function! GrepOperator(type)
    echom a:type
endfunction 
```

Source 文件，然后继续并用多种的方式测试它。你可能会得到类似下面的结果：

*   按下`viw<leader>g`显示`v`，因为我们处于字符宽度的 visual 模式。
*   按下`Vjj<leader>g`显示`V`，因为我们处于行宽度的 visual 模式。
*   按下`<leader>giw`显示`char`，因为我们在字符宽度的动作(characterwise motion)中使用该运算符。
*   按下`<leader>gG`显示`line`，因为我们在行宽度的动作(linewise motion)中使用该运算符。

现在我们已经知道怎么区分不同种类的动作，这对于我们选择需要搜索的词是很重要的。

## 复制文本

我们的函数将需要获取用户想要搜索的文本，而这样做最简单的方法就是复制它。 把函数修改成这样：

```
:::vim
nnoremap <leader>g :set operatorfunc=GrepOperator<cr>g@
vnoremap <leader>g :<c-u>call GrepOperator(visualmode())<cr>

function! GrepOperator(type)
    if a:type ==# 'v'
        execute "normal! `<v`>y"
    elseif a:type ==# 'char'
        execute "normal! `[v`]y"
    else
        return
    endif

    echom @@
endfunction 
```

哇。好多新的东西啊。试试按下`<leader>giw`，`<leader>g2e`和`vi(<leader>g`看看。 每次 Vim 都会输出动作所包括的文本，显然我们已经走上正道了！

让我们把这段代码一步步分开来看。首先我们用`if`语句检查`a:type`参数。如果是`'v'`， 它就是使用在字符宽度的 visual 模式下，所以我们复制了可视模式下的选中文本。

注意我们使用大小写敏感比较`==#`。如果我们只用了`==`而用户设置`ignorecase`， `"V"`也会是匹配的，结果*不会*如我们所愿。重视防御性编程！

`if`语句的第二个分支则会拦住 normal 模式下使用字符宽度的动作。

剩下的情况只是默默地退出。我们直接忽略行宽度/块宽度的 visual 模式和对应的动作类型。 Grep 默认情况下不会搜索多行文本，所以在搜索内容中夹杂着换行符是毫无意义的。

我们每一个`if`分支都会执行`normal!`命令来做两件事：

*   在可视状态下选中我们想要的文本范围：
    *   先移动到范围开头，并标记
    *   进入字符宽度的 visual 模式
    *   移动到范围结尾的标记
*   复制可视状态下选中的文本。

先不要纠结于特殊标记方式。你将会在完成本章结尾的练习时学到为什么它们会不一样。

函数的最后一行输出变量`@@`。不要忘了以`@`开头的变量是寄存器。`@@`是"未命名"(unnamed)寄存器： 如果你在删除或复制文本时没有指定一个寄存器，Vim 就会把文本放在这里。

简明扼要地说：我们选中要搜索的文本，复制它，然后输出被复制的文本。

## 转义搜索文本

既然得到了 Vim 字符串形式的需要的文本，我们可以像前一章一样将它转义。修改`echom`命令成这样：

```
:::vim
nnoremap <leader>g :set operatorfunc=GrepOperator<cr>g@
vnoremap <leader>g :<c-u>call GrepOperator(visualmode())<cr>

function! GrepOperator(type)
    if a:type ==# 'v'
        normal! `<v`>y
    elseif a:type ==# 'char'
        normal! `[v`]y
    else
        return
    endif

    echom shellescape(@@)
endfunction 
```

保存并 source 文件，然后在可视模式下选中带特殊字符的文本，按下`<leader>g`。 Vim 显示一个被转义了的能安全地传递给 shell 命令的文本。

## 执行 Grep

我们终于可以加上`grep!`命令来实现真正的搜索。替换掉`echom`那一行，代码看起来就像这样：

```
:::vim
nnoremap <leader>g :set operatorfunc=GrepOperator<cr>g@
vnoremap <leader>g :<c-u>call GrepOperator(visualmode())<cr>

function! GrepOperator(type)
    if a:type ==# 'v'
        normal! `<v`>y
    elseif a:type ==# 'char'
        normal! `[v`]y
    else
        return
    endif

    silent execute "grep! -R " . shellescape(@@) . " ."
    copen
endfunction 
```

看起来眼熟吧。我们简单地执行上一章得到的`silent execute "grep! ..."`命令。 由于我们不再把所有的代码塞进单个`nnoremap`命令里，现在代码甚至更加清晰易懂了！

保存并 source 文件，然后尝试一下，享受自己辛勤劳动的成果吧！

因为定义了一个全新的 Vim 运算符，现在我们可以在许多场景下使用它了，比如：

*   `viw<leader>g`: 可视模式下选中一个词，然后 grep 它。
*   `<leader>g4w`: Grep 接下来的四个词。
*   `<leader>gt;`: Grep 到分号为止的文本。
*   `<leader>gi[`: Grep 方括号里的文本.

这里彰显了 Vim 的优越性：它的编辑命令就像一门语言。当你加入新的动词，它会自动地跟(大多数)现存的名词和形容词搭配起来。

## 练习

阅读`:help visualmode()`。

阅读`:help c_ctrl-u`。

阅读`:help operatorfunc`。

阅读`:help map-operator`。