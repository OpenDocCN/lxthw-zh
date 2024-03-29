# 实例研究：Grep 运算符(Operator)，第一部分

# 实例研究：Grep 运算符(Operator)，第一部分

在本章和下一章中，我们将使用 Vimscript 来实现一个相当复杂的程序。我们将探讨一些闻所未闻的东西， 也将在实战中把之前学过的东西联系起来。

在本实例研究中，遇到不熟悉的内容，你得用`:help`弄懂它。如果你只是走马观花，就将所获无多。

## Grep

如果你未曾用过`:grep`，现在你应该花费一分钟读读`:help :grep`和`:help :make`。 如果之前没用过 quickfix window，阅读`:help quickfix-window`。

简明扼要地说：`:grep ...`将用你给的参数来运行一个外部的 grep 程序，解析结果，填充 quickfix 列表， 这样你就能在 Vim 里面跳转到对应结果。

我们将会添加一个"grep 运算符"到任意 Vim 的内置(或自定义！)的动作中，来选择想要搜索的文本， 让`:grep`更容易使用。

## 用法

在写下每一个有意义的 Vimscript 程序的第一步，你需要思索一个问题：“它会被用户怎么使用呢？”。 尝试构思出一种优雅，简易，符合直觉的调用方法。

这次我会替你把这活干了：

*   我们将创造一个"grep 运算符"并绑定到`<leader>g`。
*   它将表现得同其他任意 Vim 运算符一样，还可以加入到组合键(比如`w`和`i{`)中。
*   它将立刻开始搜索并打开 quickfix 窗口展示结果。
*   它将*不会*跳到第一个结果，因为当第一个结果不是你想要的时候，这样做会困扰你。

一些你将怎么使用它的用例：

*   `<leader>giw`: Grep 光标下的词(word)。
*   `<leader>giW`: Grep 光标下的词的大写形式(WORD)。
*   `<leader>gi'`: Grep 当前所在的单引号括住的词。
*   `viwe<leader>g`: 可视状态下选中一个词并拓展选择范围到下一词，然后 Grep。

有很多，*很多*其他的方法可以用它。看上去它好像需要写很多，很多代码， 但事实上我们只需要实现"运算符"功能然后 Vim 就会完成剩下的工作。

## 一个原型

在埋头写下巨量(trickey bits)的 Vimscript 之前，有一个也许会帮上忙的方法是简化你的目标并实现*它*， 来推测你最终解决方案可能的"外形"。

让我们简化我们的目标为"创造一个映射来搜索光标下的词"。这有用而且应该更简单，所以我们能更快得到可运行的成果。 目前我们将映射它到`<leader>g`。

我们从一个映射骨架开始并逐渐填补它。执行这个命令：

```
:::vim
:nnoremap <leader>g :grep -R something .<cr> 
```

如果你阅读过`:help grep`，你就能轻易理解这个命令。我们之前也看过许多映射，这里没有什么是新的。

显然我们还没做什么，所以让我们一步步打磨这个映射直到它符合我们的要求。

## 搜索部分

首先我们需要搜索光标下的词，而不是`something`。执行下面的命令：

```
:::vim
:nnoremap <leader>g :grep -R <cword> .<cr> 
```

现在试一下。`<cword>`是一个 Vim 的 command-line 模式的特殊变量， Vim 会在执行命令之前把它替换为"光标下面的那个词"。

你可以使用`<cWORD>`来得到大写形式(WORD)。执行这个命令：

```
:::vim
:nnoremap <leader>g :grep -R <cWORD> .<cr> 
```

现在试试把光标放在诸如`foo-bar`的词上面。Vim 将 grep`foo-bar`而不是其中的一部分。

我们的搜索部分还有一个问题：如果这里面有什么特殊的 shell 字符，Vim 会毫不犹豫地传递给外部的 grep 命令。 这样会导致程序崩溃(或更糟：铸成某些大错)。

让我们看看如何使它挂掉。输入`foo;ls`并把光标放上去执行映射。grep 命令失败了， 而 Vim 将执行`ls`命令！这肯定糟透了，如果词里包括比`ls`更危险的命令呢？

为了解决这个问题，我们将调用参数用引号括起来。执行这个命令：

```
:::vim
:nnoremap <leader>g :grep -R '<cWORD>' .<cr> 
```

大多数 shell 把单引号括起来的内容当作(大体上)字面量，所以我们的映射现在更加健壮了。

## 转义 Shell 命令参数

搜索部分还有一个问题。在`that's`上尝试这个映射。它不会工作，因为词里的单引号与 grep 命令的单引号发生了冲突！

