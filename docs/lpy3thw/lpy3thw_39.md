# 练习 35 分支和函数

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.40.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.40.learn-py3.md)

目前为止你已经了解了 if 语句，函数以及列表。现在是时候深入学习一下了。照例输入如下代码，看看你能否明白程序在做什么。

ex35.py

```py
1  from sys import  exit
2
3  def gold_room():
4  print("This room is full of gold. How much do you take?")
5
6 choice = input("> ")
7  if  "0"  in choice or  "1"  in choice:
8 how_much =  int(choice)
9  else:
10 dead("Man, learn to type a number.")
11
12  if how_much <  50:
13  print("Nice, you're not greedy, you win!")
14  exit(0)
15  else:
16 dead("You greedy bastard!")
17
18
19  def bear_room():
20  print("There is a bear here.")
21  print("The bear has a bunch of honey.")
22  print("The fat bear is in front of another door.")
23  print("How are you going to move the bear?")
24 bear_moved =  False
25
26  while  True:
27 choice = input("> ")
28
29  if choice ==  "take honey":
30 dead("The bear looks at you then slaps your face")
31  elif choice ==  "taunt bear"  and  not bear_moved:
32  print("The bear has moved from the door.")
33  print("You can go through it now.")
34 bear_moved =  True
35  elif choice ==  "taunt bear"  and bear_moved:
36 dead("The bear gets pissed off and chews your leg.")
37  elif choice ==  "open door"  and bear_moved:
38 gold_room()
39  else:
40  print("I got no idea what that means.")
41
42
43  def cthulhu_room():
44  print("Here you see the great evil Cthulhu.")
45  print("He, it, whatever stares at you and you go insane.")
46  print("Do you flee for your life or eat your head?")
47
48 choice = input("> ")
49
50  if  "flee"  in choice:
51 start()
52  elif  "head"  in choice:
53 dead("Well that was tasty!")
54  else:
55 cthulhu_room()
56
57
58  def dead(why):
59  print(why,  "Good job!")
60  exit(0)
61
62  def start():
63  print("You are in a dark room.")
64  print("There is a door to your right and left.")
65  print("Which one do you take?")
66
67 choice = input("> ")
68
69  if choice ==  "left":
70 bear_room()
71  elif choice ==  "right":
72 cthulhu_room()
73  else:
74 dead("You stumble around the room until you starve.")
75
76
77 start()
```

## 你会看到

以下是我玩这个游戏的结果：

练习 35 会话

```py
$ python3.6 ex35.py
You are in a dark room.
There  is a door to your right and left.  Which one do you take?
> left
There  is a bear here.
The bear has a bunch of honey.
The fat bear is  in front of another door.  How are you going to move the bear?
> taunt bear
The bear has moved from the door.  You can go through it now.
> open door
This room is full of gold.  How much do you take?
>  1000
You greedy bastard!  Good job!
```

## 附加练习

*   画一个这个游戏的流程图，并指出它是如何运转的。
*   修正你的错误，包括拼写和语法错误。
*   为你不理解的函数写上注释。
*   为游戏增加一些功能，同时使代码更加简化。
*   这个 gold_room 让你输入数字的方式有点奇怪。这样做有哪些 bug ？你能改善我的代码吗？可以查查看 int() 的相关知识。

## 常见问题

**救命! 这个程序是怎么工作的！？** 当你遇到不理解的代码时，不要着急，只要在每行代码下面写下注释，弄清楚这一行是做什么的，就很容易明白。确保你的注释和代码一样简洁。 然后要么画图，要么写一段话来描述代码是如何运行的。这样你就会理解其背后的原理。

**为什么你要用 `while True`？** 这样可以构建一个无限循环。

**`exit(0)` 是干什么用的？** 在很多操作系统中，一个程序可以用 `exit(0)` 来结束，其中传入的数字代表是否有错误。如果你用 `exit(1)` 代表有 1 个错误， `exit(0)` 则代表程序正常退出。它不同于通常的布尔逻辑（0==False），因为你可以用不同的数字来表示不同的错误结果。你可以用 `exit(100)` 来表示与 `exit(2)` 或者 `exit(1)` 不同的错误结果。

**为什么 `input()` 有时会被写成 `input('> ')`？** input 的参数是一个字符串，所以要在获取用户输入的内容前面加一个提示符。（ai 酱注：这里 `>` 也可以换成想要提示用户的文字。）