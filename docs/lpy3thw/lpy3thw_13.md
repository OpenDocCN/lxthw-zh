# 练习 9 打印，打印，打印

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.14.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.14.learn-py3.md)

到现在为止，你应该意识到了这本书的模式，就是用很多练习来教你学习新东西。我先让你敲一些你可能不懂的代码，然后通过更多的练习来解释其中的概念。如果你现在有不懂的东西，在你完成更多练习之后你就会明白。先把你不懂的地方记下来，然后往下进行。

ex9.py

```py
1  # Here's some new strange stuff, remember type it exactly.
2
3 days =  "Mon Tue Wed Thu Fri Sat Sun"
4 months =  "Jan\nFeb\nMar\nApr\nMay\nJun\nJul\nAug"
5
6  print("Here are the days: ", days)
7  print("Here are the months: ", months)
8
9  print("""
10  There's something going on here.
11  With the three double-quotes.
12  We'll be able to type as much as we like.
13  Even 4 lines if we want, or 5, or 6.
14  """)
```

## 你会看到

练习 9 会话

```py
$ python3.6 ex9.py
Here are the days:  Mon  Tue  Wed  Thu  Fri  Sat  Sun
Here are the months:  Jan
Feb
Mar
Apr
May
Jun
Jul
Aug
There's something going on here.
With the three double-quotes.
We'll be able to type as much as we like.
Even  4 lines if we want,  or  5,  or  6.

```

## 附加练习

*   检查你的代码，把错误记下来，以避免再犯。
*   你有打乱你的代码然后重新修复吗？

## 常见问题

**为什么我在三个双引号之间加了空格就报错了呢？** 你必须这样输入 `"""` ，而不能这样输入 `" " "` ，也就是说中间不能加空格。

**如果我想让月份另起一行开始打印怎么办？** 你只需要在字符串前面加 `\n` 即可，就像这样：`"\nJan \nFeb \nMar \nApr \nMay \nJun \nJul \nAug"` 。

**如果我的错误总是拼写错误是不是很糟糕？** 很多编程初学者（甚至非初学者）都会犯拼写错误，不用担心，细心点就行。`