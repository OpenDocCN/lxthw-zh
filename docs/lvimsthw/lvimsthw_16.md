# 本地缓冲区缩写

# 本地缓冲区缩写

上一章讲的东西比较多，完全理解会有点难，所以这一章来点容易的。我们已经学习了如何定义本地缓冲区的映射和设置选项，现在以同样的方式来学习本地缓冲区的缩写。

打开你的`foo`和`bar`这两个文件，切换到`foo`，然后执行下面的命令：

```
:::vim
:iabbrev <buffer> --- &mdash; 
```

在文件`foo`下进入插入模式输入下面的文本：

```
:::text
Hello --- world. 
```

Vim 会为你将`---`替换为“Hello“。现在切换到`bar`试试。在`bar`中替换不会发生，这是因为我们所定义的缩写被设置为只用于`foo`的本地缓冲区。

## 自动命令和缩写

使用本地缓冲区的缩写和自动命令来创建一个简单的“snippet”系统。

执行下面的命令：

```
:::vim
:autocmd FileType python     :iabbrev <buffer> iff if:<left>
:autocmd FileType javascript :iabbrev <buffer> iff if ()<left> 
```

打开一个 Javascript 文件然后输入`iff`缩写。然后再打开一个 Python 文件试试。Vim 会依据文件类型在当前行执行合适的缩写。

## 练习

为你经常编辑的文件创建更多的针对不同类型的文件的“snippet”缩写。你可以为绝大多数语言创建`return`的缩写，为 javascript 创建`function`的缩写，以及为 HTML 文件创建`&ldquo;`和`&rdquo;`的缩写。

将你创建的 snippets 加入到你的`~/.vimrc`文件中。

记住：最好的学习使用这些 snippets 的方法是*禁用*之前你做这些事情的方式。执行`:iabbrev <buffer> return NOPENOPENOPE`会*强迫*你使用缩写，这个命令在你输入 return 的时候不会输出任何东西。为了节省学习的时间，为你刚才创建的 snippets 都创建一个上面的缩写来*强迫*你使用你创建的 snippets。