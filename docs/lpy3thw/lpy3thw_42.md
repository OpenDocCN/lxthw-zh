# 练习 38\. 操作列表

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.43.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.43.learn-py3.md)

你已经学过了列表。在你学习“while 循环”的时候，你对列表进行过“追加(append)”操作——把数字追加到列表结尾并把它们打印了出来。另外你应该还在附加练习里研究过 Python 文档，看了列表支持的其他操作。不过距离之前的学习已经过去了一段时间，所以如果你不记得了的话，就回到本书的前面再复习一遍吧。

找到了吗？还记得吗？很好。那时候你对一个列表执行了 append 函数。不过，你也许还没有真正明白发生了什么，所以我们再来看看还可以对列表进行哪些操作。

当你看到像 `mystuff.append('hello')` 这样的代码时，你事实上已经在 Python 内部激发了一个连锁反应。以下是它的工作原理：

*   Python 看到你用到了 `mystuff`，于是就去找到这个变量。也许它需要倒着检查看你有没有在哪里用 `=` 创建过这个变量，或者检查它是不是一个函数参数，或者看它是不是一个全局变量。不管哪种方式，它得先找到 `mystuff` 这个变量才行。

*   一旦它找到了 `mystuff` ，就轮到处理句点 `.` (period) 这个操作符，而且开始查看 `mystuff` 内部的一些变量了。由于 `mystuff` 是一个列表，Python 知道 mystuff 支持一些函数。

*   接下来轮到处理 `append` 。Python 会将 `append` 和 `mystuff` 支持的所有函数的名称一一对比，如果确实其中有一个叫 `append` 的函数，那么 Python 就会去使用这个函数。

*   接下来 Python 看到了括号 `(`，并且意识到, “噢，原来这是一个函数”，到了这里，它就正常会调用这个函数了，不过这里的函数还要多一个参数才行。

*   这个额外的参数其实是…… `mystuff`! 你会觉得很奇怪对不对？不过这就是 Python 的工作原理，记住它就行了。所以到最后真正发生的事情其实是 `append(mystuff, 'hello')` ，不过你所看到的 `mystuff.append('hello')` 。

大部分时候你不需要知道这些细节，不过如果你看到如下的 Python 错误信息，上面的细节就对你有用了：

```py
$ python3.6
>>>  class  Thing(object):
...  def test(message):
...  print(message)
...
>>> a =  Thing()
>>> a.test("hello")
Traceback  (most recent call last):  File  "<stdin>", line 1  ,  in  <module>
TypeError  : test() takes exactly 1 argument (2 given)
>>>
```

这些是什么呢？这是我在 Python 命令行下展示给你的一点魔法。你还没有见过 `class`，不过后面很快就要碰到了。现在你看到 Python 说 `test()takes exactly 1 argument (2 given)` (`test()` 只可以接受 1 个参数，实际上给了 2 个)。它意味着 python 把 `a.test("hello")` 改成了 `test(a, "hello")`，而有人在某个地方弄错了，没有为 a 添加这个参数。

一下子要消化这么多可能有点难度，不过我们会做几个练习让你加深印象。下面的练习将字符串和列表混在一起，看看你能不能在里边找出点乐趣来

ex38.py

```py
1 ten_things =  "Apples Oranges Crows Telephone Light Sugar"
2
3  print("Wait there are not 10 things in that list. Let's fix it.")
4
5 stuff = ten_things.split(' ')
6 more_stuff =  ["Day",  "Night",  "Song",  "Frisbee",  "Corn",  "Banana",  "Girl",  "Boy"]
7
8  while len(stuff)  !=  10:
9 next_one = more_stuff.pop()
10  print("Adding: ", next_one)
11 stuff.append(next_one)
12  print(f"There are {len(stuff)} items now.")
13
14  print("There we go: ", stuff)
15
16  print("Let's do some things with stuff.")
17
18  print(stuff[1])
19  print(stuff[-1])  # whoa! fancy
20  print(stuff.pop())
21  print(' '.join(stuff))  # what? cool!
22  print('#'.join(stuff[3:5]))  # super stellar!
```

## 你会看到

```py
Wait there are not  10 things in that list.  Let's fix that. Adding:  Boy
There are 7 items now. Adding:  Girl
There are 8 items now. Adding:  Banana
There are 9 items now. Adding:  Corn
There are 10 items now.
There we go:    ['Apples', 'Oranges', 'Crows', 'Telephone', 'Light' 'Sugar', 'Boy', 'Girl', 'Banana', 'Corn']
Let's do some things with stuff.  Oranges
Corn  Corn
Apples  Oranges  Crows  Telephone  Light  Sugar  Boy  Girl  Banana  Telephone#Light
```

## 列表能做什么

