# 练习 16\. 读写文件

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.21.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.21.learn-py3.md)

如果你做了上一节的附加练习，你应该看到了所有的命令（commands，modules，functions），你可以把这些命令施加给文件。以下是一些我想让你记住的命令：

*   **close** - 关闭文件，就像编辑器中的 “文件->另存为”一样。
*   **read** - 读取文件内容。你可以把读取结果赋给一个变量。
*   **readline** - 只读取文本文件的一行内容。
*   **truncate** - 清空文件。清空的时候要当心。
*   **write('stuff')** - 给文件写入一些“东西”。
*   **seek(0)** - 把读/写的位置移到文件最开头。

这些都是你需要知道的一些非常重要的命令。其中一些要用到参数，但是我们暂且不去重点关注。你只需要记住 `write` 命令需要你提供一个你要写入的文件的字符串参数。

让我们用这些命令做一个小小的编辑器：

ex16.py

```py
1  from sys import argv
2
3 script, filename = argv
4
5  print(f"We're going to erase {filename}.")
6  print("If you don't want that, hit CTRL-C (^C).")
7  print("If you do want that, hit RETURN.")
8
9 input("?")
10
11  print("Opening the file...")
12 target = open(filename,  'w')
13
14  print("Truncating the file. Goodbye!")
15 target.truncate()
16
17  print("Now I'm going to ask you for three lines.")
18
19 line1 = input("line 1: ")
20 line2 = input("line 2: ")
21 line3 = input("line 3: ")
22
23  print("I'm going to write these to the file.")
24
25 target.write(line1)
26 target.write("\n")
27 target.write(line2)
28 target.write("\n")
29 target.write(line3)
30 target.write("\n")
31
32  print("And finally, we close it.")
33 target.close()
```

这真是一个很大的文件，可能是你输入过的最大的文件了。所以慢一点，写完检查一下，然后再运行。你也可以写一点运行一点，比如先运行 1-8 行，然后再多运行 5 行，然后再多几行，直到所有的都完成和运行了。

## 你应该看到

事实上你应该看到两样东西，首先是你新脚本的输出结果：

练习 16 会话

```py
$ python3.6 ex16.py test.txt We're going to erase test.txt.
If you don't want that, hit CTRL-C (^C).  If you do want that, hit RETURN.
?
Opening the file...
Truncating the file.  Goodbye!
Now I'm going to ask you for three lines.
line 1: Mary had a little lamb
line 2: Its fleece was white as snow
line 3: It was also tasty
I'm going to write these to the file.
And  finally, we close it.
```

现在，用编辑器打开你创建的文件（比如我的是 test.txt），检查一下是不是对的。

## 附加练习

*   如果你理解不了这个练习，回过头去按照给每行加注释的方法再过一遍，注释能帮助你理解每一行的意思，至少让你知道你不理解的地方在哪里，然后动手去查找答案。
*   写一个类似于上个练习的脚本，使用 `read` 和 `argv` 来读取你刚刚创建的文件。
*   这个练习中有太多的重复，试着用一个 `target.write()` 命令来打印 line1、line2、line3，你可以使用字符串、格式字符串和转义字符。
*   弄明白为什么我们要用一个 `'w'` 作为一个额外的参数来打开。提示：通过明确说明你想要写入一个文件，来安全地打开它。
*   如果你用 `w` 模式打开文件，那你还需要 `target.truncate()` 吗？ 读一读 Python 的 open 函数文件，来搞明白这个问题。

## 常见问题

**`truncate()` 对于 `'w'` 参数来说是必须的吗？** 详见附加练习 5。

**`'w'` 到底是什么意思？** 它真的只是一个有字符的字符串，来表示文件的一种模式。如果你用了 `'w'` ，就代表你说“用 ‘write’ 模式打开这个文件。此外还有 `'r'` 表示 read 模式，`'a'` 表示增补模式，后面还可能加一些修饰符（modifiers）。

**我能对文件使用哪些修饰符？** 目前最重要的一个就是 `+` ，你可以用 `'w+'`， `'r+'` 以及 `'a+'`。这样会让文件以读和写的模式打开，取决于你用的是那个符号以及文件所在的位置等。

**如果只输入 `open(filename)` 是不是就用 `'r'` （读）模式打开？** 是的，那是 `open()` 函数的默认值。