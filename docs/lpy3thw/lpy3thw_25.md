# 练习 21 函数可以返回一些东西

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.26.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.26.learn-py3.md)

你已经使用了 `=` 来命名变量并给变量赋予数值或字符串。接下来我会教你如何用 `=` 和一个新的 python 字符 `return` 来把函数中的变量设置为一个值。有一点需要密切注意，但是先输入如下代码：

ex21.py

```py
1  def add(a, b):
2  print(f"ADDING {a} + {b}")
3  return a + b
4
5  def subtract(a, b):
6  print(f"SUBTRACTING {a} - {b}")
7  return a - b
8
9  def multiply(a, b):
10  print(f"MULTIPLYING {a} * {b}")
11  return a * b
12
13  def divide(a, b):
14  print(f"DIVIDING {a} / {b}")
15  return a / b
16
17
18  print("Let's do some math with just functions!")
19
20 age = add(30,  5)
21 height = subtract(78,  4)
22 weight = multiply(90,  2)
23 iq = divide(100,  2)
24
25  print(f"Age: {age}, Height: {height}, Weight: {weight}, IQ: {iq}")
26
27
28  # A puzzle for the extra credit, type it in anyway.
29  print("Here is a puzzle.")
30
31 what = add(age, subtract(height, multiply(weight, divide(iq,  2))))
32
33  print("That becomes: ", what,  "Can you do it by hand?")
```

我们现在要做我们自己的加减乘除数学运算了。我说的要密切注意的是 `add` 函数里面的 `return a + b` ，这步做的是这些事情：

*   我们的函数是以两个参数被调用的： `a` 和 `b` 。
*   我们把函数所做的事情打印出来，在本例中是 “ADDING”。
*   然后我们让 Python 做一些反向的事情：我们返回 `a + b` 的和。你可以这样描述：我用 `a` 加上 `b` ，然后返回它们的结果。
*   Python 把这两个数加起来。然后当函数终止的时候，运行了这个函数的任何一行都能够将 `a + b` 的结果赋予一个变量。和这本书里其他内容比起来，这块你确实应该把节奏放慢一些，把代码打乱，然后试着琢磨一下每一步都发生了什么。

## 你会看到

练习 21 会话

```py
$ python3.6 ex21.py
2.  `Let's do some math with just functions!` 3.  `ADDING 30 + 5`4.  `SUBTRACTING 78 - 4`5.  `MULTIPLYING 90 * 2`6.  `DIVIDING 100 / 2`7.  `Age: 35, Height: 74, Weight: 180, IQ: 50.0`8.  `Here is a puzzle.`9.  `DIVIDING 50.0 / 2`10.  `MULTIPLYING 180 * 25.0`11.  `SUBTRACTING 74 - 4500.0`12.  `ADDING 35 + -4426.0`13.  `That becomes:   -4391.0`14.  `Can you do it by hand?`
```

## 附加练习

*   如果你还不能真正理解 `return` 是干什么的，试着写几个你自己的函数，并且让它们返回一些值。你可以让它 `return` 任何东西，只要你把它们放在 `=` 右边即可。
*   脚本的最后是一个难题。我在用一个函数的返回值作为另一个函数的参数，这是在一个链（chain）里面进行的，这样就用函数创建了一个公式。它看起来确实很难，但是如果你运行这个脚本，你就可以看到结果。你要做的就是试着弄明白创建同样操作的平常的函数是什么样的。
*   一旦你有了可以解出这个难题的公式，试着对函数的某些部分做做改动，看看会发生什么。有意改动一些数让它产生一些不同的值。
*   做相反的操作。写一个简单的公式，然后用同一种方式通过函数来计算它。这个练习可能真的很让你头大，但是放松，慢点学，把它当成是一个小游戏。正是解决这样的难题让编程如此有趣，所以之后我还会再给你一些小问题让你解决。

## 常见问题

**为什么 python 是“从后往前”（backward 打印公式或者函数的？** 它其实不是从后往前，它是从里到外（inside out）。当你开始把代码打乱成分开的公式和函数时，你会看到它是如何工作的。试着理解我说的 “inside out” 而不是 “backward” 。

**我如何使用 `input()` 来输入我自己的值？**还记得 `int(input())` 吗？这样做的问题是你不能输入浮点数，所以试着用 `float(input())` 来代替。

**你说的“写一个公式”是什么意思？** 先试试 `24 + 34 / 100 - 1023` 吧，变成使用函数来计算。然后自己想出一个类似的数学公式，要用变量让它看起来更像一个公式。