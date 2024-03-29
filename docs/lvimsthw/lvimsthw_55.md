# 外部命令

# 外部命令

Vim 遵循 UNIX 哲学"做一件事，做好它"。 与其试图集成你可能想要的功能到编辑器自身，更好的办法是在适当时使用 Vim 来调用外部命令。

让我们在插件中添加一些跟 Potion 编译器交互的命令，来浅尝在 Vim 里面调用外部命令的方法。

## 编译

首先我们将加入一个命令来编译和执行当前 Potion 文件。 有很多方法可以实现这一点，不过我们暂且用外部命令简单地实现。

在你的插件的 repo 中创建`potion/ftplugin/potion/running.vim`文件。 这将是我们创建编译和执行 Potion 文件的映射的地方。

```
:::vim
if !exists("g:potion_command")
    let g:potion_command = "potion"
endif

function! PotionCompileAndRunFile()
    silent !clear
    execute "!" . g:potion_command . " " . bufname("%")
endfunction

nnoremap <buffer> <localleader>r :call PotionCompileAndRunFile()<cr> 
```

第一部分以全局变量的形式储存着用来执行 Potion 代码的命令，如果还没有设置过的话。 我们之前见过类似的检查了。

如果`potion`不在用户的`$PATH`内，这将允许用户覆盖掉它， 比如在`~/.vimrc`添加类似`let g:potion_command = "/Users/sjl/src/potion/potion"`的一行。

最后一行添加了一个 buffer-local 的映射来调用我们前面定义的函数。 不要忘了，由于这个文件位于`ftdetect/potion`文件夹，每次一个文件的`filetype`设置成`potion`，它都会被执行。

真正实现了功能的地方在`PotionCompileAndRunFile()`。 保存文件，打开`factorial.pn`并按下`<localleader>r`来执行这个映射，看看发生了什么。

如果`potion`位于你的`$PATH`下，代码会被执行，你应该在终端看到输出(或者在窗口底部，如果你用的是 GUI vim)。 如果你看到了没有找到`potion`命令的错误，你需要像上面提到那样在`~/.vimrc`内设置`g:potion_command`。

让我们了解一下`PotionCompileAndRunFile()`的工作原理。

## Bang!

`:!`命令(念作"bang")会执行外部命令并在屏幕上显示它们的输出。尝试执行下面的命令：

```
:::vim
:!ls 
```

Vim 将输出`ls`命令的结果，同时还有"请按 ENTER 或其它命令继续"的提示。

当这样执行时，Vim 不会传递任何输入给外部命令。为了验证，执行：

```
:::vim
:!cat 
```

打入一些行，然后你将看到`cat`命令把它们都吐回来了，就像你是在 Vim 之外执行`cat`。按下 Ctrl-D 来结束。

想要执行一个外部命令并避免`请按 ENTER 或其它命令继续`的提示，使用`:silent !`。执行下面的命令：

```
:::vim
:silent !echo Hello, world. 
```

如果在 GUI Vim 比如 MacVim 或 gVim 下执行，你将不会看到`Hello,world.`的输出。

如果你在终端下执行，你看到的结果取决于你的配置。 一旦执行了一个`:silent !`，你可能需要执行`:redraw!`来重新刷新屏幕。

注意这个命令是`:silent !`而不是`:silent!`(看到空格了吗？)！ 这是两个不一样的命令，我们想要的是前者！Vimscript 奇妙吧？

让我们回到`PotionCompileAndRun()`上来：

```
:::vim
function! PotionCompileAndRunFile()
    silent !clear
    execute "!" . g:potion_command . " " . bufname("%")
endfunction 
```

首先我们执行一个`silent !clear`命令，来清空屏幕输出并避免产生提示。 这将确保我们仅仅看到本次命令的输出，如果一再执行同样的命令，你会觉得有用的。

在下一行我们使用老朋友`execute`来动态创建一个命令。建立的命令看上去类似于：

```
:::text
!potion factorial.pn 
```

注意这里没有`silent`，所以用户将看到命令输出，并不得不按下 enter 来返回 Vim。 这就是我们想要的，所以就这样设置好了。

## 显示字节码

Potion 编译器有一个显示由它生成的字节码的选项。如果你正试图在非常低级的层次下 debug，这将帮上忙。 在 shell 里执行下面的命令：

```
:::text
potion -c -V factorial.pn 
```

你将看到一大堆像这样的输出：

```
:::text
-- parsed --
code ...
-- compiled --
; function definition: 0x109d6e9c8 ; 108 bytes
; () 3 registers
.local factorial ; 0
.local print_line ; 1
.local print_factorial ; 2
...
[ 2] move     1 0
[ 3] loadk    0 0   ; string
[ 4] bind     0 1
[ 5] loadpn   2 0   ; nil
[ 6] call     0 2
... 
```

让我们添加一个使用户可以在新的 Vim 分割下，看到当前 Potion 代码生成的字节码的映射， 这样他们能更方便地浏览并测试输出。

首先，在`ftplugin/potion/running.vim`底部添加下面一行：

```
:::vim
nnoremap <buffer> <localleader>b :call PotionShowBytecode()<cr> 
```

这里没有什么特别的 -- 只是一个简单的映射。现在先描划出函数的大概框架：

```
:::vim
function! PotionShowBytecode()
    " Get the bytecode.

    " Open a new split and set it up.

    " Insert the bytecode.

endfunction 
```

既然已经建立起一个框架，让我们把它变成现实吧。

## system()

有许多不同的方法可以实现这一点，所以我选择相对便捷的一个。

执行下面的命令：

```
:::vim
:echom system("ls") 
```

