# 练习 31 做决定

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.36.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.36.learn-py3.md)

在这本书的前半部分你主要学习了调用函数、打印东西，但是这些基本都是直线运行下来的。你的脚本从上面开始运行，然后到底部结束。如果你用了一个函数，你可以随后再运行它，但是仍然不会有分叉需要你做决定的情况。现在你学习了 if，else，以及 elif，你就可以让脚本来做决定了。

在上个脚本中你写出了一个简单的问问题的测试集。在这个练习中你将问用户一些问题，并基于他们的回答做决定。写下这个脚本，然后多玩几遍，把它弄明白。

ex31.py

```py
1.  1.  `1  print("""You enter a dark room with two doors.`
    2.  `2   Do you go through door #1 or door #2?""")`
    3.  `3`
    4.  `4 door = input("> ")`
    5.  `5`
    6.  `6  if door ==  "1":`
    7.  `7  print("There's a giant bear here eating a cheese cake.")`
    8.  `8  print("What do you do?")`
    9.  `9  print("1\. Take the cake.")`
    10.  `10  print("2\. Scream at the bear.")` 
    11.  `11`
    12.  `12 bear = input("> ")`
    13.  `13`
    14.  `14  if bear ==  "1":`
    15.  `15  print("The bear eats your face off. Good job!")`
    16.  `16  elif bear ==  "2":`
    17.  `17  print("The bear eats your legs off. Good job!")`
    18.  `18  else:`
    19.  `19  print(f"Well, doing {bear} is probably better.")`
    20.  `20  print("Bear runs away.")`
    21.  `21`
    22.  `22  elif door ==  "2":`
    23.  `23  print("You stare into the endless abyss at Cthulhu's retina.")`
    24.  `24  print("1\. Blueberries.")`
    25.  `25  print("2\. Yellow jacket clothespins.")`
    26.  `26  print("3\. Understanding revolvers yelling melodies.")`
    27.  `27`
    28.  `28 insanity = input("> ")`
    29.  `29`
    30.  `30  if insanity ==  "1"  or insanity ==  "2":`
    31.  `31  print("Your body survives powered by a mind of jello.")`
    32.  `32  print("Good job!")`
    33.  `33  else:`
    34.  `34  print("The insanity rots your eyes into a pool of muck.")`
    35.  `35  print("Good job!")`
    36.  `36`
    37.  `37  else:`
    38.  `38  print("You stumble around and fall on a knife and die. Good job!")`
```

这里很关键的一点是你现在在 if 语句里面又放了一个 if 语句。这在创建“嵌套”（nested）决定的时候非常有用，每一个分支指向另一个选择。

确保你理解了在 if 语句中嵌套 if 语句的理念。你可以通过做附加练习来真正掌握它。

## 你会看到

这是我玩这个冒险小游戏的结果，我可能玩儿得没那么好。

练习 31 会话

```py
1.  `$ python3.6 ex31.py`2.  `You enter a dark room with two doors.` 3.  `Do you go through door #1 or door #2?`4.  `>  1`5.  `There's a giant bear here eating a cheese cake.`6.  `What do you do?`7.  `1\.  Take the cake.`8.  `2\.  Scream at the bear.`9.  `>   2`10.  `The bear eats your legs off. Good job!`
```

## 附加练习

*   给这个游戏加一些新内容，同时改变用户可以做的决定。尽可能地扩展这个游戏，直到它变得很搞笑。
*   写一个完全不同的新游戏。可能你不喜欢我的这个，你可以做一个你自己的。

## 常见问题

**我能用一系列的 if 语句来代替 elif 吗？**在某些情况下可以，但是取决于每个 if/else 是怎么写的。如果这样的话还意味着 Python 将会检查每一个 if-else 组合，而不是像 if-elif-else 组合那样只会检查第一个是 false 的。你可以多试几次，感受一下区别。

**我如何表示一个数字的区间？**有两种方式：一种是 0 < x < 10 或者 1 <= x < 10 这种传统表示方法，另一种是 x 的区间是 (1, 10)。

**如果我想在 if-elif-else 代码块中放更多的选择怎么办？**为每种可能的选择增加更多的 elif 块。