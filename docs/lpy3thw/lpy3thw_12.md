# 练习 8 打印，打印

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.13.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.13.learn-py3.md)

接下来我们要学习如何做更复杂的格式字符串。虽然它看起来很复杂，但是如果你认真做注释，并且好好做 break down 练习（就是打乱代码再修复）的话，你一定能理解的。

ex8.py

```py
1.  1.  `1 formatter =  "{} {} {} {}"`
    2.  `2`
    3.  `3  print(formatter.format(1,  2,  3,  4))`
    4.  `4  print(formatter.format("one",  "two",  "three",  "four"))`
    5.  `5  print(formatter.format(True,  False,  False,  True))`
    6.  `6  print(formatter.format(formatter, formatter, formatter, formatter))`
    7.  `7  print(formatter.format(`
    8.  `8  "Try your",`
    9.  `9  "Own text here",`
    10.  `10  "Maybe a poem",`
    11.  `11  "Or a song about fear"`
    12.  `12  ))`
```

## 你会看到

练习 8 会话

```py
1.  `$ python3.6 ex8.py`2.  `1  2  3  4`3.  `one two three four`4.  `True  False  False  True`5.  `{}  {}  {}  {}  {}  {}  {}  {}  {}  {}  {}  {}  {}  {}  {}  {}`6.  `Try your Own text here`7.  `Maybe a poem` 8.  `Or a song about fear`
```

在这个练习中我用了一个“函数”（function）来把 `formatter` 变量变成其他字符串。当你看到我写 `formatter.format(…)` 时，我就是在告诉 Python 做如下的事情：

*   在第一行定义 `formatter` 字符串。
*   调用 `format` 函数，类似于让它来做一个名为 `format` 的命令行命令。
*   把 4 个参数传给 `format` ，分别对应 `formatter` 变量中的 4 个 `{}` ，就像把参数传给命令行命令 `format` 一样。
*   为 `formatter` 变量调用 `format` 函数的结果就是，一个新的字符串会用四个变量取代原来的 `{}` ，然后再被打印出来。对于第 8 个练习来说，这样的信息量好像有点大，所以我希望你把它当成一道智力题。如果你真的不懂也没关系，因为这本书后面的内容会慢慢为你讲清楚。不过现在，试着学一学，看看会发生什么，然后再进行下面的练习。

## 加分练习

*   检查你写的代码，把错误记下来，然后做下一个练习之前看一看，避免再犯同样的错误。

## 常见问题

**为什么 `one` 要用引号，而 `True` 或者 `False` 却不用？** Python 把 `True` 和 `False` 当成代表“对“和”错“的关键词。如果你给它们加引号，它们就会变成字符串而无法工作。你会在练习 27 中学到相关内容。

**我能用 IDLE 来运行代码吗？** 不，你得学着用命令行。它对学习编程非常重要，并且是一个很好的起点。当你继续往下学这本书，你就会发现 IDLE 不管用了。