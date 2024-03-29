# 练习 10 那是什么？

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.15.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.15.learn-py3.md)

在练习 9 中我教了你一些新东西。这两天我们一直在学习字符串。我教了你两种创建多行字符串的方式，第一种是在月份中间加 `\n` ，它可以实现换行。

`\` 这个字符可以把没法输入的字符转化成字符串。有很多你可能会用到的“转义字符”（escape scequence），我们会在接下来的练习中学到一些，以便你理解我说的意思。

一个很重要的转义字符就是转义单引号或者双引号。比如你要在一个用双引号引起来的字符串中再加一对双引号，就像这样：`"I "understand" joe."`，python 就会懵掉，因为它会认为 understand 后面的双引号就代表这个字符串已经结束了。所以你需要用一种方式告诉 python 字符串里面的双引号并不是一个真正的双引号。

要解决这个问题，你得转义双引号和单引号，让 python 知道得把它们包含在字符串里。例如：

```py
"I am 6'2\" tall."  # escape double—quote inside string
'I am 6\'2" tall.'  # escape single—quote inside string
```

第二种方法是用三个双引号，即 `"""` ，这样就能像字符串一样运行，而且你可以多输入几行，最后再以 `"""` 结尾即可。我们来做个练习。

ex10.py

```py
1 tabby_cat =  "\tI'm tabbed in."
2 persian_cat =  "I'm split\non a line."
3 backslash_cat =  "I'm \\ a \\ cat."
4
5 fat_cat =  """
6   I'll do a list:
7   \t* Cat food
8   \t* Fishies
9   \t* Catnip\n\t* Grass
10  """
11
12  print(tabby_cat)
13  print(persian_cat)
14  print(backslash_cat)
15  print(fat_cat)
```

## 你会看到

找一找你输入的 `tab` 符号（即 `\t` ），在这个练习中空格很重要，别弄错了。

```py
$ python ex10 . py
I'm tabbed in.
I'm split
on a line.
I'm \ a \ cat .
I'll do a list:
*  Cat food
*  Fishies
*  Catnip
*  Grass

```

## 转义字符

这是 python 支持的所有的转义字符了。你可能用不到这么多，但是记住它们的格式以及用法。在一些字符串里试着用用它们，看看能不能成功运行。

## 附加练习

*   记住所有的转义字符。可以把它们添加到卡片上来记。
*   改用三个单引号（`'''`），你知道什么情况下用它而不是三个双引号（`"""`）吗？
*   把转义字符和格式字符串结合起来创建一个更复杂的字符串。

## 常见问题

**我还是没完全理解前面的练习，我该继续往下学吗？** 是的，继续学，别停在这儿。把你不明白的东西记在本子上，定期复习，等你做完更多的练习看你能不能理解。有时候你可能需要回过头去重新做做之前的练习才能明白。

**双反斜杠 `\` 和其他符号有什么区别？** 它只是为了让你能把单反斜杠 `\` 打印出来，想想你为什么要用 `\` 。

**我要是用 `//` 或者 `/n` 就不行。** 因为你用的是斜杠而不是反斜杠。它们是不同的符号，有着不同的作用。

**我不明白附加练习的第 3 题。你说的把转义字符和格式字符串结合起来是什么意思？** 我需要你理解一个概念，就是这些练习都可以结合起来解决问题。用你知道的关于格式字符串的东西和本练习学到的转义字符写一些新的代码。

**`'''` 和 `"""` 用哪个更好？** 这完全基于风格。现在先用 `'''` ，当你感觉用 `"""` 更好或者别人都用它的时候你可以用 `"""` 。`