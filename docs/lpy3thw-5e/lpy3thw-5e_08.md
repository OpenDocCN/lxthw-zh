## 练习 6：字符串和文本

虽然你一直在写字符串，但你仍然不知道它们是做什么的。在这个练习中，我们创建了一堆带有复杂字符串的变量，这样你就可以看到它们的用途。首先解释一下字符串。

一个字符串通常是你想要向某人显示或从你正在编写的程序“导出”的一小段文本。当你在文本周围放置`"`（双引号）或`'`（单引号）时，Python 知道你想要的是一个字符串。当你在`print`中放置你想要放入字符串中的文本时，你会看到这种情况发生了很多次，放在`print`后面的`"`或`'`中打印字符串。

字符串可以包含在你的 Python 脚本中的任意数量的变量。记住，变量是你设置一个名字`=`（等于）一个值的任何代码行。在这个练习的代码中，`types_of_people = 10`创建了一个名为`types_of_people`的变量，并将其设置为`=`（等于）`10`。你可以将它放在任何带有`{types_of_people}`的字符串中。你还会看到我必须使用一种特殊类型的字符串来“格式化”；它被称为“f-string”，看起来像这样：

```py
f"some stuff here {avariable}"
f"some other stuff {anothervar}"
```

Python *还*有另一种使用`.format()`语法的格式化方式，你可以在第 17 行看到。有时候当我想对已经创建的字符串应用格式时，你会看到我使用它。我们稍后会更详细地讨论这个。

现在我们将输入一大堆字符串、变量和格式，并打印它们。你还将练习使用简短的缩写变量名。程序员喜欢通过使用令人讨厌的短小和神秘的变量名来节省时间，所以让我们从早期开始阅读和编写它们。

清单 6.1：ex6.py

```py
 1   types_of_people = 10
 2   x = f"There are {types_of_people} types of people."
 3
 4   binary = "binary"
 5   do_not = "don't"
 6   y = f"Those who know {binary} and those who {do_not}."
 7
 8   print(x)
 9   print(y)
10
11   print(f"I said: {x}")
12   print(f"I also said: '{y}'")
13
14   hilarious = False
15   joke_evaluation = "Isn't that joke so funny?! {}"
16
17   print(joke_evaluation.**format**(hilarious))
18
19   w = "This is the left side of..."
20   e = "a string with a right side."
21
22   print(w + e)
```

### 你应该看到的内容

```py
1   There are 10 types of people.
2   Those who know binary and those who don't.
3   I said: There are 10 types of people.
4   I also said: 'Those who know binary and those who don't.'
5   Isn't that joke so funny?! False
6   This is the left side of...a string with a right side.
```

### 学习扩展

1.  浏览这个程序，并在每行上面写一个注释，解释它。

2.  找出所有将字符串放在另一个字符串中的地方。

3.  你确定只有四个地方吗？你怎么知道？也许我喜欢说谎。

4.  解释为什么使用`+`将两个字符串`w`和`e`相加会得到一个更长的字符串。

### 破解它

现在你已经到了一个可以尝试破坏你的代码以查看结果的阶段。把这看作是一个游戏，想出最聪明的方法来破坏代码。你也可以找到最简单的方法来破坏它。一旦你破坏了代码，你就需要修复它。如果你有一个朋友，那么你们两个可以尝试破坏对方的代码并修复它。把你的代码给你的朋友，保存在一个名为`ex6.py`的文件中，这样他们就可以破坏一些东西。然后你尝试找到他们的错误并修复它。玩得开心，并记住，如果你写过这段代码一次，你可以再次做到。如果你把损坏搞得太严重，你总是可以再次输入以进行额外练习。

### 常见学生问题

**为什么**你会在一些字符串周围加上`'`（单引号），而在另一些字符串周围不加呢？大多数情况下是出于风格考虑，但我会在双引号内部使用单引号。看看第 6 行和第 15 行，看看我是如何做到这一点的。

**如果你觉得这个笑话很有趣，你能写下** `hilarious = True`**吗？** 是的，你以后会更多地了解这些布尔值。
