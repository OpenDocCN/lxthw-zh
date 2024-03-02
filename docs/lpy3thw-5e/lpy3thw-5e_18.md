## 练习 16：读写文件

如果你做了上一个练习的学习练习，你应该看到各种可以给文件的命令（方法/函数）。这是我希望你记住的命令列表：

+   `close` – 关闭文件。就像文本编辑器或文字处理器中的`文件->保存..`一样。

+   `read` – 读取文件的内容。你可以将结果赋值给一个变量。

+   `readline` – 读取文本文件的一行。

+   `truncate` – 清空文件。如果你关心文件的话要小心。

+   `write('stuff')` – 将“stuff”写入文件。

+   `seek(0)` – 将读/写位置移动到文件的开头。

记住每个命令的一种方法是想象一下黑胶唱片、磁带、VHS 磁带、DVD 或 CD 播放器。在计算机的早期，数据存储在这些媒体上，所以许多文件操作仍然类似于一个线性存储系统。磁带和 DVD 驱动器需要“寻找”到一个特定的位置，然后你可以在那个位置读取或写入。今天我们有操作系统和存储介质模糊了随机存取内存和磁盘驱动器之间的界限，但我们仍然使用一个必须移动的线性磁带的读/写头的旧概念。

目前，这些是你需要知道的重要命令。其中一些需要参数，但我们并不真的关心。你只需要记住`write`需要一个你想写入文件的字符串参数。

让我们利用其中的一些内容制作一个简单的文本编辑器：

列表 16.1: ex16.py

```py
 1   filename = "test.txt"
 2
 3   print(f"We're going to erase {filename}.")
 4   print("If you don't want that, hit CTRL-C *(*^C*)*.")
 5   print("If you do want that, hit RETURN.")
 6
 7   **input(**"?")
 8
 9   print("Opening the file...")
10   target = **open(**filename, 'w')
11
12   print("Truncating the file. Goodbye!")
13   target.truncate**()**
14
15   print("Now I'm going to ask you for three lines.")
16
17   line1 = **input(**"line 1: ")
18   line2 = **input(**"line 2: ")
19   line3 = **input(**"line 3: ")
20
21   print("I'm going to write these to the file.")
22
23   target.write**(**line1)
24   target.write**(**"\n")
25   target.write**(**line2)
26   target.write**(**"\n")
27   target.write**(**line3)
28   target.write**(**"\n")
29
30   print("And finally, we close it.")
31   target.close**()**
```

那是一个很大的文件，可能是你输入的最大的文件。所以慢慢来，检查一下，*经常运行*，慢慢来。一个技巧是一次运行一部分。先运行 1-2 行，然后再运行两行，再运行几行，直到全部完成并运行。

### 你应该看到的内容

实际上你会看到两件事。首先是你新脚本的输出：

```py
 1   We're going to erase test.txt.
 2   If you don't want that, hit CTRL-C (^C).
 3   If you do want that, hit RETURN.
 4   ?
 5   Opening the file...
 6   Truncating the file. Goodbye!
 7   Now I'm going to ask you for three lines.
 8   line 1:  Mary had a little lamb
 9   line 2:  Its fleece was white as snow
10   line 3:  It was also tasty
11   I'm going to write these to the file.
12   And finally, we close it.
```

现在，打开你创建的文件（在我的案例中是`test.txt`），使用 Jupyter 的左侧面板查看一下。整洁，对吧？

### 学习练习

1.  如果你不理解这个，回过头来，使用注释技巧来弄清楚。在每一行上加一个简单的英文注释将帮助你理解，或者至少让你知道你需要更多地研究。

2.  编写一个类似于上一个练习 14 的`.py`脚本，使用`read`（练习 15）和`argv`（练习 13）来读取你刚刚创建的文件。确保你在终端/PowerShell 中运行而不是在 Jupyter 中。

3.  这个文件中有太多的重复。使用字符串、格式和转义来用一个`target.write()`命令打印出`line1`、`line2`和`line3`，而不是六个命令。

4.  找出为什么我们需要将`'w'`作为`open`的额外参数传递。提示：`open`试图通过让你明确表示你要写入一个文件来保持安全。

5.  如果以**'w'**模式打开文件，那么你真的需要**target.truncate()**吗？阅读 Python 的**open**函数的文档，看看这是否属实。

### 常见学生问题

**在使用** **'w'** **参数时，** `truncate()` **是必需的吗？** 参见学习任务 5。

**'w'** **代表什么？** 实际上，它只是一个包含文件模式字符的字符串。如果使用**'w'**，那么你是在说“以‘写’模式打开此文件”，这就是**'w'** 字符的原因。还有**'r'**代表“读取”，**'a'**代表追加，以及这些的修饰符。

**我可以使用哪些文件模式的修饰符？** 现在最重要的是要知道**+**修饰符，这样你就可以使用**'w+'**，**'r+'**和**'a+'**。这将以读取和写入模式打开文件，并根据使用的字符，以不同的方式定位文件。

**只需执行** **open(filename)** **就会以** **'r'** **（读取）模式打开文件吗？** 是的，这是**open()**函数的默认设置。
