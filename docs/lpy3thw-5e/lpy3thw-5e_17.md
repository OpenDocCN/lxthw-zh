## 练习 15：读取文件

你知道如何使用`input`或`argv`从用户那里获取输入。现在你将学习如何从文件中读取。你可能需要仔细研究这个练习，以理解发生了什么，所以仔细做练习并记住你的检查。如果不小心处理文件，这是一种*擦除你的工作*的简单方法。

这个练习涉及编写两个文件。一个是你将运行的通常的`ex15.py`文件，但*另一个*名为`ex15_sample.txt`。这第二个文件不是一个脚本，而是一个我们将在我们的脚本中读取的纯文本文件。以下是该文件的内容：

```py
1   This is stuff I typed into a file.
2   It is really cool stuff.
3   Lots and lots of fun to have in here.
```

我们想要在我们的脚本中“打开”那个文件并将其打印出来。然而，我们不想将名为`ex15_sample.txt`的文件名直接“硬编码”到我们的脚本中。所谓“硬编码”是指将应该来自用户的一些信息作为字符串直接放在我们的源代码中。这是不好的，因为我们希望以后加载其他文件。解决方案是使用`argv`或`input`询问用户要打开哪个文件，而不是将文件名“硬编码”到脚本中。

列表 15.1：ex15.py

```py
 1   from sys import argv
 2
 3   script, filename = argv
 4
 5   txt = open(filename)
 6
 7   print(f"Here's your file {filename}:")
 8   print(txt.read())
 9
10   print("Type the filename again:")
11   file_again = input("> ")
12
13   txt_again = open(file_again)
14
15   print(txt_again.read())
```

这个文件中有一些花哨的东西，所以让我们快速地分解一下。

第 1-3 行使用`argv`获取文件名。接下来是第 5 行，我们使用一个新命令：`open`。现在运行`pydoc open`并阅读说明。注意，就像你自己的脚本和`input`一样，它接受一个参数并返回一个可以设置为你自己变量的值。你刚刚打开了一个文件。

第 7 行打印了一条小消息，但在第 8 行，我们有一些非常新颖和令人兴奋的东西。我们在`txt`上调用了一个名为`read`的函数。你从`open`得到的是一个`file`，它也有你可以给它的命令。你可以使用`.`（点）命令一个文件，命令的名称和参数，就像`open`和`input`一样。不同之处在于`txt.read()`表示，“嘿`txt`！执行你的读取命令，不带参数！”

文件的其余部分基本相同，但我们将在*学习练习*部分留给你来分析。

### 你应该看到什么

警告！

注意！我说了要注意！你之前只是用脚本的名称运行脚本，但现在你正在使用`argv`，你必须添加参数。看看以下示例的第一行，你会看到我执行`python ex15.py ex15_sample.txt`来运行它。在`ex15.py`脚本名称后面看到额外的参数`ex15_sample.txt`。如果你不输入，你会得到一个错误，所以要注意！

我创建了一个名为`ex15_sample.txt`的文件并运行了我的脚本。

```py
 1   Here's your file ex15_sample.txt:
 2   This is stuff I typed into a file.
 3   It is really cool stuff.
 4   Lots and lots of fun to have in here.
 5
 6
 7   Type the filename again:
 8   > ex15_sample.txt
 9   This is stuff I typed into a file.
10   It is really cool stuff.
11   Lots and lots of fun to have in here.
```

### 学习练习

这是一个很大的飞跃，所以在继续之前，请确保你尽力完成这些学习练习。

1.  在每一行上面，用英语写出那行代码的作用。

2.  如果你不确定，向别人寻求帮助或在网上搜索。很多时候搜索“python3 THING”会找到关于 Python 中那个 THING 做什么的答案。尝试搜索“python3 open”。

3.  我在这里使用了“命令”这个词，但命令也被称为“函数”和“方法”。你将在本书后面学习有关函数和方法的知识。

4.  删除使用`input`并再次运行脚本的 10-15 行。

5.  只使用`input`，尝试以这种方式运行脚本。为什么有一种获取文件名的方式比另一种更好？

6.  启动`python3`以启动`python3` shell，并从提示符中像在这个程序中一样使用`open`。注意你如何可以在`python3`中打开文件并运行`read`？

7.  让你的脚本也在`txt`和`txt_again`变量上调用`close()`。在完成文件操作后关闭文件是很重要的。

### 常见学生问题

**`txt = open(filename)`是否返回文件的内容？** 不，它不会。它实际上创建了一个叫做“文件对象”的东西。你可以把文件想象成 50 年代大型计算机上看到的旧磁带驱动器，甚至像今天的 DVD 播放器。你可以在其中移动，然后“读取”它们，但 DVD 播放器不是 DVD，就像文件对象不是文件内容一样。

**我无法像你在第 7 个学习任务中说的那样在终端/PowerShell 中输入代码**。首先，从命令行中只需输入`python3`并按 Enter。现在你在`python3`中，就像我们之前做过几次一样。然后你可以输入代码，Python 会逐段运行它。尝试一下。要退出，请输入`quit()`并按 Enter。

**为什么我们打开文件两次时没有错误？** Python 不会限制你多次打开文件，有时这是必要的。

**`from sys import argv`是什么意思？** 现在只需理解`sys`是一个包，这个短语只是说从那个包中获取`argv`功能。你以后会学到更多。

**我将文件名放在** `script, ex15_sample.txt = argv` **中，但它不起作用**。不，这不是你应该做的。确保代码与我的完全一样，然后像我一样从命令行运行它。你不需要放文件名进去；让 Python 放进去。
