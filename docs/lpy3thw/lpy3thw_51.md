# 练习 47\. 自动化测试

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.52.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.52.learn-py3.md)

为了确认游戏功能是否正常，你需要一遍一遍地在你的游戏中输入命令。这个过程非常枯燥。如果能写一小段代码来测试你的代码岂不是更好？一旦你对程序做了任何修改，或者添加了什么新东西，你只要“跑一下你的测试”，这些测试就能确保程序依然能正常运行。这些自动测试不会捕捉到所有 bug，但是可以让你无需重复输入命令来运行你的代码，从而为你节约很多时间。

从这一节开始，以后每个练习将不再有“你会看到”这一部分，取而代之的是“你应该测试”（What You Should Test）部分。从现在开始，你需要为自己写的所有代码写自动化测试，这会让你成为一个更好的程序员。

我不会试图解释为什么你需要写自动化测试。我要告诉你的是，你想要成为一个程序员，而程序的作用是让无聊冗繁的工作自动化，测试软件毫无疑问是无聊冗繁的，所以你还是写点代码让它为你来做测试工作比较好好。

这应该是你需要的所有的解释了。因为你写单元测试的原因是让你的大脑更加强健。你读了这本书，写了很多代码让它们实现一些事情。现在你将更进一步，写出能读懂你写的其他代码的代码。这个写代码来测试你写的其他代码的过程将强迫你清楚地理解你之前写的代码。同时清晰地了解这些代码实现的功能及其原理，从而让你对细节的注意更上一个台阶。

## 写一个测试用例（test case）

我们会拿一段非常简单的代码为例，写一个简单的测试，这个测试将建立在上节我们创建的项目骨架上面。

首先，从你的项目骨架创建一个叫做 ex47 的项目。以下是你要遵循的步骤，我会通过语言描述来告诉你，而不是直接给你代码，这样可以给你思考的机会：

*   把项目骨架复制到 ex47。

*   把所有的 NAME 文件重命名为 ex47。

*   把所有文件中的 NAME 单词替换为 ex47。

*   最后，删除所有 `*.pyc` 文件来确保你的文件夹是干净的。

如果你卡住了，可以回去查阅练习 46，如果没办法完成这些步骤，那你可能需要多练习几次。

**警告！**

记住，你通过运行 `nosetests` 命令来运行测试。你可以直接输入 `python3.6 ex47_tests.py` 来运行，但是没那么容易跑通，而且你需要为每个测试文件执行一次这个命令。

接下来，创建一个简单的文件 ex47/game.py ，你可以把代码放入其中进行测试。这是一个非常小的类，其代码如下：

game.py

```py
1.  1.  `1  class  Room(object):`
    2.  `2`
    3.  `3  def __init__(self, name, description):`
    4.  `4  self.name = name`
    5.  `5  self.description = description`
    6.  `6  self.paths =  {}`
    7.  `7`
    8.  `8  def go(self, direction):`
    9.  `9  return  self.paths.get(direction,  None)`
    10.  `10`
    11.  `11  def add_paths(self, paths):`
    12.  `12  self.paths.update(paths)`
```

一旦你有了这个文件，把单元测试骨架改成这样：

ex47_tests.py

