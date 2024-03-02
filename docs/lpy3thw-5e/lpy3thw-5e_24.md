## 练习 21：函数可以返回值

你一直在使用`=`字符来命名变量并将它们设置为数字或字符串。现在我们将再次让你大开眼界，向你展示如何使用`=`和一个新的 Python 词`return`来将变量设置为来自函数的*值*。有一件事要特别注意，但首先输入这个：

代码清单 21.1: ex21.py

```py
 1   **def** add**(**a, b**)**:
 2       **print(**f"ADDING {a} + {b}"**)**
 3       **return** a + b
 4
 5   **def** subtract**(**a, b**)**:
 6       **print(**f"SUBTRACTING {a} - {b}"**)**
 7       **return** a - b
 8
 9   **def** multiply**(**a, b**)**:
10       **print(**f"MULTIPLYING {a} * {b}"**)**
11       **return** a * b
12
13   **def** divide**(**a, b**)**:
14       **print(**f"DIVIDING {a} / {b}"**)**
15       **return** a / b
16
17
18   **print(**"Let's do some math with just functions!"**)**
19
20   age = add**(**30, 5**)**
21   height = subtract**(**78, 4**)**
22   weight = multiply**(**90, 2**)**
23   iq = divide**(**100, 2**)**
24
25   **print(**f"Age: {age}, Height: {height}, Weight: {weight}, IQ: {iq}"**)**
26
27
28   # A puzzle for the extra credit, type it in anyway.
29   **print(**"Here is a puzzle."**)**
30
31   what = add**(**age, subtract**(**height, multiply**(**weight, divide**(**iq, 2**))))**
32
33   **print(**"That becomes: ", what, "Can you do it by hand?"**)**
```

现在我们正在为`add`、`subtract`、`multiply`和`divide`做我们自己的数学函数。需要注意的重要一点是我们说的最后一行`return a + b`（在`add`中）。这样做的效果如下：

1.  我们的函数被调用时带有两个参数：`a`和`b`。

2.  我们打印出我们的函数正在做的事情，在这种情况下是“ADDING”。

3.  然后我们告诉 Python 做一些有点反向的事情：我们返回`a + b`的加法。你可以这样说，“我将`a`和`b`相加然后返回它们。”

4.  Python 将这两个数字相加。然后当函数结束时，运行它的任何行都可以将`a + b`的结果赋给一个变量。

就像本书中的许多其他内容一样，你应该慢慢来，分解问题，并尝试追踪发生了什么。为了帮助，有额外的练习来解决一个谜题并学到一些有趣的东西。

### 你应该看到的结果

```py
 1   Let's do some math with just functions!
 2   ADDING 30 + 5
 3   SUBTRACTING 78 - 4
 4   MULTIPLYING 90 * 2
 5   DIVIDING 100 / 2
 6   Age: 35, Height: 74, Weight: 180, IQ: 50.0
 7   Here is a puzzle.
 8   DIVIDING 50.0 / 2
 9   MULTIPLYING 180 * 25.0
10   SUBTRACTING 74 - 4500.0
11   ADDING 35 + -4426.0
12   That becomes: -4391.0 Can you do it by hand?
```

### 学习扩展

1.  如果你不确定`return`的作用，尝试编写一些自己的函数，并让它们返回一些值。你可以返回任何可以放在`=`右侧的东西。

2.  脚本的结尾是一个谜题。我正在将一个函数的返回值作为另一个函数的参数。我正在以链式方式执行这个操作，所以我有点像使用函数创建一个公式。看起来很奇怪，但如果你运行脚本，你会看到结果。你应该尝试找出能够重新创建相同操作集的正常公式。

3.  一旦你为谜题找到了公式，就深入其中，看看当你修改函数的部分时会发生什么。试着故意改变它以生成另一个值。

4.  做相反的操作。编写一个简单的公式，并以相同的方式使用函数来计算它。

这个练习可能会让你的大脑混乱，但慢慢来，把它当作一个小游戏。像这样解决谜题是编程变得有趣的地方，所以在我们继续进行时，我会给你更多类似的小问题。

### 常见学生问题

**为什么 Python 打印公式或函数“反向”？** 它实际上不是反向的，而是“里外相反”。当你开始将函数分解为单独的公式和函数时，你会看到它是如何工作的。试着理解我所说的“里外相反”而不是“反向”。

**我如何使用** `input()` **输入自己的值？** 还记得`int(input())`吗？问题在于你无法输入浮点数，所以也尝试使用`float(input())`。

**“写出一个公式”是什么意思？** 尝试以`24 + 34 / 100 - 1023`为起点。将其转换为使用函数。现在想出你自己类似的数学方程，并使用变量使其更像一个公式。
