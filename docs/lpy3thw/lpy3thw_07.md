# 练习 3 数字和数学

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.8.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.8.learn-py3.md)

每一种编程语言都得和数字、数学打交道。不用担心：程序员总是自诩为数学天才，其实事实并非如此。如果他们是数学天才，他们就会去研究数学，而不是去写那些 bug 连篇的网站框架以便能开上豪车。

这个练习包含了很多数学符号。让我们看看它们的名字，在你输入的时候，试着说出名字，直到你烂熟于心为止。以下是这些符号的名字：

• `+` plus，加号 • `-` minus，减号 • `/` slash，斜杠 • `*` asterisk，星号 • `%` percent，百分号 • `<` less-than，小于号 • `>` greater-than，大于号 • `<=` less-than-equal，小于等于号 • `>=` greater-than-equal，大于等于号

有没有注意到以上只是些符号，没有运算操作呢？写完下面的练习代码后，再回到上面的列表，弄明白每个符号的作用。例如 `+` 是用来做加法运算的。

ex3.py

```py
1  print("I will now count my chickens:")
2
3  print("Hens",  25  +  30  /  6)
4  print("Roosters",  100  -  25  *  3  %  4)
5
6  print("Now I will count the eggs:")
7
8  print(3  +  2  +  1  -  5  +  4  %  2  -  1  /  4  +  6)
9
10  print("Is it true that 3 + 2 < 5 - 7?")
11
12  print(3  +  2  <  5  -  7)
13
14  print("What is 3 + 2?",  3  +  2)
15  print("What is 5 - 7?",  5  -  7)
16
17  print("Oh, that's why it's False.")
18
19  print("How about some more.")
20
21  print("Is it greater?",  5  >  -2)
22  print("Is it greater or equal?",  5  >=  -2)
23  print("Is it less or equal?",  5  <=  -2)
```

确保你在运行它之前准确输入了每一行代码，和我的要求做一下对比检查。

## 你应该看到

练习 3 会话

```py
$ python3.6 ex3.py
I will now count my chickens:  Hens  30.0
Roosters  97
Now I will count the eggs:  6.75
Is it true that 3  +  2  <  5  -  7?  False
What  is  3  +  2?  5
What  is  5  -  7?  -2
Oh, that's why it's False.  How about some more.
Is it greater?  True
Is it greater or equal?  True
12.  ``Is it less or equal?  False``
```

 `## 课后练习

*   在每一行上面，用 `#` 写一句注释，向自己解释这行代码的作用。
*   还记得你在练习 0 中是如何启动 Python 3.6 的吗？再次启动它，把 Python 当成一个计算器来做一些数学运算。
*   找一些你需要计算的东西，然后写一个新的 `.py` 文件。
*   用浮点数重新写一下 `ex3.py`，让它更精确一些，比如 20.0 就是一个浮点数。

## 常见问题

**为什么 `%` 是一个模数，而不是百分比？** 这很可能只是设计者们选用的一个符号。在正常情况下你可以把它读作百分号，但是，在编程中 `%` 只是一个符号。

**`%` 是如何工作的？** 可以这样讲，x 除以 y 余 J。比如 100 除以 16 余 4，`%` 求的就是余数 J。

**运算顺序是怎样的？** 在美国我们遵循 PEMDAS 规则，即“括号，指数，乘，除，加，减（Parentheses Exponents Multiplication Division Addition Subtraction）。Python 也遵循这样的规则。很多人对 PEMDAS 规则存在误解，认为它们是严格按照先后次序来的，其实并不是，乘除是同时的，加减也是同时的，所以这个规则可能写成 `PE(M&D)(A&S)` 更合适。`