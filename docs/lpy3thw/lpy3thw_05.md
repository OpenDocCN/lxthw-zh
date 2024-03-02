# 练习 1\. 第一个程序

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.6.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.6.learn-py3.md)

| 警告！ |
| --- |
| 如果你跳过了练习 0，那你就没有按照这本书的正确学习方式来。另外，也不要使用 IDLE 或者 IDE。如果你跳过了练习 0，拐回去重新学习。 |

你可能已经花费了大量时间在练习 0 上，学习如何安装一个文本编辑器，运行编辑器以及 Terminal，并且学习如何操作它们。如果你还没有做这些，就不要继续，否则你会后悔的。这种练习前的警告我再说最后一次：**不要擅自跳过练习自己往前学**。

把下面的本文输入到一个名为 `ex1.py` 单个文件中，python 文件一般以 `.py`为后缀。

ex1.py

```py
1  print("Hello World!")
2  print("Hello Again")
3  print("I like typing this.")
4  print("This is fun.")
5  print('Yay! Printing.')
6  print("I'd much rather you 'not'.")
7  print('I "said" do not touch this.')
```

你的 Atom 文本编辑器应该看起来像这样：

![ex1-1.jpg](img/e21389f3c099b6fe538226d20f97726a.png)

如果你的编辑器看起来不完全一样也不用担心，只要大体一致就行。

当你敲这个文件时，你得明白：

*   左边这些数字不是我敲上去的，它印在书上是为了讲解的时候方便说明。比如“看第 5 行…”之类，所以不要把行数敲进 Python 脚本里。
*   我输出的结果跟我在练习 1 的 `ex1.py` 中让你们输入的内容是一模一样的，而不是大致相同。所以每一个字符你都要严格按照我的要求来输入，当然颜色无所谓。在终端这样输入就可以运行你的 Python 文件：

```py
python3.6 ex1.py
```

如果你都做对了，你就会看到和我一样的结果，如果没有，你肯定是哪里出错了。不，相信我，不是电脑的问题。

## 你应该看到

在 MacOS 的 Terminal 上你应该看到这样的结果：

![ex1-2.jpg](img/e21389f3c099b6fe538226d20f97726a.png)

在 Windows 的 Powershell 上你应该看到这样的结果:

![ex1-3.jpg](img/e21389f3c099b6fe538226d20f97726a.png)

你可能会在 python3.6 命令行前面看到不同的名字，这不重要，重要的是你输入的命令要输出跟我一样的结果。

如果你出错了你可能会看到这个：

```py
$ python3.6 python/ex1.py
File  "python/ex1.py"  , line 3
print  (" I like typing this.
^
SyntaxError : EOL while scanning string literal
```

能读懂这些错误信息很重要，因为你接下来可能会出现很多这种错误，我也是。让我们一行一行来看。

*   我们在 Terminal 运行 `ex1.py` 脚本。
*   Python 告诉我们 `ex1.py` 文件的第三行出错了。
*   它把第三行的代码打印出来以便我们查看。
*   然后它放了一个 `^` （插入符号）来指出哪里出了问题。注意到那个缺失的 `"` 了吗？
*   最后，它输出“SyntaxError”，并告诉我们可能的错误信息。通常这些错误信息都比较隐晦，但是如果你用搜索引擎搜索以下，你就会发现别人也遇到过这样的错误，然后你很可能就会找到问题的解决办法。

## 课后练习

这个课后练习包括一些你应该尝试去做的东西，如果你不会，可以先跳过，随后再拐回来做。

对于这个练习，试试以下操作：

> 1.  让你的脚本再打印出一行。
> 2.  让你的脚本只打印一行。
> 3.  在任一行的开头放一个 `#` ，看看会发生什么？试着弄明白这个符号的作用。

从现在开始，我不会解释每个练习都是如何工作的，除非遇到特殊情况。

## 常见问题

以下是实际学习本节练习过程中学生们经常会问到的一些问题：

**我能用 IDLE 吗？**不，你应该用 Terminal 或者 Powershell。如果你不知道怎么用，就去学习附录 A 的命令行速成教程。

**我怎么才能像你一样编辑代码时有颜色？**先把你的文件另存为 `.py` ，比如 `ex1.py` 。然后你在输入的时候就会有颜色了。

**我在运行 `ex1.py` 时遇到了 `SyntaxError：invalid syntax` 提示。**你很可能是已经运行了 Python，然后又输了一次 `python`。关闭 Terminal，重新打开，然后只输入 `python3.6 ex1.py`。

**我遇到了 `can't open 'ex1.py': [Errno 2] No such file or directory.` （“无法打开‘ex1.py’：[错误号 2] 没有该文件或目录”）**。你需要和你创建的文件在同一个目录（文件夹）下。你要先使用 `cd` 命令切换到了那个目录下。比如，如果你把你的文件保存在 `lpthw/ex1.py`，那你就应该在运行 `python3.6 ex1.py` 之前先用 `cd lpthw/` 切换到 `lpthw/` 目录下。如果这段你看不懂，去学附录 A 的命令行速成教程。

**我的文件不运行，我只是返回了提示符，没有任何输出。** 你很可能以为我让你输入 `print("Hello World!")`只是让你输 `"Hello World!"`。并不是，你要完整地、一字不差地把代码敲出来。