# 练习 17\. 更多文件

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.22.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.22.learn-py3.md)

现在让我们对文件做更多新的操作。我们会写一个 Python 脚本来把一个文件复制成另一个。代码会非常短，但是能让你学会对文件做更多的操作。

ex17.py

```py
1  from sys import argv
2  from os.path import exists
3
4 script, from_file, to_file = argv
5
6  print(f"Copying from {from_file} to {to_file}")
7
8  # we could do these two on one line, how?
9 in_file = open(from_file)
10 indata = in_file.read()
11
12  print(f"The input file is {len(indata)} bytes long")
13
14  print(f"Does the output file exist? {exists(to_file)}")
15  print("Ready, hit RETURN to continue, CTRL-C to abort.")
16 input()
17
18 out_file = open(to_file,  'w')
19 out_file.write(indata)
20
21  print("Alright, all done.")
22
23 out_file.close()
24 in_file.close()
```

你应该会很快注意到我们输出了另一个常用命令 `exists`。它会基于一个字符串里面的变量文件名来判断，如果一个文件存在，它就会返回 `True`，不存在就会返回 `False`。我们会在这本书的下半部分经常使用这个函数，现在你只用知道你是如何输出它的。

使用 `import` 可以调出海量的免费代码，这些是程序员已经写过的代码，你就不用重复造轮子了。

## 你会看到

像你其他的脚本文件一样运行 ex17.py ，再加上两个变量：一个是要复制的源文件，一个是要复制到的目标文件。我会使用一个叫 test.txt 的示例文件：

练习 17 会话 # first make a sample file echo "This is a test file." > test.txt # then look at it cat test.txt This is a test file. # now run our script on it python3.6 ex17.py test.txt new_file.txt Copying from test.txt to new_file.txt The input file is 21 bytes long Does the output file exist? False Ready, hit RETURN to continue, CTRL-C to abort. Alright, all done.

它应该对每一个文件都适用，多试一些看看会发生什么。注意不要动重要的文件。

| 警告！ |
| --- |
| 你应该注意到我使用了 `cat` 命令来显示文件内容。如果你不懂，可以在附录 A 的命令行速成教程中学到这个命令。 |

## 附加练习

*   这个脚本真的很烦人。在复制之前其实没必要问你，而且它打印了太多内容，试着通过删掉一些特征让这个脚本更简洁一些。
*   看看你把这个脚本缩到多短，我可以把它变成一行。
*   注意“你会看到”部分，我用了 `cat`，这是一种把文件打印到屏幕的简单办法，你可以输入 `man cat` 来看看关于这个命令的作用。
*   弄明白你为什么得在代码里写 `out_file.close()` 。
*   去读读 Python 的 import statement，然后自己试试 import 一些东西，看能不能成功运行。不成功也没关系。

## 常见问题

**为什么 `'w'` 要用引号？** 因为这是一个字符串。你已经用了一段时间字符串了，确保你知道它的含义。

**你不可能把那些代码变成一行！** 那；取决于；你；如何；定义；一行；代码。

**我觉得这个练习很难，这正常吗？** 是的，很正常。甚至到练习 36 的时候，或者学完这本书的时候，你可能还是会觉得很难。每个人的情况都不一样，所以坚持学下去，坚持做练习，要有耐心。

**`len()` 函数是什么作用？** 它能够取字符串的长度，然后返回一个数字。你可以试着玩玩。

**但我试着把这些代码缩短的时候，我在关闭文件时遇到了错误。** 你可能用了 `indata = open(from_file).read()`，这意味着你不需要在之后再输入 `in_file.close()` ，因为你已经到了脚本的最后。一旦那一行运行过之后，它就已经被 Python 关掉了。

**我收到了一个这样的错误：`Syntax:EOL while scanning string literal` 。** 你忘了在字符串后面加引号了，再检查一遍的代码。