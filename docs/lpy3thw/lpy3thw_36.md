# 练习 32 循环和列表

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.37.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.37.learn-py3.md)

你现在可以做一些更有意思的程序了。如果你一直跟着我们的节奏，你应该可以把所有学过的东西用 if 语句和布尔表达式结合起来，让你的程序做一些好玩的事情。

不过，程序仍然需要快速做一些重复的事情。我们要在这个练习中用一个 for-loop 来创建和打印各种列表。你在做练习的时候，得想想它们是什么。我不会立马告诉你，你得自己去想。

在你能够用一个 for-loop 之前，你需要一种方法来把这些循环的结果储存在某处。最好的办法就是用列表。列表顾名思义就是一个按顺序从头到尾组成的某种东西的容器。它并不复杂：你只需要学习一个新的语法。首先，你可以这样创建列表：

```py
1.  `hairs =  ['brown',  'blond',  'red']`2.  `eyes =  ['brown',  'blue',  'green'] weights =  [1,  2,  3,  4]`
```

以左方括号（ [ ）开始打开列表，然后把你想要的条目用逗号隔开放进去，有点类似于函数的参数。最后，用右方括号（ ] ）来表明列表的结束。Python 会选取这个列表以及它的所有内容并把它们分配到变量里。

| **警告！** |
| --- |
| 这块内容对于不会编程的人来说有点难理解，因为你的大脑一直以来都被训练成平面的了。还记得上个练习中你把 if 语句放在 if 语句中吗？这可能让你伤脑筋了，因为大多数人不理解如何在一个东西里面嵌套一个东西。在编程中，嵌套结构无处不在。你会看到一个函数调用其他包含 if 语句的函数，这个 if 语句中又有一个包含列表的列表。如果你看到一个类似的结构无法理解，拿出一根笔和一张纸，然后手动把它拆解开，直到你完全理解为止。 |

我们现在要用 for-loops 来创建一些列表，然后把它们打印出来。

ex32.py

```py
1.  1.  `1 the_count =  [1,  2,  3,  4,  5]`
    2.  `2 fruits =  ['apples',  'oranges',  'pears',  'apricots']`
    3.  `3 change =  [1,  'pennies',  2,  'dimes',  3,  'quarters']`
    4.  `4`
    5.  `5  # this first kind of for-loop goes through a list`
    6.  `6  for number in the_count:`
    7.  `7  print(f"This is count {number}")`
    8.  `8`
    9.  `9  # same as above`
    10.  `10  for fruit in fruits:`
    11.  `11  print(f"A fruit of type: {fruit}")`
    12.  `12`
    13.  `13  # also we can go through mixed lists too`
    14.  `14  # notice we have to use {} since we don't know what's in it`
    15.  `15  for i in change:`
    16.  `16  print(f"I got {i}")`
    17.  `17`
    18.  `18  # we can also build lists, first start with an empty one`
    19.  `19 elements =  []`
    20.  `20`
    21.  `21  # then use the range function to do 0 to 5 counts`
    22.  `22  for i in range(0,  6):`
    23.  `23  print(f"Adding {i} to the list.")`
    24.  `24  # append is a function that lists understand`
    25.  `25 elements.append(i)`
    26.  `26`
    27.  `27  # now we can print them out too`
    28.  `28  for i in elements:`
    29.  `29  print(f"Element was: {i}")`
```

## 你会看到

练习 32 会话

```py
1.  `$ python3.6 ex32.py`2.  `This  is count 1`3.  `This  is count 2`4.  `This  is count 3`5.  `This  is count 4`6.  `This  is count 5`7.  `A fruit of type: apples`8.  `A fruit of type: oranges`9.  `A fruit of type: pears`10.  `A fruit of type: apricots`11.  `I got 1`12.  `I got pennies`13.  `I got 2`14.  `I got dimes`15.  `I got 3`16.  `I got quarters`17.  `Adding  0 to the list.`18.  `Adding  1 to the list.` 19.  `Adding  2 to the list.`20.  `Adding  3 to the list.` 21.  `Adding  4 to the list.`22.  `Adding  5 to the list.` 23.  `Element was:  0`24.  `Element was:  1`25.  `Element was:  2`26.  `Element was:  3`27.  `Element was:  4`28.  `Element was:  5`
```

## 附加练习

*   看看你是如何使用 range 的。查阅上面的 range 函数并理解掌握。
*   你能在第 22 行不使用 for-loop，而是直接把 range(0, 6) 赋给 elements 吗？
*   找到 Python 文档关于列表的部分，然后读一读。看看除了 append，你还能对列表做哪些操作？

## 常见问题

**如何创建一个二维列表？**可以用这种列表中的列表：`[[1,2,3],[4,5,6]]`

**列表（lists）和数组（arrays）难道不是一个东西吗？**这取决于语言以及实现方法。在传统术语中，列表和数组的实现方式不同。在 Ruby 中都叫做 arrays，在 python 中都叫做 lists。所以我们就把这些叫做列表吧。

**为什么 `for-loop` 可以用一个没有被定义的变量？**变量在 `for-loop` 开始的时候就被定义了，它被初始化到了每一次 loop 迭代时的当前元素中。

**为什么 `range(1, 3)` 中的 i 只循环了两次而不是三次？** `range()` 函数只处理从第一个到最后一个数，但不包括最后一个数，所以它在 2 就结束了。这是这类循环的通用做法。

**`element.append()` 的作用是什么？**它只是把东西追加到列表的末尾。打开 Python shell 然后创建一个新列表。任何时候当你遇到类似的用法，试着多玩几次，去体会它们的作用。