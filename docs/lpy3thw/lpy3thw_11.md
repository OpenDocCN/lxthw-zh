# 练习 7 更多打印

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.12.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.12.learn-py3.md)

现在我们要做更多的练习，你只用输入代码让它运行即可。我不会做过多的解释，因为跟前面基本是一样的，目的是为了让你建立起自己的技能。千万别跳过，也别复制粘贴！

ex7.py

```py
1.  1.  `1  print("Mary had a little lamb.")`
    2.  `2  print("Its fleece was white as {}.".format('snow'))`
    3.  `3  print("And everywhere that Mary went.")`
    4.  `4  print("."  *  10)  # what'd that do?`
    5.  `5`
    6.  `6 end1 =  "C"`
    7.  `7 end2 =  "h"`
    8.  `8 end3 =  "e"`
    9.  `9 end4 =  "e"`
    10.  `10 end5 =  "s"`
    11.  `11 end6 =  "e"`
    12.  `12 end7 =  "B"`
    13.  `13 end8 =  "u"`
    14.  `14 end9 =  "r"`
    15.  `15 end10 =  "g"`
    16.  `16 end11 =  "e"`
    17.  `17 end12 =  "r"`
    18.  `18`
    19.  `19  # watch that comma at the end. try removing it to see what h`
    20.  `20  print(end1 + end2 + end3 + end4 + end5 + end6,  end=' ')`
    21.  `21  print(end7 + end8 + end9 + end10 + end11 + end12)`
```

## 你会看到

练习 7 会话

```py
1.  `$ python3.6 ex7.py`2.  `Mary had a little lamb.`3.  `Its fleece was white as snow.`4.  `And everywhere that Mary went.`6.  ``..........``7.  ``Cheese  Burger``
```

 `## 附加练习

接下来的附加练习基本也跟前面一样：

*   回过头复习一遍代码，在每一行上面添加注释。
*   倒着大声把每一行读出来，以发现你的错误。
*   从现在开始，当你犯错了，就在本子上写下你的错误。
*   当你学习下个练习之前，看看这些错误，以避免再犯。
*   记住每个人都会犯错。程序员就像音乐家一样总让别人觉得他们很完美，从不犯错，但其实他们经常犯错。

## 把代码打乱

在练习 6 中你还喜欢这种方式吗？从现在开始你要打乱你写的全部代码，或者你朋友的。我不会在每个练习中都写到这部分，你要自觉来做这件事。你的目标是找到很多不同的方式来打乱你的代码，知道你试遍了所有可能的方法。在一些练习里我可能会提到一种人们通常使用的打乱方法。除此之外，把它当成一项标准的任务来完成吧。

## 常见问题

**为什么你要用这个叫做 `'snow'` 的变量？**事实上那不是一个变量，它只是一个里面有 `snow` 这个单词的字符串，变量不会用单引号的。

**是不是写每一行代码都要加注释？** 不是，写注释只是为了向你自己解释一些难以理解的代码，或者你为什么要那样做。重要的是搞清楚为什么，然后你再试着写代码，让它实现一些事情。然而，有时候你不得不写一些让人讨厌的代码来解决一个问题，这个问题又需要你在每一行都写上注释，这时候你就应该严格地练练如何把代码用自然语言解释出来。

**单引号或者双引号都可以用来创建字符串吗？**在 Python 里面，两个都可以，不过严格来讲，像 `a` 或者 `snow` 这种比较短的字符串应该用单引号。`