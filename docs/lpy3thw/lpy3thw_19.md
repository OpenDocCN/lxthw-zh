# 练习 15 阅读文件

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.20.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.20.learn-py3.md)

你已经知道如何用 `input` 或者 `argv` 来获取用户的输入了。现在你将学习如何阅读文件。你需要好好做这个练习，才能理解发生了什么，记住要仔细输入和检查。对文件进行操作很容易把文件删掉，所以你要千万小心。

在这个练习中你要写两个文件。一个是通常你要运行的 `ex15.py` ，一个是叫做 `ex15_sample.txt` 的文本文件。以下是文本文件中要输入的内容：

```py
This  is stuff I typed into a file.
It  is really cool stuff.
Lots  and lots of fun to have in here.
```

我们要做的就是在我们的脚本中打开这个文件并把它打印出来。然而，我们不想只是简单粗暴（hard coding）地把 `ex15_sample.txt` 这个文件名输入进去，hard coding 的意思是把一些应该从用户那里获取的信息直接放到源代码里。这样不好，因为我们随后会需要它载入别的文件。解决方法是用 `argv` 或者 `input` 来问用户应该打开哪个文件，而不是 hard coding 文件名。

ex15.py

```py
1  from sys import argv
2
3 script, filename = argv
4
5 txt = open(filename)
6
7  print(f"Here's your file {filename}:")
8  print(txt.read())
9
10  print("Type the filename again:")
11 file_again = input("> ")
12
13 txt_again = open(file_again)
14
15  print(txt_again.read())
```

这个文件里发生了一些奇妙的事情，让我们快速分解来看一下：

第 1-3 行用了 `argv` 来获取一个文件名，然后第 5 行用了一个新的命令 `open` 。现在，运行 `pydoc open` 然后阅读说明。看见了吧，就像你自己的脚本和输入，它用了一个参数（parameter）然后返回了一个值，你可以把它赋给你自己的变量。你只是打开了一个文件。

第 7 行打印了一些信息，第 8 行就有一些新东西了。我们对 txt 用了一个叫做 `read.` 的函数，你从 `open` 那里得到的是一个文件，而且你还可以通过 . 命令名，以及参数，来给它一个命令，就像用 `open` 和 `input` 那样。区别是，`txt.(read)` 是说：`txt` ，执行不带参数的 `read` 命令！

剩下的部分基本上类似，但是我们会把分析留到附加练习里。

## 你会看到

| 警告！ |
| --- |
| 注意！你一直通过输入文件名来运行脚本，但是你要用 `argv` 加上参数来运行。看看下面例子的第一行，你会看我是通过输入 `python ex15.py ex15_sample.txt` 来运行它的。 `ex15.py` 后面的内容就是你要输入的参数，如果你漏掉了，就会收到报错信息！所以千万要注意！ |

我创建了一个叫做 `ex15_sample.txt` 的文件来运行我的脚本。

练习 15 会话

```py
1.  `$ python3.6 ex15.py ex15_sample.txt` 2.  `Here's your file ex15_sample.txt:`3.  `This is stuff I typed into a file.`4.  `It is really cool stuff.`5.  `Lots and lots of fun to have in here.`7.  ``Type the filename again:``8.  ``>   ex15_sample.txt``9.  ``This is stuff I typed into a file.``10.  ``It is really cool stuff.``11.  ``Lots and lots of fun to have in here.``
```

## 附加练习

这部分可能比较难，在你往下进行之前，确保你尽力去做这个附加练习。

*   在每行上面添加注释解释其含义。
*   如果你不确定，上网搜，或者问别人，比如你不知道 open 的用法，直接搜 `python3.6 open` 即可。
*   我在这儿用的是“命令”（command）这个词，不过，它也叫“函数”（function）或者“方法”（method）。你会在本书后面学到 functions 和 methods。
*   把第 10-15 行删掉（或者用别的方法使其失效）然后再运行脚本。
*   只用 input 来试试运行这个脚本。为什么要获取文件名的话一种方法比另一种方法更好？
*   开启 python3.6 shell，然后就像这个程序中一样从提示界面用 `open`。注意你是如何从 python3.6 里面打开文件并运行 `read` 的？
*   在你的脚本中对 `txt` 调用 `close()` 以及 `txt_again` 变量。当你对它们完成操作后关掉文件是非常重要的。

## 常见问题

**`txt = open(filename)` 会返回文件的内容吗？** 不会。它其实是创建了一个叫做“文件对象”（file object）的东西。你可以把它想象成曾经的 DVD 播放器，你可以在里面移动然后“读取”它们。但是 DVD 播放器不是 DVD 本身，就像文件对象也不是文件本身一样。

**我无法像你附加练习 7 中说的那样在 Terminal/PowerShell 里输入代码。** 首先，在命令行输入 `python3.6` 然后敲回车。现在你已经在 python3.6 里面了。然后你可以输入代码，python 就会运行一些。试着这样玩玩，然后输入 `quit()` 并回车，退出。

**为什么打开文件两次不会收到报错？**Python 不会限制你只能打开一次文件，事实上有时候确实需要打开多次。

**`from sys import argv` 是什么意思？**现在你只需要明白 `sys` 是一个包（package），这个短语是说从那个包里获取 `argv` 功能（feature）。你会在后面深入学习这块内容。

**我把脚本文件名这样放进去：`ex15_sample.txt = argv`, 但是无法运行。** 你不能这样做。严格按照我的代码来，然后用同样的方法在命令行运行它。你不用把文件名放进去，你得让 python 自己放。`