为了解决问题，我们可以使用 Vim 的`shellescape`函数。 阅读`:help escape()`和`:help shellescape()`来看它是怎样工作的(真的很简单)。

因为`shellescape()`要求 Vim 字符串，我们需要用`execute`动态创建命令。 首先执行下面命令来转换`:grep`映射到`:execute "..."`形式：

```
:::vim
:nnoremap <leader>g :execute "grep -R '<cWORD>' ."<cr> 
```

试一下并确信它可以工作。如果不行，找出拼写错误并改正。 然后执行下面的使用了`shellescape`的命令。

```
:::vim
:nnoremap <leader>g :execute "grep -R " . shellescape("<cWORD>") . " ."<cr> 
```

在一般的词比如`foo`上执行这个命令试试。它可以工作。再到一个带单引号的词，比如`that's`，上试试看。 它还是不行！为什么会这样？

问题在于 Vim 在拓展命令行中的特殊变量，比如`<cWORD>`，的*之前*，就已经执行了`shellescape()`。 所以 Vim shell-escaped 了字面量字符串`"<cWORD>"`(什么都不做，除了给它添上一对单引号)并连接到我们的`grep`命令上。

通过执行下面的命令，你可以亲眼目睹这一切。

```
:::vim
:echom shellescape("<cWORD>") 
```

Vim 将输出`'<cWORD>'`。注意引号也是输出字符串的一部分。Vim 把它作为 shell 命令参数保护了起来。

为解决这个问题，我们将使用`expand()`函数来强制拓展`<cWORD>`为对应字符串， 抢在它被传递给`shellescape`*之前*。

让我们单独看看这一部分是怎么工作的。把你的光标移到带单引号的词(比如`that's`)上去， 并执行下面命令：

```
:::vim
:echom expand("<cWORD>") 
```

Vim 输出`that's`，因为`expand("<cWORD>")`以 Vim 字符串的形式返回当前光标下的词。 是时候加入`shellescape`的部分了：

```
:::vim
:echom shellescape(expand("<cWORD>")) 
```

这次 Vim 输出`'that'\''s'`。 如果觉得这看上去真可笑，你大概没有感受过看透了各种 shell 转义的疯狂形式后的淡定吧。 目前，不用为此而纠结。就相信 Vim 接受了`expand`的输出并正确地转义了它。

目前我们已经得到了光标下的词的彻底转义版本。是时候连接它到我们的映射了！ 执行下面的命令：

```
:::vim
:nnoremap <leader>g :exe "grep -R " . shellescape(expand("<cWORD>")) . " ."<cr> 
```

试一下。这个映射不再有问题，即使我们用它搜索带古怪符号的词。

"从简单的 Vimscript 开始并一点点转变它直到达成你的目标"这样的工作方式将会被你一再取用。

## 整理整理

在完成映射之前，还要处理一些小问题。首先，我们说过我们不想自动跳到第一个结果， 所以要用`grep!`替换掉`grep`。执行下面的命令：

```
:::vim
:nnoremap <leader>g :execute "grep! -R " . shellescape(expand("<cWORD>")) . " ."<cr> 
```

再一次试试，发现什么都没发生。Vim 用结果填充了 quickfix 窗口，我们却无法打开。 执行下面的命令：

```
:::vim
:nnoremap <leader>g :execute "grep! -R " . shellescape(expand("<cWORD>")) . " ."<cr>:copen<cr> 
```

现在试试这个映射，你将看到 Vim 自动打开了包含搜索结果的 quickfix 窗口。 我们所做的仅仅是在映射的结尾续上`:copen<cr>`。

最后一点，在搜索的时候，我们要移除 Vim 所有的 grep 输出。执行下面的命令：

```
:::vim
:nnoremap <leader>g :silent execute "grep! -R " . shellescape(expand("<cWORD>")) . " ."<cr>:copen<cr> 
```

我们完成了，试一试并犒劳一下自己吧！`silent`命令仅仅是在运行一个命令的同时隐藏它的正常输出。

## 练习

把我们刚刚做出来的映射加入到你的`~/.vimrc`文件。

如果你未曾读过`:help :grep`，去读它。

阅读`:help cword`。

阅读`:help cnext`和`help cprevious`。修改你的 grep 映射，试一下它们。

设置`:cnext`和`:cprevious`的映射，让在匹配内容间的移动更加方便。

阅读`:help expand`。

阅读`:help copen`。

在我们创建的映射中加入 height 参数到`:copen`命令中，看看 quickfix 窗口能不能以指定的高度打开。

阅读`:help silent`。