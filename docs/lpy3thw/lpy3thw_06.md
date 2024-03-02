# 练习 2 注释和井号

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.7.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.7.learn-py3.md)

注释在程序中非常重要，它们可以用自然语言告诉你某段代码的功能时什么，还能在你想要暂时移除某段代码时禁用程序的一部分。以下是如何在 Python 中使用注释：

ex2.py

```py
1  # A comment, this is so you can read your program later.
    2.  `2  # Anything after the # is ignored by python.` 
3
4  print("I could have code like this.")  # and the comment after 5
6  # You can also use a comment to "disable" or comment out code
    6.  `7  # print("This won't run.")` 
8
9  print("This will run.")
```

从现在开始，我都会这样写代码。你得明白不是所有的东西都得在字面上保持一致，你的屏幕和程序可能看起来跟我的不一样，但是只要你在编辑器里输入的文本一样就行。事实上，我用任何文本编辑器都可以输出同样的结果。

## 你应该看到

练习 2 会话

```py
1.  `$ python3.6 ex2.py`2.  `I could have code like this.  This will run.`
```

再说一次，我之后可能不会将所有的截图都贴出来，你得明白第一个 `$` 和最后一个 `$` 之间的内容才是你应该关注的。

## 课后练习

*   弄清楚 `#` 符号的作用，而且记住它的名字。(中文为井号，英文为 octothorpe 或者 pound character)。
*   打开你的 `ex2.py` 文件，从后往前逐行检查每个单词，与要求输入的内容进行对比。
*   有没有发现什么错误？有的话就改正过来.
*   读你写的习题，把每个字符都读出来。有没有发现更多错误？有的话改正过来。

## 常见问题

**为什么在 `print("Hi # there.")` 里 `#` 就没有被忽略？** 因为 `#` 在一个字符串里，计算机会打印引号之间字符串的所有内容， `#` 在字符串里被认为是一个字符，而不是注释符号。

**我如何把很多行变成注释？** 在每一行前面加一个 `#` 。

**为什么我要倒着检查代码？** 这是一个让你的大脑不专注于每行代码意思的小技巧，这样做能够让你更准确地检查出错误，可以说是一个很好用的纠错技巧了。