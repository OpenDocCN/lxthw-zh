# 实例研究：Grep 运算符(Operator)，第三部分

# 实例研究：Grep 运算符(Operator)，第三部分

我们新鲜出炉的"grep 运算符"工作得很好，但是写 Vimscript 的目的，就是要体贴地改善你的用户的生活。 我们可以额外做两件事，让我们的运算符更加符合 Vim 生态圈的要求。

## 保护寄存器

由于把文本复制到未命名寄存器中，我们破坏了之前在那里的内容。

这并不是我们的用户想要的，所以让我们在复制之前先保存寄存器中的内容并于最后重新加载。 修改代码成这样：

```
:::vim
nnoremap <leader>g :set operatorfunc=GrepOperator<cr>g@
vnoremap <leader>g :<c-u>call GrepOperator(visualmode())<cr>

function! GrepOperator(type)
    let saved_unnamed_register = @@

    if a:type ==# 'v'
        normal! `<v`>y
    elseif a:type ==# 'char'
        normal! `[v`]y
    else
        return
    endif

    silent execute "grep! -R " . shellescape(@@) . " ."
    copen

    let @@ = saved_unnamed_register
endfunction 
```

我们在函数的开头和结尾加入了两个`let`语句。 第一个用一个变量保存`@@`中的内容，第二个则重新加载保存的内容。

保存并 source 文件。测试一下，复制一些文本，接着按下`<leader>giw`来执行运算符， 然后按下`p`来粘贴之前复制的文本。

当写 Vim 插件时，你*总是*应该尽量在修改之前保存原来的设置和寄存器值，并在之后加载回去。 这样你就避免了让用户陷入恐慌的可能。

## 命名空间

我们的脚本在全局命名空间中创建了函数`GrepOperator`。 这大概不算什么大问题，但当你写 Vimscript 的时候，事前以免万一远好过事后万分歉意。

仅需增加几行代码，我们就能避免污染全局命名空间。把代码修改成这样：

```
:::vim
nnoremap <leader>g :set operatorfunc=<SID>GrepOperator<cr>g@
vnoremap <leader>g :<c-u>call <SID>GrepOperator(visualmode())<cr>

function! s:GrepOperator(type)
    let saved_unnamed_register = @@

    if a:type ==# 'v'
        normal! `<v`>y
    elseif a:type ==# 'char'
        normal! `[v`]y
    else
        return
    endif

    silent execute "grep! -R " . shellescape(@@) . " ."
    copen

    let @@ = saved_unnamed_register
endfunction 
```

脚本的前三行已经被改变了。首先，我们在函数名前增加前缀`s:`，这样它就会处于当前脚本的命名空间。

我们也修改了映射，在`GrepOperator`前面添上`<SID>`，所以 Vim 才能找到这个函数。 如果我们不这样做，Vim 会尝试在全局命名空间查找该函数，这是不可能找到的。

欢呼吧，我们的`grep-operator.vim`脚本不仅非常有用，而且是一个善解人意的 Vimscript 公民！

## 练习

阅读`:help <SID>`。

享受一下，吃点零食犒劳自己。