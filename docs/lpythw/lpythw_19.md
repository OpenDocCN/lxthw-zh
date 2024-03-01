# 练习 15.读文件

# 练习 15.读文件

你已经学过`raw_input`和`argv`，这些是你开始学习读取文件的必备基础。你可能需要多多实验才能明白它的工作原理，所以你要细心做练习，并且仔细检查结果。处理文件需要非常仔细，否则，你可能会把有用的文件弄坏或者清空。导致前功尽弃。

这节练习涉及到写两个文件。一个正常的 ex15.py 文件，另外一个是 ex15_sample.txt，第二个文件并不是脚本，而是供你的脚本读取的文本文件。以下是后者的内容：

```py
This is stuff I typed into a file.
It is really cool stuff.
Lots and lots of fun to have in here. 
```

我们要做的是用我们的脚本“打开(open)”这个文件，然后打印出来。然而把文件名`ex15_sample.txt`写死在代码中并不是一个好主意，这些信息应该是用户输入的才对。如果我们碰到其他文件要处理，写死的文件名就会给你带来麻烦了。我们的解决方案是使用`argv`和`raw_input`来从用户获取信息，从而知道哪些文件该被处理。

```py
from sys import argv

script, filename = argv

txt = open(filename)

print "Here's your file %r:" % filename
print txt.read()

print "Type the filename again:"
file_again = raw_input("> ")

txt_again = open(file_again)

print txt_again.read() 
```

这个脚本中有一些新奇的玩意，我们来快速地过一遍：

代码的 1-3 行使用`argv`来获取文件名，这个你应该已经熟悉了。接下来第 5 行我们看到`open`这个新命令。现在请在命令行运行`pydoc open` 来读读它的说明。你可以看到它和你自己的脚本、或者`raw_input`命令类似，它会接受一个参数，并且返回一个值，你可以将这个值赋予一个变量。这就是你打开文件的过程。

第 7 行我们打印了一小行信息，但在第 8 行我们看到了新奇的东西。我们在 `txt` 上调用了一个函数。你从`open`获得了一个文件，文件本身也支持一些命令。它接受命令的方式是使用句点 `.` (英文称作 dot 或者 period)，紧跟着你的命令，然后是类似 `open` 和 `raw_input` 一样的参数。不同点是：当你执行`txt.read`时，你的意思其实是：“嘿 txt！执行你的 read 命令，无需任何参数！”

脚本剩下的部分基本差不多，不过我就把剩下的分析作为附加题留给你自己了。

## 你看到的结果

我创建了一个名字叫做`ex15_sample.txt`的文件，然后执行我的脚本：

```py
$ python ex15.py ex15_sample.txt
Here's your file 'ex15_sample.txt':
This is stuff I typed into a file.
It is really cool stuff.
Lots and lots of fun to have in here.

Type the filename again:
>  ex15_sample.txt
This is stuff I typed into a file.
It is really cool stuff.
Lots and lots of fun to have in here. 
```

## 附加题

这节的难度跨越有点大，所以你要尽量做好这节加分习题，然后再继续后面的章节。

> 1.  在每一行的上面加上注释。
> 2.  如果你不确定答案，就问别人，或者上网搜索。大部分时候，只要搜索 “python” 加上你要搜的东西就能得到你要的答案。比如搜索一下“python open”。
> 3.  我使用了“命令”这个词，不过实际上它们的名字是“函数（function）”和“方法（method）。上网搜索一下这两者的意义和区别。看不明白也没关系，这本书后面也会讲到这些。
> 4.  删掉 10-15 行使用到`raw_input`的部分，再运行一遍脚本。
> 5.  只用`raw_input`写这个脚本，想想哪种得到文件名称的方法更好？为什么？
> 6.  运行 python 在命令行下使用 open 打开一个文件，这种 open 和 read 的方法也值得你一学。
> 7.  让你的脚本对 `txt`和`txt_again`两个变量执行一下 `close()`，处理完文件后你需要将其关闭，这是很重要的一点。

## 常见问题

### Q:`txt = open(filename)`返回的是文件的文本内容吗？

> 不是的。它的返回值我们称为“文件对象”。你可以把文件想象成 19 世纪 50 年代的大型计算机上的老旧的磁带驱动器， 或者是像现在的 DVD 播放器，你可以在他们内部走动，然后阅读他们。但是文件对象并不是文件的文本内容一样就好像 DVD 播放器也不是一个 DVD 视频.

### Q:我不能按照你在附加题 7 中说的那样在命令行输入代码

> 首先，在命令行里输入`python`并回车，现在你已经进入了一个 python 解析器。接下来你就可以输入一系列的代码，python 会一一执行你的代码。最后别忘了输入`quit()`并回车退出 python。

### Q:当我打开同一个文件两次的时候，为什么不会报错？

> Python 不会限制你只能打开一个文件一次,有时这是必要的。

### Q:`from sys import argv` 这句是什么意思?

> 目前来说，你可以认为`sys`是一个包，这句代码的意思是从`sys`的包中引入`argv`功能模块。

### Q: 我把文件的名字放进脚本中，`ex15_sample.txt = argv`，却没有生效。

> 你不能这么写，请按照我的示例写代码，并像我一样在命令行里运行脚本。