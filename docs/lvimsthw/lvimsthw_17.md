# 自动命令组

# 自动命令组

前面几章我们学习了自动命令。执行下面命令：

```
:::vim
:autocmd BufWrite * :echom "Writing buffer!" 
```

现在使用`:write`命令将当前缓冲区写入文件，然后执行`:messages`命令查看消息日志。你会看到`Writing buffer!`在消息列表中。

然后将当前缓冲区写入文件，执行`:messages`查看消息日志。你会看到`Writing buffer!`在消息列表中出现了两次。

现在再次执行上面的自动命令：

```
:::vim
:autocmd BufWrite * :echom "Writing buffer!" 
```

再次将当前缓冲区写入文件并执行`:messages`命令。你会看到`Writing buffer!`在消息列表中出现了*4*次，这是怎么回事？

这是因为当你以上面的方式创建第二个自动命令的时候，Vim 没办法知道你是想替换第一个自动命令。在上面的示例中，Vim 创建了两个*不同*的自动命令，并且这两个命令刚好做同样的事情。

## 这会有什么问题？

既然你现在知道了 Vim 可能创建两个完全一样的自动命令，你可能会想：“有什么大不了？只要别这么干就可以！”。

问题是当你加载你的`~/.vimrc`文件的时候，Vim 会重新读取整个文件，包括你所定义的任何自动命令！这就意味着每次你加载你的`~/.vimrc`文件的时候，Vim 都会复制之前的自动命令，这会降低 Vim 的运行速度，因为它会一次又一次地执行相同的命令。

你可以执行下面的命令模拟这种情况：

```
:::vim
:autocmd BufWrite * :sleep 200m 
```

现在将当前缓冲区写入文件。你可能注意到 Vim 在写入文件的时候有点缓慢，当然也你可能注意不到。现在执行上面的自动命令三次：

```
:::vim
:autocmd BufWrite * :sleep 200m
:autocmd BufWrite * :sleep 200m
:autocmd BufWrite * :sleep 200m 
```

再次写文件。这次会更明显。

当然你不会创建任何只是进行 sleep 而不做任何事情的自动命令，不过一个使用 Vim 的老鸟的`~/.vimrc`文件可以轻易达到 1000 行，其中会有很多自动命令。再加上安装的插件中的自动命令，这肯定会影响 Vim 的速度。

## 把自动命令放到组中（Grouping Autocommands）

对于这个问题，Vim 有一个解决方案。这个解决方案的第一步是将相关的自动命令收集起来放到一个已命名的组（groups）中。

新开一个 Vim 实例，这样可以清除之前所创建的自动命令。然后运行下面的命令：

```
:::vim
:augroup testgroup
:    autocmd BufWrite * :echom "Foo"
:    autocmd BufWrite * :echom "Bar"
:augroup END 
```

中间两行的缩进没有什么含义，如果你不想输入的话可以不输。

将一个缓冲区写入文件然后执行`:messages`。你应该可以在消息日志列表中看到`Foo`和`Bar`。现在执行下面的命令：

```
:::vim
:augroup testgroup
:    autocmd BufWrite * :echom "Baz"
:augroup END 
```

当你再次将缓冲区写入文件的时候猜猜会发生什么。ok，你也许已经有结果了，重新写入缓冲区，然后执行`:messages`命令，看看你猜对了没。

## 清除自动命令组

当你写入文件的时候发生什么了？猜对了么？

如果你认为 Vim 会替换那个组，那么你猜错了。不要紧，很多人刚开始的时候都会这么想（我也是）。

当你多次使用`augroup`的时候，Vim 每次都会组合那些组。

如果你想清除一个组，你可以把`autocmd!`这个命令包含在组里面。执行下面的命令：

```
:::vim
:augroup testgroup
:    autocmd!
:    autocmd BufWrite * :echom "Cats"
:augroup END 
```

现在试试写入文件然后执行`:messages`查看消息日志。这次 Vim 只会输出`Cats`在消息列表中。

## 在 Vimrc 中使用自动命令

既然我们现在知道了怎么把自动命令放到一个组里面以及怎么清除这些组，我们可以使用这种方式将自动命令添加到`~/.vimrc`中，这样每次加载它的时候就不会复制自动命令了。

添加下面的命令到你的`~/.vimrc`文件中：

```
:::vim
augroup filetype_html
    autocmd!
    autocmd FileType html nnoremap <buffer> <localleader>f Vatzf
augroup END 
```

当进入`filetype_html`这个组的时候，我们会立即清除这个组，然后定义一个自动命令，然后退出这个组。当我们再次加载`~/.vimrc`文件的时候，清除组命令会阻止 Vim 添加一个一模一样的自动命令。

## 练习

查看你的`~/.vimrc`文件，然后把所有的自动命令用上面组的方式包裹起来。如果你觉得有必要，可以把多个自动命令放到一个组里面。

想想上一节的示例中的自动命令是干啥的。

阅读`:help autocmd-groups`。