## 练习 34：While 循环

现在让我们用一个新的循环完全震惊你，`while-loop`。`while-loop`会持续执行其下的代码块，只要布尔表达式为`True`。

等等，你一直跟上术语了吗？如果我们写一行并以`:`（冒号）结尾，那告诉 Python 开始一个新的代码块？然后我们缩进，这就是新代码。这一切都是关于构建你的程序，让 Python 知道你的意图。如果你没有理解这个概念，那就回去多做一些关于`if`语句、函数和`for`循环的工作，直到你理解为止。

后面我们会有一些练习，训练你的大脑阅读这些结构，类似于我们如何将布尔表达式烙印在你的大脑中。

回到`while-loop`。它们的作用就像一个`if`语句的测试，但不同于只运行代码块*一次*，它们会跳回到`while`所在的“顶部”，并重复。`while`循环会一直运行，直到表达式为`False`。

`while`循环的问题在于：有时它们不会停止。如果你的意图只是一直循环直到宇宙的尽头，那么这很好。否则，你几乎总是希望你的循环最终会结束。

为了避免这些问题，有一些规则需要遵循：

1.  确保你谨慎使用`while`循环。通常`for`循环更好。

2.  检查你的`while`语句，并确保布尔测试最终会变为`False`。

3.  如果有疑问，在`while`循环的顶部和底部打印出你的测试变量，看看它在做什么。

在这个练习中，你将学习`while`循环，并在进行以下三个检查时使用它们：

列表 34.1: ex34.py

```py
 1   i = 0
 2   numbers = []
 3
 4   **while** i < 6:
 5       **print(**f"At the top i is {i}"**)**
 6       numbers.append**(**i**)**
 7
 8       i = i + 1
 9       **print(**"Numbers now: ", numbers**)**
10       **print(**f"At the bottom i is {i}"**)**
11
12
13   **print(**"The numbers: "**)**
14
15   **for** num **in** numbers:
16       **print(**num**)**
```

### 你应该看到的结果

```py
 1   At the top i is 0
 2   Numbers now: [0]
 3   At the bottom i is 1
 4   At the top i is 1
 5   Numbers now: [0, 1]
 6   At the bottom i is 2
 7   At the top i is 2
 8   Numbers now: [0, 1, 2]
 9   At the bottom i is 3
10   At the top i is 3
11   Numbers now: [0, 1, 2, 3]
12   At the bottom i is 4
13   At the top i is 4
14   Numbers now: [0, 1, 2, 3, 4]
15   At the bottom i is 5
16   At the top i is 5
17   Numbers now: [0, 1, 2, 3, 4, 5]
18   At the bottom i is 6
19   The numbers:
20   0
21   1
22   2
23   3
24   4
25   5
```

#### `dis()`它

在我们代码之游戏的最终“支线任务”中，你将使用`dis()`来分析`while-loop`的工作原理：

```py
1   from dis import dis
2
3   dis('''
4   i = 0
5   while i < 6:
6       i = i + 1
7   ''')
```

你已经看到了大部分这些字节码，所以现在轮到你去弄清楚这个`dis()`输出与 Python 有什么关系了。记住你可以在[文档的末尾](https://docs.python.org/3/library/dis.xhtml#python-bytecode-instructions)的`[dis()](https://docs.python.org/3/library/dis.xhtml#python-bytecode-instructions)`[文档](https://docs.python.org/3/library/dis.xhtml#python-bytecode-instructions)中查找所有的字节码。祝你好运！

### 学习练习

1.  将这个`while-loop`转换为一个可以调用的函数，并用一个变量替换测试中的`6`（`i < 6`）。

2.  使用这个函数来重写脚本以尝试不同的数字。

3.  在函数参数中添加另一个变量，你可以传入它，以便你可以更改第 8 行的`+ 1`，这样你就可以改变增量是多少。

4.  再次重写脚本以使用这个函数，看看会有什么影响。

5.  重写它以使用`for-loops`和`range`。你还需要在中间保留增量器吗？如果不去掉它会发生什么？

如果在任何时候你这样做时出现问题（很可能会），只需按住`CTRL`并按下`c`（`CTRL-c`），程序就会中止。

### 常见学生问题

**`for`**-循环和**`while`**-循环有什么区别？**`for`**-循环只能在“集合”上进行迭代（循环）。**`while`**-循环可以进行任何类型的迭代（循环）。然而，**`while`**-循环更难正确使用，通常可以用**`for`**-循环完成许多任务。

**循环很难。我该如何理解它们？** 人们不理解循环的主要原因是因为他们无法跟随代码的“跳跃”。当循环运行时，它会执行其代码块，最后跳回顶部。为了可视化这一点，在循环中到处放置`print`语句，打印出 Python 在循环中运行的位置以及这些点上变量的设置。在循环之前、顶部、中间和底部编写`print`行。研究输出并尝试理解正在进行的跳跃。
