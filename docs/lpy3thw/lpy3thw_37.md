# 练习 33 While 循环

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.38.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.38.learn-py3.md)

现在我们来看一个新的循环： while-loop。只要一个布尔表达式是 True，while-loop 就会一直执行它下面的代码块。

等等，你应该能理解这些术语吧？如果我们写一行以 : 结尾的代码，它就会告诉 Python 开始一个新的代码块。我们用这种方式来结构化你的程序，以便 Python 明白你的意图。如果你还没有掌握这块内容，先回去复习一下，再做一些 if 语句、函数以及 for-loop，直到你掌握为止。

之后我们会做一些练习来训练你的大脑读取这些结构，就像我们训练你掌握布尔表达式一样。

回到 while-loop，它所做的只是像 if 语句一样的测试，但是它不是只运行一次代码块，而是在 while 是对的地方回到顶部再重复，直到表达式为 False。

但是 while-loop 有个问题：有时候它们停不下来。如果你的目的是让程序一直运行直到宇宙的终结，那这样的确很屌。但大多数情况下，你肯定是需要你的循环最终能停下来的。

为了避免这些问题，你得遵守一些规则：

*   保守使用 while-loop，通常用 for-loop 更好一些。
*   检查一下你的 while 语句，确保布尔测试最终会在某个点结果为 False。
*   当遇到问题的时候，把你的 while-loop 开头和结尾的测试变量打印出来，看看它们在做什么。在这个练习中，你要通过以下三个检查来学习 while-loop：

ex33.py

```py
1 i =  0
2 numbers =  []
3
4  while i <  6:
5  print(f"At the top i is {i}")
6 numbers.append(i)
7
8 i = i +  1
9  print("Numbers now: ", numbers)
10  print(f"At the bottom i is {i}")
11
12
13  print("The numbers: ")
14
15  for num in numbers:
16  print(num)
```

## 你会看到

练习 33 会话

```py
$ python3.6 ex33.py
2.  `At the top i is  0` 3.  `Numbers now:  [0]`4.  `At the bottom i is  1`5.  `At the top i is  1` 6.  `Numbers now:  [0,  1]`7.  `At the bottom i is  2`8.  `At the top i is  2`9.  `Numbers now:  [0,  1,  2]`10.  `At the bottom i is  3`11.  `At the top i is  3`12.  `Numbers now:  [0,  1,  2,  3]`13.  `At the bottom i is  4`14.  `At the top i is  4`15.  `Numbers now:  [0,  1,  2,  3,  4]`16.  `At the bottom i is  5`17.  `At the top i is  5`18.  `Numbers now:  [0,  1,  2,  3,  4,  5]`19.  `At the bottom i is  6`20.  `The numbers:`21.  `0`22.  `1`23.  `2`24.  `3`25.  `4`26.  `5`
```

## 附加练习

*   把这个 while-loop 转换成一个你可以调用的函数，然后用一个变量替代 i < 6 里面的 6。
*   用这个函数重新写一下这个脚本，试试不同的数值。
*   再增加一个变量给这个函数的参数，然后改变第 8 行的 +1，让它增加的值与之前不同。
*   用这个函数重新写这个脚本，看看会产生什么样的效果。
*   用 for-loop 和 range 写这个脚本。你还需要中间的增加值吗？如果不去掉这个增加值会发生什么？任何时候你在运行程序的时候它失控了，只用按下 `CTRL-C` ，程序就会终止。

## 常见问题

**for-loop 和 while-loop 的区别是什么？** for-loop 只能迭代（循环）一些东西的集合，而 while-loop 能够迭代（循环）任何类型的东西。不过，while-loop 很难用对，而你通常能够用 for-loop 完成很多事情。

**循环好难，我应该如何理解它们？**人们不理解循环的主要原因是他们跟不上代码的运行。当一个循环运行的时候，它会过一遍代码块，到结尾之后再跳到顶部。为了直观表现这个过程，你可以用 print 打印出循环的整个过程，把 print 行写在循环的前面、顶部、中间、结尾。研究一下输出的内容，试着理解它是如何运行的。