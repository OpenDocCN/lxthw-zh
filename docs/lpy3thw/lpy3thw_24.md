# 练习 20 函数和文件

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.25.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.25.learn-py3.md)

记住你的函数 checklist，然后在做这个练习的时候注意函数是如何和文件一起工作并发挥一些作用的。

ex20.py

```py
1  from sys import argv
2
3 script, input_file = argv
4
5  def print_all(f):
6  print(f.read())
7
8  def rewind(f):
9 f.seek(0)
10
11  def print_a_line(line_count, f):
12  print(line_count, f.readline())
13
14 current_file = open(input_file)
15
16  print("First let's print the whole file:\n")
17
18 print_all(current_file)
19
20  print("Now let's rewind, kind of like a tape.")
21
22 rewind(current_file)
23
24  print("Let's print three lines:")
25
26 current_line =  1
27 print_a_line(current_line, current_file)
28
29 current_line = current_line +  1
30 print_a_line(current_line, current_file)
31
32 current_line = current_line +  1
33 print_a_line(current_line, current_file)
```

着重注意我们是如何在每次运行 print_a_line 的时候把当前行的数字传递出去的。

## 你会看到

练习 20 会话

```py
1.  `$ python3.6 ex20.py test.txt`2.  `First  let's print the whole file:`4.  ``This is line 1``5.  ``This is line 2``6.  ``This is line 3``8.  ```Now let's rewind, kind of like a tape.```py 9.  ```Let's print three lines:```py10.  ```1   This is line 1```py12.  ````2   This is line 2```py`14.  ````3   This is line 3```py`
```

 ``## 附加练习

*   在每一行上方添加注释解释它的作用。
*   每次 `print_a_line` 运行的时候，你都在传入一个 `current_line` 变量。写出每一次调用函数的时候 `current_line` 等于什么，然后找出它是如何变成 `print_a_line` 里面的 `line_count` 的。
*   找出每一个用到函数的地方，然后检查它的 `def` 确保你给出了正确的参数。
*   在网上搜搜 `seek` 这个函数的作用。试着输入 `pydoc file`，看看你能否从这里看明白。然后试着输入 `pydoc file.seek` 再看看 `seek` 是用来干嘛的。
*   搜一下简化符号 `+=` ，然后用 `+=` 重新写这个脚本。

## 常见问题

**在 `print_all` 和其他函数里的 `f` 是什么东西？** `f` 是一个变量，就像你在练习 18 中函数的变量一样，只不过这次它是一个文件。文件在 Python 里面有点类似于一个老式电脑里面的磁带驱动器，或者一个 DVD 播放机。它有一个“读取头”（read head），你可以在文件里 `seek` （寻找）这个读取头所在的位置，然后在那里工作。每次你做 `f.seek(0)` 的时候你都会从移动到文件最开始，每次你做 `f.readline()` 的时候，你都在从文件里读取一行内容，并且把读取头移动到 `\n` 后面，也就是每行结束的地方。 我会在后面给你做更详细的解释。

**为什么 `seek(0)` 没有把 `current_line` 设置为 0？** 首先，`seek()` 函数处理的是字节（bytes），不是行。`seek(0)` 这个代码把文件移动到 0 字节（也就是第一个字节处）。其次，`current_line` 只是一个变量并且跟这个文件没有任何实际联系。我们是在手动累加它。

**什么是 `+=` ？** 你知道在英语里我们可以把 “it is” 写成 “it's” ，或者把 “you are” 写成“you're” ，这叫缩写（contraction）。而 `+=` 就像 `=` 和 `+` 两种运算的缩写。也就是 `x = x + y` 就等同于 `x += y` 。

**`readline()` 是怎么知道每一行在哪儿的？** `readline()` 里面的代码能够扫描文件的每个字节，当它发现一个 `\n` 字符，它就会停止扫描这个文件，然后回到它发现的地方。文件 `f` 就负责在每次调用 `readline()` 之后维持文件的当前位置，以此来保证它能阅读到每一行。

**为什么文件中的行之间会有空行？** `readline()` 函数返回文件中每行最后的 `\n` 。又在 `print` 函数的结尾加上一个 `end = " "` 来避免给每行加上两个 `\n` 。``