假设你想基于“Go Fish”来创建一个计算机游戏，如果你不知道“Go Fish”是什么，可以花些时间去网上查查。要做这个游戏你必须要有“一副卡牌”（“deck of cards”）的概念，并且把它运用到你的 Python 程序里。然后你需要去写 Python 代码来实现这个想象中的卡牌游戏，并且让玩你游戏的人认为它是真的，即使它不是。你需要的是“一副牌”的思维框架，程序员们将此称之为一种“数据结构”。

什么是数据结构？如果你仔细想想，“数据结构”就是用一种正式的方式来组织一些数据（事实），就是这么简单。尽管一些数据结构会异常复杂，它们终归还是一种把事实（facts）存储在一个程序里的方式，你可以用不同的方式访问这些数据。数据结构使数据形成体系。

我会在下一个练习里深入讲解这一点，但是列表是程序员们使用最多的数据结构之一，**它们把你想要存储的内容以一种简单、有序的列表方式存储起来，并且可以通过索引（index）来随机（randomly）或线性（linearly）地获取到。**列表不会因为程序员解释说“列表就是列表”而比现实世界中已经存在的列表更复杂。让我们以一副卡牌为例来理解一下列表：

*   你有一副包含值（value）的卡牌。
*   这些卡牌被从上到下放成一摞。
*   你可以从上面取，从下面取，或者从中间随机抽取。
*   如果你想找到一张特定的卡牌，你就得把整副牌拿起来，一张一张翻找。让我们看看我刚才所说的定义:

**“一个有序列表”**，是的，一副卡牌是有序的，有第一张，有最后一张。

**“有你想要存储的东西”** 是的，卡牌就是我想要存储的东西。

**“可以随机获取”** 是的，我可以从这副卡牌里随机抽取一张。

**“或者线性获取”** 是的，如果我想找特定的一张卡牌，我可以从头开始按顺序找。

**“通过一个索引”** 基本上，你拿着一副牌，如果我让你取出第 19 张，你肯定得一张一张数到第 19。在我们的 Python 列表里，程序可以直接跳到任何你指定的索引。

以上就是一个列表所能做的所有事情。这些应该能够帮助你弄明白编程中的思想。编程中的每一种思想通常都与现实世界有着某种联系。至少那些有用的思想都是这样。如果你能弄明白它们在现实世界中的类似情形，你就能据此理解数据结构的作用。

## 何时使用列表

当你有能够匹配列表数据结构有用特性的东西时，你就可以使用列表：

*   如果你需要保持次序。记住，是列出的顺序，而不是分类的顺序，列表不会为你做分类工作。
*   如果你需要通过一个数字随机获取到内容。记住，是使用从 0 开始的基数。
*   如果你需要线性地遍历这些内容 (从头到尾)。记住，这就是 for 循环的作用。那么，你就可以使用列表。

## 附加练习

*   将每一个被调用的函数以前面提到的方式翻译成 Python 实际执行的动作。例如：`more_stuff.pop()` 其实是 `pop(more_stuff)`。
*   将这两种调用函数的方式翻译为自然语言。例如，`more_stuff.pop()` 可以翻译成“在 `more_stuff` 上调用 `pop`，而 `pop(more_stuff)` 是指“调用 `pop`，参数为 `more_stuff`”。想想它们为什么是同一件事情。
*   上网阅读一些关于“面向对象编程(Object Oriented Programming)”的资料。是不是有点困惑？我以前也是。别担心，后面还有更难的，慢慢学吧。
*   查一下 Python 中的 “class” 是什么东西。不要去看其他语言的 “class” 用法，会把你搞晕的。
*   如果你不知道我在说什么，别担心。程序员为了显得自己聪明，于是就发明了“面向对象编程”这种东西，简称为 OOP，然后他们就开始滥用这个东西。如果你觉得这东西太难，你可以先学一下 “函数编程(functional programming)”。
*   在现实世界中找 10 个可以适用于列表的东西。试着写一些脚本来操作一下。

## 常见问题

**你不是说不能用 while 循环吗？** 我是说过，所以你要记住，如果你有足够好的理由，你完全可以打破规则。只有傻瓜才会永远做规则的奴隶。

**为什么不能用 `join(' ', stuff)` ？** 用这种方式使用 join 是行不通的。join 是一种可以调用的方法，它能够把字符串放在列表的元素之间，把它们连接起来。你需要这样用它：`' '.join(stuff)`。

**你为什么要用 while 循环？** 你可以试试用 for 循环，看会不会容易点儿。

**`stuff[3:5]` 的作用是什么？** 它可以从 `stuff` 列表里抽取一个从元素 3 到元素 4 的切片。也就是它并不包含 5，有点类似于 `range(3,5)`。