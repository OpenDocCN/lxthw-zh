# 切换

# 切换

在开头前几章我们曾讲过怎么在 Vim 里设置选项。 对于布尔选项，我们可以使用`set someoption!`来"切换"选项。 如果我们能给这个命令创建一个映射，那就再好不过了。

执行下面的命令：

```
:::vim
:nnoremap <leader>N :setlocal number!<cr> 
```

在 normal 模式中按下`<leader>N`看看。Vim 将会在开启和关闭行号显示之间切换。 像这样的"切换"映射是十分方便的，因此我们就不需要两个独立的键来开/关。

不幸的是，这只对布尔选项起作用。如果我们想要切换一个非布尔选项，还需要做更多的工作。

## 切换选项

从创建一个可以切换选项的函数，以及调用该函数的映射开始吧。 把下面的代码加入到你的`~/.vimrc`(或一个`~/.vim/plugin/`中的独立文件，如果你想要的话)：

```
:::vim
nnoremap <leader>f :call FoldColumnToggle()<cr>

function! FoldColumnToggle()
    echom &foldcolumn
endfunction 
```

保存并 source 文件，然后按下`<leader>f`试试看。Vim 显示当前`foldcolumn`选项的值。 如果你不熟悉这个选项，阅读`:help foldcolumn`再继续。

让我们添加真正的切换功能。修改代码成这样：

```
:::vim
nnoremap <leader>f :call FoldColumnToggle()<cr>

function! FoldColumnToggle()
    if &foldcolumn
        setlocal foldcolumn=0
    else
        setlocal foldcolumn=4
    endif
endfunction 
```

保存并 source 文件，然后试试看。每次你按下它 Vim 将显示或隐藏折叠状态条(fold column)。

`if`语句判断`&foldcolumn`是否为真(记住 Vim 把 0 看作假而其他数字为真)。 如果是，把它设成 0(隐藏它)。否则就设置它为 4。就是这么简单。

你可以使用一个简单的函数像这样来切换任何以`0`代表关，以其他数字代表开的选项。

## 切换其他东西

我们的梦想不应止于切换选项。还有一个我们想切换的东西是 quickfix 窗口。 依然以之前的骨架代码作为起点。加入下面的代码到你的文件：

```
:::vim
nnoremap <leader>q :call QuickfixToggle()<cr>

function! QuickfixToggle()
    return
endfunction 
```

这个映射暂时什么都不干。让我们把它转变成其他稍微有点用的东西(不过还没有彻底完成)。 把代码改成这样：

```
:::vim
nnoremap <leader>q :call QuickfixToggle()<cr>

function! QuickfixToggle()
    copen
endfunction 
```

保存并 source 文件。如果现在你试一下这个映射，你就会看到一个空荡荡的 quickfix 窗口。

为了达到实现切换功能的目的，我们将选择一个既快捷又肮脏的手段：全局变量。 把代码改成这样：

```
:::vim
nnoremap <leader>q :call QuickfixToggle()<cr>

function! QuickfixToggle()
    if g:quickfix_is_open
        cclose
        let g:quickfix_is_open = 0
    else
        copen
        let g:quickfix_is_open = 1
    endif
endfunction 
```

我们干的事情十分简单 —— 每次调用函数时，我们用一个全局变量来储存 quickfix 窗口的开关状态。

保存并 source 文件，接着执行映射试试看。Vim 将抱怨变量尚未定义！那么我们先把变量初始化吧。

```
:::vim
nnoremap <leader>q :call QuickfixToggle()<cr>

let g:quickfix_is_open = 0

function! QuickfixToggle()
    if g:quickfix_is_open
        cclose
        let g:quickfix_is_open = 0
    else
        copen
        let g:quickfix_is_open = 1
    endif
endfunction 
```

保存并 source 文件，接着试一下映射。成功了！

## 改进

我们的切换函数可以工作，但还留有一些问题。

第一个问题是，假设用户用`:copen`或`:cclose`手动开关窗口，我们的全局变量将不会刷新。 实际上这不会是个大问题，因为大多数情况下用户会用这个映射开关窗口，万一没有打开，他们也会再按一次。

这又是关于写 Vimscript 代码的重要经验：如果你试图处理每一个边际条件，你将陷在里面，而且不会有任何进展。

在大多数情况下，先推出可工作(而且即使不能工作也不会造成破坏)的代码然后回过头改善， 要比耗费许多小时苛求完美好得多。除外你正在开发一个很可能有很多人用到的插件。 在这种情况下它才值得耗费时日来达到无懈可击的程度，让用户满意并减少 bug 报告。

## 重新加载窗口/缓冲区

我们的函数的另外一个问题是，当用户已经打开了 quickfix 窗口，并执行这个映射时， Vim 关闭了窗口，接着把他们弹到上一个分割中，而不是送他们回之前的地方。 如果你仅仅想快速查看一下 quickfix 窗口然后继续工作，发生这种事是让人恼怒的。

为了解决这个问题，我们将引入一种写 Vim 插件时非常有用的惯用法。把你的代码改成这样：

```
:::vim
nnoremap <leader>q :call QuickfixToggle()<cr>

let g:quickfix_is_open = 0

function! QuickfixToggle()
    if g:quickfix_is_open
        cclose
        let g:quickfix_is_open = 0
        execute g:quickfix_return_to_window . "wincmd w"
    else
        let g:quickfix_return_to_window = winnr()
        copen
        let g:quickfix_is_open = 1
    endif
endfunction 
```

我们在映射中加入了新的两行。其中一行(在`else`分支)设置了另一个全局变量，来保存执行`:copen`时的当前窗口序号。

另一行(在`if`分支)执行以那个序号作前缀的`wincmd w`，来告诉 Vim 跳转到对应窗口。

我们的解决方法又一次不是无懈可击的，用户可能在两次执行映射之间打开或关闭新的分割。 即使这样，它还是适合于大多数场合，所以目前这已经够好的了。

在大多数程序中，这种手工保存全局状态的伎俩会遭到谴责，但对于一个非常短小的 Vimscript 函数而言， 它既快捷又肮脏，却能不辱使命，完成重任。

## 练习

阅读`:help foldcolumn`.

阅读`:help winnr()`

阅读`:help ctrl-w_w`.

阅读`:help wincmd`.

在需要的地方加上`s:`和`<SID>`来把函数限定在独自的命名空间中。