# 练习 29 if 语句

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.34.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.34.learn-py3.md)

这个练习中的 Python 脚本将带你了解 if 语句。输入代码，准确运行，然后我们来看看你都学到了什么。

ex29.py

```py
1 people =  20
2 cats =  30
3 dogs =  15
4
5
6  if people < cats:
7  print("Too many cats! The world is doomed!")
8
9  if people > cats:
10  print("Not many cats! The world is saved!")
11
12  if people < dogs:
    13.  `13  print("The world is drooled on!")` 
14
15  if people > dogs:
16  print("The world is dry!")
17
18
19 dogs +=  5
20
21  if people >= dogs:
22  print("People are greater than or equal to dogs.")
23
24  if people <= dogs:
25  print("People are less than or equal to dogs.")
26
27
28  if people == dogs:
29  print("People are dogs.")
```

## 你会看到

练习 29 会话

```py
$ python3.6 ex29.py
2.  `Too many cats!  The world is doomed!` 3.  `The world is dry!`4.  `People are greater than or equal to dogs.`5.  `People are less than or equal to dogs.`6.  `People are dogs.`
```

## 附加练习

在附加练习中，试着猜猜 if 语句是什么以及它是干什么的。在继续进行下个练习之前，试着用自己的话回答以下这些问题，

*   你认为 if 对它下面的代码起什么作用？
*   为什么 if 下面的代码要缩进 4 个空格？
*   如果没有缩进会发生什么？
*   你能从练习 27 里面把一些布尔表达式放进 if 语句吗？试试看。
*   如果你改变 people，cats 和 dogs 的初始值会发生什么？

## 常见问题

**`+=` 是什么意思？** `x += 1` 就相当于 `x = x + 1` ，但是输入的内容更少。你可以把它叫做“累加”（increment by）运算符。之后你还会学到 `-=` 这样类似的表达。