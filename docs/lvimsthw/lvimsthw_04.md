# 打印信息

# 打印信息

Vimscript 中，我们最先关注的是`echo`和`echom`命令。

你可以在 Vim 中执行`:help echo`和`:help echom`命令以查看其帮助文档。读完本书之后， 再次遇到新的命令时，你应该先执行`:help`命令查看其帮助文档。

执行如下命令，体验`echo`命令：

```
:::vim
:echo "Hello, world!" 
```

你应该会在屏幕的底部看到`Hello, world!`被打印出来。

## 还是打印消息

现在执行如下命令，体验`echom`命令：

```
:::vim
:echom "Hello again, world!" 
```

你应该会在屏幕的底部看到`Hello again, world!`被打印出来。

执行如下命令，查看上述两个打印命令的区别：

```
:::vim
:messages 
```

你应该会看到一些消息。`Hello, world!`应该*不在*其中，但是`Hello again, world!` *在*。

当你写更为复杂的 Vimscript 时，你可能会想"打印一些信息"以方便调试程序。`:echo`命令 会打印输出，但是一旦你的脚本运行完毕，那些输出信息就会消失。使用`:echom`打印的信息 会保存下来，你可以执行`:messages`命令再次查看那些信息。

## 注释

继续之前，咱们先看看如何添加注释。当你写 Vimscript 脚本时(在你的`~/.vimrc`文件中或 其它任意文件)，你可以通过`"`字符添加注释，例如：

```
:::vim
" Make space more useful
nnoremap <space> za 
```

这个注释方法并不*总是*有效(这就是 Vimscript 令人无语的一点)，但是更多的情况这个方法是 可以正常工作的。以后我们会谈到什么情况、为什么这个方法会无效。

## 练习

阅读`:help echo`帮助文档。

阅读`:help echom`帮助文档。

阅读`:help messages`帮助文档。

添加一行代码到你的`~/.vimrc`文件中，使得每个打开 Vim 时都会显示一个可爱的 ASCII 字符猫(`>^.^<`)。