你应该在屏幕的底部看到`ls`命令的输出。如果执行`:message`，你也能看到它们。 Vim 函数`system()`接受一个字符串命令作为参数并以字符串形式返回那个命令的输出。

你可以把另一个字符串作为参数传递给`system()`。执行下面命令：

```
:::vim
:echom system("wc -c", "abcdefg") 
```

Vim 将显示`7`(以及一些别的)。 如果你像这样传递第二个参数，Vim 将写入它到临时文件中并通过管道作为标准输入输入到命令里。 目前我们不需要这个特性，不过它值得了解。

回到我们的函数。编辑`PotionShowBytecode()`来填充框架的第一部分：

```
:::vim
function! PotionShowBytecode()
    " Get the bytecode.
    let bytecode = system(g:potion_command . " -c -V " . bufname("%"))
    echom bytecode

    " Open a new split and set it up.

    " Insert the bytecode.

endfunction 
```

保存文件，在`factorial.pn`处执行`:set ft=potion`重新加载，并使用`<lovalleader>b`尝试一下。 Vim 会在屏幕的底部显示字节码。一旦看到它成功执行了，你可以移除`echom`。

## 在分割上打草稿

接下来我们将打开一个新的分割把结果展示给用户。 这将让用户能够借助 Vim 的全部功能来浏览字节码，而不是仅仅只在屏幕上昙花一现。

为此我们将创建一个"草稿"分割：一个分割，它包括一个永不保存并每次执行映射都会被覆盖的缓冲区。 把`PotionShowBytecode()`函数改成这样：

```
:::vim
function! PotionShowBytecode()
    " Get the bytecode.
    let bytecode = system(g:potion_command . " -c -V " . bufname("%"))

    " Open a new split and set it up.
    vsplit __Potion_Bytecode__
    normal! ggdG
    setlocal filetype=potionbytecode
    setlocal buftype=nofile

    " Insert the bytecode.

endfunction 
```

新增的命令应该很好理解。

`vsplit`创建了名为`__Potion_Bytecode__`的新竖直分割。 我们用下划线包起名字，使得用户注意到这不是普通的文件(它只是显示输出的缓冲区)。 下划线不是什么特殊用法，只是约定俗成罢了。

接着我们用`normal! ggdG`删除缓冲区中的所有东西。 第一次执行这个映射时，并不需要这样做，但之后我们将重用`__Potion_Bytecode__`缓冲区，所以需要清空它。

接下来我们为这个缓冲区设置两个本地设置。首先我们设置它的文件类型为`potionbytecode`，只是为了指明它的用途。 我们也改变`buftype`为`nofile`，告诉 Vim 这个缓冲区与磁盘上的文件不相关，这样它就不会把缓冲区写入。

最后还剩下把我们保存在`bytecode`变量的字节码转储进缓冲区。完成函数，让它看上去像这样：

```
:::vim
function! PotionShowBytecode()
    " Get the bytecode.
    let bytecode = system(g:potion_command . " -c -V " . bufname("%") . " 2>&1")

    " Open a new split and set it up.
    vsplit __Potion_Bytecode__
    normal! ggdG
    setlocal filetype=potionbytecode
    setlocal buftype=nofile

    " Insert the bytecode.
    call append(0, split(bytecode, '\v\n'))
endfunction 
```

Vim 函数`append()`接受两个参数：一个将被附加内容的行号和一个将按行附加的字符串列表。 举个例子，尝试执行下面命令：

```
:::vim
:call append(3, ["foo", "bar"]) 
```

这将附加两行，`foo`和`bar`，在你当前缓冲区的第三行之后。 这次我们将在表示文件开头的第 0 行之后添加。

我们需要一个字符串列表来附加，但我们只有来自`system()`调用的单个包括换行符的字符串。 我们使用 Vim 的`split()`函数来分割这一大坨文本成一个字符串列表。 `split()`接受一个待分割的字符串和一个查找分割点的正则表达式。这真的很简单。

现在函数已经完成了，试一下对应的映射。 当你在`factorial.pn`中执行`<localleader>b`，Vim 将打开新的包括 Potion 字节码的缓冲区。 修改 Potion 源代码，保存文件，执行映射来看看会有什么不同的结果。

## 练习

阅读`:help bufname`。

阅读`:help buftype`。

阅读`:help append()`。

阅读`:help split()`。

阅读`:help :!`。

阅读`:help :read`和`:help :read!`(我们没有讲到这些命令，不过它们非常好用)。

阅读`:help system()`。

阅读`:help design-not`。

目前，我们的插件要求用户在执行映射之前手动保存文件来使得他们的改变起效。 当今撤销已经变得非常轻易，所以修改写过的函数来自动替他们保存。

如果你在一个带语法错误的 Potion 文件上执行这个字节码映射，会发生什么？为什么？

修改`PotionShowBytecode()`函数来探测 Potion 编译器是否返回一个错误，并向用户输出错误信息。

## 加分题

每次你执行字节码映射时，一个新的竖直分割都会被创建，即使用户没有关闭上一个。 如果用户没有一再关闭这些窗口，他们最终将被大量额外的窗口困住。

修改`PotionShowBytecode()`来探测`__Potion_Bytecode__`缓冲区的窗口是否已经打开了， 如果是，切换到它上去而不是创建新的分割。

你大概想要阅读`:help bufwinnr()`来获取帮助。

## 额外的加分题

还记得我们设置临时缓冲区的`filetype`为`potionbytecode`？ 创建`syntax/potionbytecode.vim`文件并为 Potion 字节码定义语法高亮，使得它们更易读。