# 练习 13 参数，解包，变量

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.18.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.18.learn-py3.md)

在这个练习中我们将会再涉及一种 `input` 方法，你可以用这种方法把变量传给一个脚本（也就是你的 `.py` 文件）。你知道如何运行 `ex13.py` 吧？输入 `python3.6 ex13.py` 就行（Windows 下输入 `python ex13.py` ）。这句命令的 ex13.py 就叫做参数（argument）。我们现在要做的就是写一个也接受参数的脚本。

输入这个程序，然后我会详细解释：

ex13.py

```py
1  from sys import argv
2  # read the WYSS section for how to run this
3 script, first, second, third = argv
4
5  print("The script is called:", script)
6  print("Your first variable is:", first)
7  print("Your second variable is:", second)
8  print("Your third variable is:", third)
```

第一行我们进行了 “import”（导入），这能让你把 Python 功能库中的功能（features）添加到你的脚本中。Python 会问你你想用什么，而不是一次把所有的功能都给你。它会让你的程序很小，但是它同时也可以为其它阅读你代码的程序员提供参考。

这个 `argv` 是 “argument variable” ，一个在编程语言中非常标准的名字，你会在其它很多的语言中看到它的使用。当你运行 Python 脚本的时候，这个变量（variable）保存了你传给 Python 脚本的参数（argument）。在这个练习中，你会做更多相关的练习，看看会发生什么。

第三行“解包”（unpacks）了 `argv` ，而不是保留所有的参数，它分成了四个变量：`script`, `first`, `second`, 以及 `third` 。这可能看起来很奇怪，但是“解包”这个词可能是对这个操作的最好定义，就好像在说：“把 argv 里面的东西解包，然后按顺序分配给从左到右每一个变量。最后就像平常一样把它们打印出来即可。

## 等等！Features 还有另一个名字

我在这儿把它们叫做 features （就是你导入进来让 python 做更多事情的东西），但是很少有人叫它们 features。我用这个名字只是因为我想让你在专业术语之外思考它们的真正含义。不过在你继续学习之前，你需要知道它们真正的名字：modules （模块）。

从现在开始我们会把这些 features 说成导入模块，比如，“你想导入 `sys` 模块”。 它们还被有些程序员叫做“libraries”（库），但是我们就用模块这个名字吧。

## 你会看到

| 警告！ |
| --- |
| 注意！你之前一直直接运行 python 脚本，不用输入命令行参数。如果你只输入 `python3.6 ex13.py` 你就错了！注意看我是怎么操作的，这在任何有 `argv` 的地方都会用到。 |

像这样运行这个程序，前面是你要传递的命令行参数：

练习 13 会话

```py
$ python3.6 ex13.py first 2nd  3rd
The script is called: ex13.py
Your first variable is: first
Your second variable is:  2nd
Your third variable is:  3rd
```

当你做一些不同参数的运行时，你会看到：

练习 13 会话

```py
$ python3.6 ex13.py stuff things that
 The script is called: ex13.py
Your first variable is: stuff
Your second variable is: things
Your third variable is: that
$
$ python3.6 ex13.py apple orange  grapefruit
The script is called: ex13.py
Your first variable is: apple
Your second variable is: orange
Your third variable is: grapefruit

```

事实上你还可以把 `first`，`2nd`，`3rd` 替换成任何你想替换的东西。如果你没有正确运行，你会收到这样的报错：

练习 13 会话

```py
$ python3.6 ex13.py first 2nd
 Traceback  (most recent call last):
File  "ex13.py", line 3,  in  <module>
 script, first, second, third = argv
ValueError:  not enough values to unpack (expected 4, got 3)

```

这种情况一般是当你运行脚本的时候没有在命令行放足够的变量（在本例中只有 `first` 、`2nd` ）。注意当我运行的时候只给出 `first` 、`2nd` ，就会出现错误说“需要三个以上的值来解包”，这就是告诉你，你没有给到足够多的参数。”

## 附加练习

*   试着给你的脚本三个以内的参数，看看你会收到什么样的报错，你是否能解释它。
*   写一个参数少的脚本和一个参数多的脚本，给未解包的变量起个合适的名字。
*   把 `input` 和 `argv` 结合起来创建一个脚本，从用户那里获取更多 `input` 。别想得太难，就用 `argv` 来获取一些东西，再用 `input` 从用户那里获取一些东西。
*   记住模块给我们一些特征，记住它叫模块（modules），我们之后会用到。

## 常见问题

**当我运行的时候我收到了 `ValueError: need more than 1 value to unpack.`**还记得我说过，学习编程的一项重要技能就是注意细节。如果你看了“你会看到”那部分，你就会看到我是如何在命令行上运行有参数的脚本的，你应该准确按照我做的来。

**`argv` 和 `input()` 之间的区别是什么？** 区别取决于用户在哪被要求输入，如果是在命令行，就用 argv。如果你想让它们在程序已经运行的情况下用键盘输入，那就用 `input()` 。

**命令行参数是字符串吗？**是的，它们是以字符串的形式进来的，即使你在命令行输入的是数字。你可以用 `int()` 把它们转化成数值，就像 `int(input())` 。

**你如何使用用命令行？”** 你应该已经学过命令行的使用了，现在应该用得很 6 了。但是如果你还没有学，先去附录 A 学习命令行速成课程。

**我不知道怎么把 `argv` 和 `input()` 结合在一起。** 别把它想得太难。就在脚本最后加两行，用 `input()` 获取一些东西，再打印出来。然后试着用更多方式在同一个脚本中使用这两样东西。

**为什么我不能这样用：`input('? ') = x` ?** 因为它写反了，按我的要求写，就能运行。