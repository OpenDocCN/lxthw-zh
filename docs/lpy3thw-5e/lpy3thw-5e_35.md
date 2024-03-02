## 练习 32：做决策

在这本书的前半部分，你主要只是打印出一些称为“函数”的东西，但一切基本上都是直线的。你的脚本从顶部开始运行，一直到底部结束。如果你创建了一个函数，你可以稍后运行该函数，但它仍然没有你真正需要做出决策的分支。现在你有了 `if`、`else` 和 `elif`，你可以开始编写决策性的脚本了。

在上一个脚本中，你列出了一组简单的测试，询问一些问题。在这个脚本中，你将询问用户问题，并根据他们的答案做出决定。编写这个脚本，然后多玩一下，弄清楚它的运行方式。

代码清单 32.1: ex32.py

```py
 1   print("""You enter a dark room with two doors.
 2   Do you go through door #1 or door #2?""")
 3
 4   door = **input(**"> ")
 5
 6   **if** door == "1":
 7       print("There's a giant bear here eating a cheese cake.")
 8       print("What do you do?")
 9       print("1\. Take the cake.")
10       print("2\. Scream at the bear.")
11
12       bear = **input(**"> ")
13
14       **if** bear == "1":
15           print("The bear eats your face off. Good job!")
16       **elif** bear == "2":
17           print("The bear eats your legs off. Good job!")
18       **else**:
19           print(f"Well, doing {bear} is probably better.")
20       print("Bear runs away.")
21
22   **elif** door == "2":
23       print("You stare into the endless abyss at Cthulhu's retina.")
24       print("1\. Blueberries.")
25       print("2\. Yellow jacket clothespins.")
26       print("3\. Understanding revolvers yelling melodies.")
27
28       insanity = **input(**"> ")
29
30       **if** insanity == "1" **or** insanity == "2":
31           print("Your body survives powered by a mind of jello.")
32           print("Good job!")
33       **else**:
34           print("The insanity rots your eyes into a pool of muck.")
35           print("Good job!")
36
37   **else**:
38       print("You stumble around and fall on a knife and die. Good job!")
```

这里的关键点是，现在你正在将`if-statements`放在`if-statements`内部作为可以运行的代码。这是非常强大的，可以用来创建“嵌套”决策，其中一个分支导致另一个分支。

确保你理解了`if`-statements 中嵌套`if`-statements 的概念。实际上，做一些练习来真正掌握它。

### 你应该看到的结果

这是我玩这个小冒险游戏的情况。我表现得不太好。

```py
1   You enter a dark room with two doors.
2   Do you go through door #1 or door #2?
3   > 1
4   There's a giant bear here eating a cheese cake.
5   What do you do?
6   1\. Take the cake.
7   2\. Scream at the bear.
8   > 2
9   The bear eats your legs off. Good job!
```

### `dis()` 它

这次没有 `*dis()*` *It* 部分，因为这段代码太复杂了，难以理解，但如果你感觉幸运的话，可以尝试一下：

```py
 1   from dis import dis
 2
 3   if door == "1":
 4       print("1")
 5       bear = input("> ")
 6       if bear == "1":
 7           print("bear 1")
 8       elif bear == "2":
 9           print("bear 2")
10       else:
11           print("bear 3")
```

这将产生大量需要分析的代码，但尽力而为。过一段时间会变得无聊，但也有助于理解 Python 的工作原理。再次强调，如果这让你困惑，可以先跳过，以后再尝试。

### 练习

1.  制作游戏的新部分，并改变人们可以做出的决定。在游戏变得荒谬之前尽可能扩展游戏。

2.  编写一个全新的游戏。也许你不喜欢这个，那就自己创造一个。这是你的电脑；做你想做的事情。

### 常见学生问题

**你能用一系列** `if-else` **组合替换** `elif` **吗？** 在某些情况下可以，但这取决于每个 `if/else` 的编写方式。这也意味着 Python 将检查*每个* `if-else` 组合，而不像 `if-elif-else` 那样只检查第一个为假的条件。尝试创建一些来了解差异。

**如何判断一个数字是否在一系列数字范围内？** 你有两个选择：使用 `0 < x` `< 10` 或 `1 <= x < 10`—这是经典的表示法—或使用 `x in range(1, 10)`。

**如果我想在** `if-elif-else` **块中增加更多选项怎么办？** 为每个可能的选择添加更多 `elif` 块。
