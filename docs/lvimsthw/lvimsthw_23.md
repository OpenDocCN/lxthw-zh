# 变量作用域

# 变量作用域

如果你之前用过像 Python 或者 Ruby 之类的动态语言，现在你可能已经熟悉了 Vim 脚本的变量。你会发现 Vim 变量的大部分内容跟你想的一样，不过有一个东西可能会不同，那就是变量的作用域。

在两个分隔的窗口中分别打开两个不同的文件，然后在其中一个窗口中执行下面的命令：

```
:::vim
:let b:hello = "world"
:echo b:hello 
```

如你所愿，Vim 会显示`world`。现在切换到另外一个缓冲区再次执行`echo`命令：

```
:::vim
:echo b:hello 
```

这一次 Vim 会抛出一个无法找到变量的错误，

当你在变量名中使用`b:`，这相当于告诉 Vim 变量`hello`是当前缓冲区的本地变量。

Vim 有很多不同的变量作用域，不过在使用其他类型变量作用域之前我们需要先学习更多 Vim 脚本编程的知识。就目前而言，你只需要记住当某个变量由一个字符和冒号开头，那么这就表示它是一个作用域变量。

## 练习

浏览`:help internal-variables`中的作用域列表。先看看，熟悉熟悉，即使有不明白的地方也没关系。