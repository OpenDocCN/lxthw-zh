## 练习 20：函数和文件

记住函数的清单，然后在这个练习中要特别注意函数和文件如何一起工作以制作有用的东西。你还应该继续在运行代码之前只输入几行。如果发现自己输入了太多行，请删除它们然后重新输入。这样做可以使用`python`来训练你对 Python 的理解。

这是这个练习的代码。再次强调，如果你觉得 Jupyter 难以使用，那么写一个`ex20.py`文件并以这种方式运行它。

列表 20.1: ex20.py

```py
 1   from sys import argv
 2
 3   script, input_file = argv
 4
 5   def print_all(f):
 6       print(f.read())
 7
 8   def rewind(f):
 9       f.seek(0)
10
11   def print_a_line(line_count, f):
12       print(line_count, f.readline())
13
14   current_file = open(input_file)
15
16   print("First let's print the whole file:\n")
17
18   print_all(current_file)
19
20   print("Now let's rewind, kind of like a tape.")
21
22   rewind(current_file)
23
24   print("Let's print three lines:")
25
26   current_line = 1
27   print_a_line(current_line, current_file)
28
29   current_line = current_line + 1
30   print_a_line(current_line, current_file)
31
32   current_line = current_line + 1
33   print_a_line(current_line, current_file)
```

注意每次运行`print_a_line`时我们如何传入当前行号。在这个练习中没有什么新的。它有函数，你知道那些。它有文件，你也知道那些。只要花点时间，你就能理解。

### 你应该看到的内容

```py
 1   First let's print the whole file:
 2
 3   This is line 1
 4   This is line 2
 5   This is line 3
 6
 7   Now let's rewind, kind of like a tape.
 8   Let's print three lines:
 9   1 This is line 1
10
11   2 This is line 2
12
13   3 This is line 3
```

### 学习扩展

1.  为每一行写英文注释以理解该行的作用。

2.  每次运行`print_a_line`时，你都会传入一个变量`current_line`。写出每个函数调用中`current_line`等于什么，并跟踪它如何变成`print_a_line`中的`line_count`。

3.  找到每个函数被使用的地方，并检查其`def`以确保你给出了正确的参数。

4.  在线研究`file`的`seek`函数是做什么的。尝试`pydoc file`，看看能否从中弄清楚。然后尝试`pydoc file.seek`来查看`seek`的作用。

5.  研究`+=`的简写表示法，并重写脚本以使用`+=`。

### 常见学生问题

**`print_all`和其他函数中的`f`是什么？** `f`就像你在练习 18 中的其他函数中一样，只是这次它是一个文件。在 Python 中，文件有点像主机上的旧磁带驱动器或者可能是 DVD 播放器。它有一个“读头”，你可以“寻找”这个读头在文件中的位置，然后在那里进行操作。每次你执行`f.seek(0)`时，你都在移动到文件的开头。每次你执行`f.readline()`时，你都在从文件中读取一行，并将读头移动到结束该行的`\n`之后。随着你的学习，这将会有更多解释。

**为什么**`seek(0)`**不会将**`current_line`**设置为 0？** 首先，`seek()`函数处理的是*字节*，而不是行。代码`seek(0)`将文件移动到文件中的第 0 字节（第一个字节）。其次，`current_line`只是一个变量，与文件没有真正的连接。我们是手动递增它。

**`+=`是什么？** 你知道在英语中我可以将“it is”重写为“it’s”吗？或者我可以将“you are”重写为“you’re”吗？在英语中，这被称为“缩略形式”，这有点像`=`和`+`两个操作的缩写。这意味着`x = x + y`与`x += y`是相同的。

**`readline()`** 如何知道每行在哪里？在 `readline()` 内部有代码扫描文件的每个字节，直到找到一个 `\n` 字符，然后停止读取文件并返回到目前为止找到的内容。文件 `f` 负责在每次 `readline()` 调用后维护文件中的当前位置，以便继续读取每一行。

文件中的行之间为什么有空行？`readline()` 函数返回文件中该行末尾的 `\n`。在 `print` 函数调用的末尾添加 `end = ""` 可以避免在每行末尾添加双重 `\n`。
