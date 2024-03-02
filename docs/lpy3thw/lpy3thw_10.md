# 练习 6 字符串和文本

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.11.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.11.learn-py3.md)

你已经写过字符串了，但你还是不知道它们是用来干嘛的。在这个练习中，我们会创建一些包含复杂字符串的变量，让你看看它们的作用。首先解释一下字符串的含义。

字符串通常是一些你想要让你的程序呈现给别人或者”输出“出来的文本信息。当你把双引号或者单引号括在一段本文外面时，Python 就会知道你想要把这些文本变成字符串。你在学习 print 的时候应该多次看到这种用法了，当你想要打印一些文本的时候，你就把这些文本放在双引号或者单引号里面。

字符串可以包含你的 Python 脚本中任意数量的变量。记住，变量就是让名字 = 一个值的那行代码。在本练习的代码中，`types_of_people = 10` 创建了一个名称为 `types_of_people`，值为 10 的变量。你可以用 `{types_of_people}` 的形式把这个变量放到任意字符串中。你还会看到我用了格式字符串（f-string），就像这样：

```py
1.  `f"some stuff here { avariable }"`2.  `f"some other stuff { anothervar }"`
```

Python 还有其他种类的格式，就像你在第 17 行看到的 `.format()` 语法。你还会看到当我想对一个已经创建的字符串应用一种格式的时候，我就会这样用，比如在一个循环里，我们会在后面的内容中涉及到。

我们现在要输入一整段字符串、变量和格式，然后把它们打印出来。你还会练习使用缩写作为变量名。程序员都喜欢使用简短的缩写来节省时间，但是那些缩写在你看来会十分晦涩难懂。所以我们得尽早开始学习阅读和书写这些东西。

ex6.py

```py
1.  1.  `1 types_of_people =  10`
    2.  `2 x = f"There are {types_of_people} types of people."`
    3.  `3`
    4.  `4 binary =  "binary"`
    5.  `5 do_not =  "don't"`
    6.  `6 y = f"Those who know {binary} and those who {do_not}."`
    7.  `7`
    8.  `8  print(x)`
    9.  `9  print(y)`
    10.  `10`
    11.  `11  print(f"I said: {x}")`
    12.  `12  print(f"I also said: '{y}'")`
    13.  `13`
    14.  `14 hilarious =  False`
    15.  `15 joke_evaluation =  "Isn't that joke so funny?! {}"`
    16.  `16`
    17.  `17  print(joke_evaluation.format(hilarious))`
    18.  `18`
    19.  `19 w =  "This is the left side of..."`
    20.  `20 e =  "a string with a right side."`
    21.  `21`
    22.  `22  print(w + e)`
```

## 你会看到

练习 6 会话

```py
1.  `$ python3.6 ex6.py`2.  `There are 10 types of people.`3.  `Those who know binary and those who don't.`4.  `I said: There are 10 types of people.`5.  `I also said: 'Those who know binary and those who don't.'`6.  `Isn't that joke so funny?! False`7.  `This is the left side of...a string with a right side.`
```

## 附加练习

*   复习一遍这个程序，并在每一行上面写上注释来解释它。
*   找到所有把字符串放在字符串里面的地方，一共有 4 处。
*   你确定有 4 处吗？你怎么知道？也许我爱撒谎呢。
*   解释一下为什么把 `w` 和 `e` 两个字符串用 `+` 连起来能够弄成一个更长的字符串。

## 把代码打乱

你现在已经可以把代码打乱了。把它当成一个游戏，用一种最聪明或者最简单的方式把代码打乱。打乱之后，你需要修复它们。如果你跟你的朋友一起学习，你们可以相互打乱对方的代码，然后再试着修复它。把你的 `ex6.py` 发给你的朋友，让他们打乱，然后你再试着找出它们的错误，并修复它。记住，如果你已经写了一遍这些代码了，你可以再写一次。如果你打乱得太彻底了，就试着重新写一遍。

## 常见问题

**为什么你在一些字符串外面放的是单引号，而其他的不是？**大多数是因为格式。但是如果一个字符串已经用了双引号，我就会在这个字符串里面用单引号，看看第 6 行和第 15 行你就知道了。

**如果你觉得一个笑话很好笑，可以写 `hilarious = True` 吗？** 可以的，你会在练习 27 中学习到这些布尔值。