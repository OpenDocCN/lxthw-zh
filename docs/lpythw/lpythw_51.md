# 练习 47.自动化测试

# 练习 47.自动化测试

你需要一遍一遍地在你的游戏中输入命令，来测试游戏的功能是否正常。这个过程是很枯燥无味的。如果能写一小段代码用来测试你的代码岂不是更好？然后无论你对程序做了什么修改，或者添加了什么新东西，你只要“跑一下你的测试”，而这些测试能确认程序依然能正确运行。这些自动测试不会抓到所有的 bug，但可以让你无需重复输入命令运行你的代码，从而为你节约很多时间。

从这节练习开始，以后的练习将不会有“你应该看到的结果”部分，取而代之的是一个“你应该测试的东西”。从现在开始，你需要为自己写的所有代码写自动化测试，而这将让你成为一个更好的程序员。

我不会解释你为什么需要写自动化测试。我要告诉你的是，你想要成为一个程序员，而程序的作用是让无聊冗繁的工作自动化，测试一个软件毫无疑问是无聊冗繁的，所以你还是写点代码让它为你测试的更好。

这应该是你需要的所有的解释了。因为你写单元测试的原因是让你的大脑更加强健。读了这本书，你写了很多代码让它们实现一些事情。现在你将更进一步，写出懂得你写的其他代码的代码。这个写代码测试你写的其他代码的过程将强迫你清楚的理解你之前写的代码。这会让你更清晰地了解你写的代码实现的功能及其原理，而且让你对细节的注意更上一个台阶。

## 编写测试用例

我们将拿一段非常简单的代码为例，写一个简单的测试，这个测试将建立在上节我们创建的项目骨架上面。

首先从你的项目骨架创建一个叫做`ex47`的项目。下面是你要采取的步骤。我会给出文字说明，而不是直接告诉你该如何写代码，所以你要自己弄明白并写出代码。

> 1.  复制`skeleton`到`ex47`
> 2.  将所有的`NAME`重命名为`ex47`
> 3.  修改所有文件中`NAME`为`ex47`
> 4.  最后删除所有的`*.pyc`文件

如果遇到什么困难，回顾一下练习 46，如果你不能简单的完成这些，那你需要多练习几次。

> **NOTE:**记得通过命令`nosetests`来检测你的测试代码没有错误信息。你可以通过`python ex47_tests.py`来运行，但是它不会那么容易的运行，你必须保证你的每一个测试文件正常运行。

接下来创建一个简单的`ex47/game.py`文件，里边放一些用来被测试的代码。我们现在放一个傻乎乎的小 class 进去，用来作为我们的测试对象：

```py
class Room(object):

    def __init__(self, name, description):
        self.name = name
        self.description = description
        self.paths = {}

    def go(self, direction):
        return self.paths.get(direction, None)

    def add_paths(self, paths):
        self.paths.update(paths) 
```

准备好了这个文件，接下来把测试骨架改成这样子：

```py
from nose.tools import *
from ex47.game import Room

def test_room():
    gold = Room("GoldRoom", 
                """This room has gold in it you can grab. There's a
                door to the north.""")
    assert_equal(gold.name, "GoldRoom")
    assert_equal(gold.paths, {})

def test_room_paths():
    center = Room("Center", "Test room in the center.")
    north = Room("North", "Test room in the north.")
    south = Room("South", "Test room in the south.")

    center.add_paths({'north': north, 'south': south})
    assert_equal(center.go('north'), north)
    assert_equal(center.go('south'), south)

def test_map():
    start = Room("Start", "You can go west and down a hole.")
    west = Room("Trees", "There are trees here, you can go east.")
    down = Room("Dungeon", "It's dark down here, you can go up.")

    start.add_paths({'west': west, 'down': down})
    west.add_paths({'east': start})
    down.add_paths({'up': start})

    assert_equal(start.go('west'), west)
    assert_equal(start.go('west').go('east'), start)
    assert_equal(start.go('down').go('up'), start) 
```

这个文件导入了你在`ex47.game`创建的`Room`这个类，接下来我们要做的就是测试它。于是我们看到一系列的以`test_`开头的测试函数，它们就是所谓的“测试用例(test case)”，每一个测试用例里面都有一小段代码，它们会创建一个或者一些房间，然后去确认房间的功能和你期望的是否一样。它测试了基本的房间功能，然后测试了路径，最后测试了整个地图。

这里最重要的函数是`assert_equal`，它保证了你设置的变量，以及你在`Room` 里设置的路径和你的期望相符。如果你得到错误的结果的话，`nosetests` 将会打印出一个错误信息，这样你就可以找到出错的地方并且修正过来。

## 测试指南

在写测试代码时，你可以照着下面这些不是很严格的指南来做：

> 1.  测试脚本要放到`tests/`目录下，并且命名为`BLAH_tests.py`，否则 `nosetests`就不会执行你的测试脚本了。这样做还有一个好处就是防止测试代码和别的代码互相混掉。
> 2.  为你的每一个模组写一个测试。
> 3.  测试用例（函数）保持简短，但如果看上去不怎么整洁也没关系，测试用例一般都有点乱。
> 4.  就算测试用例有些乱，也要试着让他们保持整洁，把里边重复的代码删掉。创建一些辅助函数来避免重复的代码。当你下次在改完代码需要改测试的时候，你会感谢我这一条建议的。重复的代码会让修改测试变得很难操作。
> 5.  最后一条是别太把测试当做一回事。有时候，更好的方法是把代码和测试全部删掉，然后重新设计代码。

## 你看到的结果

```py
$ nosetests
...
----------------------------------------------------------------------
Ran 3 tests in 0.008s

OK 
```

如果一切工作正常的话，你看到的结果应该就是这样。试着把代码改错几个地方，然后看错误信息会是什么，再把代码改正确。

## 附加题

> 1.  仔细读读`nosetest`相关的文档，再去了解一下其他的替代方案。
> 2.  了解一下 Python 的 “doc tests” ，看看你是不是更喜欢这种测试方式。
> 3.  改进你游戏里的 Room，然后用它重建你的游戏，这次重写，你需要一边写代码，一边把单元测试写出来。

## 常见问题

### Q: 当我运行`nosetest`的时候，我遇到一个语法错误

> 如果你遇到这个报错，看看错误信息是怎么说的，并改正该行或上一行的错误。类似`nosetest`的工具是在运行你的代码和测试代码，所以他可以像运行 python 一样发现你的语法错误。

### Q: 我无法导入`ex47.game`

> 确认你创建了`ex47/__init__.py`文件，参照练习 46，看它是如何做的。如果这个文件没有问题，在 OSX/Linux 下执行:`export PYTHONPATH=.`在 window 下执行`$env:PYTHONPATH = "$env:PYTHONPATH;."`，最后，确认你是用`nosetest`运行测试脚本，而不是用 python。

### Q: 我运行`nosetest`的时候，遇到一个报错`UserWarning`

> 你可能安装了两个版本的 python 或者没有使用`distribute`，按照我在练习 46 中所描述的安装`distribute`或`pip`。