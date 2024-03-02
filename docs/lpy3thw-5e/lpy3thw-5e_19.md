## 练习 17. 更多文件

现在让我们做更多关于文件的事情。我们将编写一个 Python 脚本将一个文件复制到另一个文件。这将非常简短，但会给你关于文件的其他操作想法。

列表 17.1：ex17.py

```py
 1   **from** sys **import** argv
 2   **from** os.path **import** exists
 3
 4   from_file = "test.txt"
 5   to_file = "new_test.txt"
 6
 7   **print(**f"Copying from {from_file} to {to_file}"**)**
 8
 9   # we could do these two on one line, how?
10   in_file = **open(**from_file**)**
11   indata = in_file.read**()**
12
13   **print(**f"The input file is {len*(*indata*)*} bytes long"**)**
14
15   **print(**f"Does the output file exist? {exists*(*to_file*)*}"**)**
16   **print(**"Ready, hit RETURN to continue, CTRL-C to abort."**)**
17   **input()**
18
19   out_file = **open(**to_file, 'w'**)**
20   out_file.write**(**indata**)**
21
22   **print(**"Alright, all done."**)**
23
24   out_file.close**()**
25   in_file.close**()**
```

你应该立即注意到我们`import`了另一个方便的命令叫做`exists`。如果文件存在，它会返回`True`，基于它的名称作为字符串参数。如果不存在，则返回`False`。我们将在本书的后半部分使用这个函数来做很多事情，但现在你应该看看如何导入它。

使用`import`是一种获取其他更好（通常是）程序员编写的大量免费代码的方法，这样你就不必自己编写它。

### 你应该看到的内容

就像你的其他脚本一样，用两个参数运行这个脚本：要复制的文件和要复制到的文件。我将使用一个名为`test.txt`的简单测试文件：

```py
1   Copying from test.txt to new_test.txt
2   The input file is 70 bytes long
3   Does the output file exist? True
4   Ready, hit RETURN to continue, CTRL-C to abort.
5
6   Alright, all done.
```

它应该适用于任何文件。尝试更多文件并看看会发生什么。只是要小心不要破坏重要文件。

警告！

你看到我用`echo`制作文件和`cat`显示文件的技巧了吗？你可以在附录 A“命令行速成课程”中学习如何做到这一点。

### 学习练习

1\. 这个脚本*真的*很烦人。在复制之前没有必要询问你，而且在屏幕上打印出太多内容。尝试通过删除功能使脚本更加友好易用。

2\. 看看你能把脚本做得多短。我可以让这一行很长。

3\. 注意在“你应该看到的内容”末尾我使用了一个叫做`cat`的东西？这是一个“连接”文件的旧命令，但主要是一个将文件打印到屏幕的简单方法。输入`man cat`来了解它。

4\. 找出为什么你需要在代码中写`out_file.close()`。

5\. 去了解一下 Python 的`import`语句，并开始使用`python3`尝试一下。尝试导入一些东西，看看你是否能做对。如果做不对也没关系。

6\. 尝试将这段代码转换为一个`ex17.py`脚本，你可以再次从终端/PowerShell 运行。如果你已经厌倦了 Jupyter 的文本编辑器，那么可以查看*[First Steps](https://learncodethehardway.org/first_steps/python/)*部分提到的编辑器。

### 常见学生问题

**为什么** `'w'` **要加引号？** 那是一个字符串。你已经使用字符串一段时间了。确保你知道什么是字符串。

**不可能让这一行变成一行！** 那个；取决于；你；如何；定义；一行；代码。

**感觉这个练习很难是正常的吗？** 是的，这是完全正常的。直到 Exercise 36，甚至可能在你完成这本书并用 Python 做一些东西之后，编程可能才会“点亮”。每个人都不同，所以继续前进，继续复习你遇到困难的练习，直到理解为止。要有耐心。

**`len()`函数是做什么的？** 它获取你传递给它的字符串的长度，然后将其作为一个数字返回。试着玩一下。

**当我试图缩短这个脚本时，在结尾关闭文件时出现错误**。你可能做了类似这样的事情，`indata = open(from_file).read()`，这意味着当你到达脚本结尾时就不需要再执行`in_file.close()`。一旦那一行运行，Python 应该已经关闭了它。

**我收到一个** `Syntax:EOL while scanning string literal` **错误**。你忘记用引号正确结束一个字符串。再去看看那一行。
