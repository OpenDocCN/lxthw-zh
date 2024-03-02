# 练习 19 函数和变量

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.24.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.24.learn-py3.md)

函数是一个信息量巨大的东西，但是别担心，老老实实做练习，仔仔细细核对 checklist，你最终会掌握它的。

有个小点你可能没注意到，我们会在之后进行强化：你函数里面的变量跟你脚本里面的变量没有关联。通过下面这个练习思考一下这个问题：

ex19.py

```py
1  def cheese_and_crackers(cheese_count, boxes_of_crackers):
2  print(f"You have {cheese_count} cheeses!")
3  print(f"You have {boxes_of_crackers} boxes of crackers!"
4  print("Man that's enough for a party!")
5  print("Get a blanket.\n")
6
7
8  print("We can just give the function numbers directly:")
9 cheese_and_crackers(20,  30)
10
11
12  print("OR, we can use variables from our script:")
13 amount_of_cheese =  10
14 amount_of_crackers =  50
15
16 cheese_and_crackers(amount_of_cheese, amount_of_crackers)
17
18
19  print("We can even do math inside too:")
20 cheese_and_crackers(10  +  20,  5  +  6)
21
22
23  print("And we can combine the two, variables and math:")
24 cheese_and_crackers(amount_of_cheese +  100, amount_of_crackers +  1000)
```

这个练习展示了我们可以给函数 `cheese_and_crackers` 赋值的几种不同的方式，我们可以直接给它数字，或者变量，亦或是数学运算，甚至是数学运算和变量的结合。

从某种程度上说，函数的参数有点类似于我们给变量赋值时的 `=` 符号 。事实上，如果你可以用 `=` 来定义一个东西，你就可以把它作为参数赋给函数。

## 你会看到

你应该研究一下这个脚本的输出结果，把它和你之前的脚本输出结果对比一下。

练习 19 会话

```py
1.  `$ python3.6 ex19.py`2.  `We can just give the function numbers directly:`3.  `You have 20 cheeses!`4.  `You have 30 boxes of crackers!`5.  `Man that's enough for a party!`6.  `Get a blanket.`8.  ``OR, we can use variables from our script:``9.  ``You have 10 cheeses!``10.  ``You have 50 boxes of crackers!``11.  ``Man that's enough for a party!``12.  ``Get a blanket.``14.  ```We can even do math inside too:```py15.  ```You have 30 cheeses!```py16.  ```You have 11 boxes of crackers!```py17.  ```Man that's enough for a party!```py18.  ```Get a blanket.```py20.  ````And we can combine the two, variables and math:```py`21.  ```You have 110 cheeses!```py22.  ```You have 1050 boxes of crackers!```py23.  ```Man that's enough for a party!```py24.  ```Get a blanket.```py
```

 ``## 附加练习

*   回顾一遍这个脚本，然后在每一行上方加上注释，解释它的作用。
*   从下到上阅读每一行，说出所有重要的字符。
*   写至少一个自己设计的函数，然后用 10 种不同的方式运行它。

## 常见问题

**运行一个函数怎么可能有 10 种不同的方式？** 爱信不信，理论上讲，任何函数都有无数种调用方式。看看你对于函数、变量以及用户输入的创造力有多强。

**有没有什么方法能分析函数是如何运行的，以帮助我更好地理解它？**有很多方法，但是你先试试给每行加注释这种方式。其他方法包括大声把代码读出来，或者把代码打印出来然后在上面画图，来展示它是怎么运行的。

**如果我想问用户关于 cheese 和 crackers 的数字呢？**你需要用 `int()` 来把你通过 `input()` 获取的内容转化成数值。

**在函数中创建 `amount_of_cheese` 这个变量会改变 `cheese_count` 这个变量吗？** 不会的，这些变量是相互独立并存在于函数之外的。它们之后会传递给函数，而且是“暂时版”，只是为了让函数运行。当函数退出之后，这些暂时的变量就会消失，其他一切正常运行。接着往下学，你会慢慢明白的。

**像 `amount_of_cheese` 这样的全局变量（`global variables`）跟函数变量同名的话是不是不太好？**是的，如果这样的话，你就不知道你说的到底是哪个变量了。不过你有时候可能不得不用同样的名字，或者你可能不小心同名了，不管怎么样，尽量避免这种情况。

**一个函数里包含的参数有数量限制吗？**这取决于 Python 的版本以及你的电脑，但是这个数量其实相当大。实践中一个函数包含 5 个参数为宜，再多就比较难用了。

**你能在一个函数里面调用一个函数吗？**可以，在之后的练习里你会创建一个小游戏，到时候就会用到这个。``