```py
1.  1.  `1  from nose.tools import  *`
    2.  `2  from ex47.game import  Room`
    3.  `3`
    4.  `4`
    5.  `5  def test_room():`
    6.  `6 gold =  Room("GoldRoom",`
    7.  `7  """This room has gold in it you can grab. There's a`
    8.  `8                   door to the north.""")`
    9.  `9 assert_equal(gold.name,  "GoldRoom")`
    10.  `10 assert_equal(gold.paths,  {})`
    11.  `11`
    12.  `12  def test_room_paths():`
    13.  `13 center =  Room("Center",  "Test room in the center.")`
    14.  `14 north =  Room("North",  "Test room in the north.")`
    15.  `15 south =  Room("South",  "Test room in the south.")`
    16.  `16`
    17.  `17 center.add_paths({'north': north,  'south': south})`
    18.  `18 assert_equal(center.go('north'), north)`
    19.  `19 assert_equal(center.go('south'), south)`
    20.  `20`
    21.  `21  def test_map():`
    22.  `22 start =  Room("Start",  "You can go west and down a hole."`
    23.  `23 west =  Room("Trees",  "There are trees here, you can go east.")`
    24.  `24 down =  Room("Dungeon",  "It's dark down here, you can go up.")`
    25.  `25`
    26.  `26 start.add_paths({'west': west,  'down': down})`
    27.  `27 west.add_paths({'east': start})`
    28.  `28 down.add_paths({'up': start})`
    29.  `29`
    30.  `30 assert_equal(start.go('west'), west)`
    31.  `31 assert_equal(start.go('west').go('east'), start)`
    32.  `32 assert_equal(start.go('down').go('up'), start)`
```

这个文件引入了你在 ex47.game 模块中的 Room 类，这样你就能在这上面进行测试。然后是一系列以 `test_` 开头的函数来进行的测试。在每一个测试用例中都有一小段代码，它们会创建一个或多个房间，然后去确认房间的功能和你期望的是否一样。它先测试了基本的房间功能，然后测试了路径，最后测试了整个地图。

这里最重要的函数是 `assert_equal` ，它保证了你设置的变量，以及你在 Room 里设置的路径和你的期望相符。如果你得到错误的结果，`nosetests` 将会打印出一个错误信息，这样你就可以找到出错的地方并修正过来。

## 测试指南

在测试时，你可以照着下面这些不是很严格的指南来做：

*   测试脚本要放到 `tests/` 目录下，并且命名为 `BLAH_tests.py` ，否则 `nosetests` 就不会执行你的测试脚本了。这样做还有一个好处就是防止测试代码和别的代码互相混淆。 **ai 酱注：** 这里的 `BLAH_tests.py` 是一种调皮的写法（BLAH 是废话的意思），你应该把 `BLAH` 替换为你的 `NAME`，在这个练习中就是 `ex47`。

*   为你创建的每个模块写一个测试。

*   测试用例（函数）尽量保持简短，但如果看上去不怎么整齐也没关系，测试用例一般都有点乱。

*   就算测试用例有些乱，也要试着让他们保持整洁，把里边重复的代码删掉。创建一些辅助函数来避免重复的代码。当你下次在改完代码需要改测试的时候，你会感谢我这一条建议的。重复的代码会让修改测试变得很难操作。

*   最后一条是别太把测试当回事。有时候，更好的方法是把代码和测试全部删掉，然后重新设计代码。

## 你会看到

Exercise 47 会话

```py
1.  `$ nosetests`2.  `...`3.  `-----------------------------------------------------------------`4.  `Ran  3 tests in  0.008s OK`
```

如果一切正常的话你应该会看到这个。试着搞一个错误，看看输出结果是什么，然后再把代码修改正确。

## 附加练习

*   阅读 nosetests 相关文档，再去了解一下其他替代方案。

*   了解一下 Python 的 “doc tests”，看看你是不是更喜欢这种测试方式。

*   改进你游戏里的 Room，然后用它重建你的游戏，这次重写，你需要一边写代码，一边把单元测试写出来。

## 常见问题

**我运行 `nosetests` 的时候收到了一个语法错误（syntax error）** 如果你收到这样的提示，看一下错误提示是怎么说的，然后修改出错的哪一行或者之前的一行。像 `nosetests` 这样的工具是运行你的代码和测试代码，所以它们会在运行 Python 的同时发现语法错误。

**我为什么没办法引入 ex47.game ？** 确认你创建了 `ex47/**init**.py` 文件，回到练习 46 看看如何创建。如果问题不是出在这儿，那么你可以这样做： macOS/Linux 系统：

```py
1.  `export PYTHONPATH=.`
```

Windows 系统：

```py
1.  `$env :PYTHONPATH =  "$env :PYTHONPATH ; . "`
```

最后，确保你是用 `nosetests` 来进行测试，而不是在用 Python。

**我运行 `nosetests` 的时候看到了 `UserWarning`。** 你可能装了两个版本的 Python，或者你不是用的 `distribute`，回去跟着练习 46 安装一下 `distribute` 或者 `pip` 就可以了。