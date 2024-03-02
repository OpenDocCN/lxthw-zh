# 练习 40 模块、类和对象

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.45.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.45.learn-py3.md)

Python 是一门“面向对象的编程语言”（Object Oriented Programming）。这是指 Python 中有一个叫做 类（class）的结构，能够让你用一种特定的方式结构化你的软件。通过使用类，你可以让你的程序保持连贯性，使用起来更清晰。至少理论上是这样。

我现在要教你一些面向对象编程的初级知识——类和对象，就用你已经学过的列表和模块来解释。我知道面向对象编程（OOP）这个说法听起来有点抽象，但是你必须试着去理解它，老老实实敲代码，我会在下一个练习中深入讲解。

让我们开始吧。

## 模块就像字典

你知道一个字典是如何被创建、使用以及将一个东西映射到另一个东西上。也就是说，如果你有一个字典的键是“apple”，你可以这样做来获取它：

ex40a.py

```py
1 mystuff =  {'apple':  "I AM APPLES!"}
2  print(mystuff['apple'])
```

记住这种 "get X from Y" 的方式。现在想想模块。你已经用过一些了，应该知道它们是：

*   一个包含函数和变量的 Python 文件 ..
*   你导入这个文件。
*   你用 `.` 运算符来获取这个模块中的函数或变量。假设我有一个名为 `mystuff.py` 的模块，我在其中放了一个叫做 apple 的函数。以下是 `mystuff.py` 这个模块的内容：

mystuff.py

```py
1  def apple():
2  print("I AM APPLES!")
```

**ai 酱注：**新建一个 mystuff.py 文件来输入。

一旦有了这些代码，我就可以通过导入来使用这个模块，然后获取其中的 apple 函数：

ex40b.py

```py
1  import mystuff
2 mystuff.apple()
```

**ai 酱注：**新建一个 ex40b.py 文件来输入。

我还可以创建一个名为 `tangerine` 的变量:

mystuff.py

```py
1  def apple():
2  print("I AM APPLES!")
3
4  # this is just a variable
5 tangerine =  "Living reflection of a dream"
```

**ai 酱注：**继续在 mystuff.py 文件中输入第 4-5 行。

我可以用同样的方式来访问这个变量：

ex40b.py

```py
1  import mystuff
2
3 mystuff.apple()
4  print(mystuff.tangerine)
```

**ai 酱注：**继续在 ex40b.py 文件中输入第 4 行。

说回字典，你应该已经意识到了上述模块的使用与字典非常类似，但是语法有些不一样，让我们对比一下：

```py
1 mystuff['apple']  # get apple from dict
2 mystuff.apple()  # get apple from the module
3 mystuff.tangerine # same thing, it's just a variable
```

这表明 Python 中有一个非常通用的模式：

*   用一个键=值（key=value）形式的容器。
*   通过键的名称来从中获取内容。在字典中，键是一个字符串，语法是：`[key]`。而在模块中，键是一个识别符，语法是 `.key`，除此之外它们几乎是同一种东西。

### 40.1.1 类就像模块

你可以把模块想象成一个可以储存 Python 代码并且可以用 `.` 运算符获取它的特定字典。Python 还有一种类似功能的结构叫做类（class）。**类是一种整合一组函数和数据的方式，它将函数和数据放在一个容器内以便你能通过 `.` 运算符进行访问。**

如果我要创建一个类似 mystuff 模块的类，我会这么做：

ex40c.py

```py
1  class  MyStuff(object):
2
3  def __init__ (self):
4  self.tangerine =  "And now a thousand years between"
5
6  def apple(self):
7  print("I AM CLASSY APPLES!")
```

**ai 酱注：**新建一个 ex40c.py 文件来输入。

和模块比起来这看起来有些复杂，而且不同点很多，但是你应该能够看出来它就像一个小型的 MyStuff 模块，包含了一个 `apple()` 函数。可能让你困惑的是这个 `**init**()` 函数以及设置实例变量使用的 `self.tangerine` 。

使用类而不用模块的原因有：你可以用这个 MyStuff 类复制很多个，如果你想的话，一次几百万个都行，并且它们之间不会相互干涉。但是当你导入一个模块，对整个程序来说只有一个，除非你用一些黑客技术。

不过在你理解这些之前，你需要先知道什么是“对象”，以及如何和 `MyStuff` 类一起使用，就像你使用 `mystuff.py` 模块一样。

### 40.1.2 对象就像导入（import）

如果说类是一个小型模块，那么应该要有一个概念和 import 类似。这个概念就叫做“实例化”（instantiate），你可以理解为它是“创造”（create）一词的华而不实、令人讨厌、自以为是的说法。当你实例化一个类，你得到的东西就叫做对象。

你通过像函数一样调用这个类来实例化（创造）一个对象，就像这样：

ex40c.py

```py
1 thing =  MyStuff()
2 thing.apple()
3  print(thing.tangerine)
```

**ai 酱注：**继续在 ex40c.py 文件中输入。

第一行就是实例化操作，它很像调用一个函数。不过，Python 在屏幕后面为你协调了一系列事件，我会为你过一下这些步骤：

*   Python 找了一下 `MyStuff()` 然后发现它是你定义的一个类。
*   Python 创建了一个空对象，以及你在类中用 `def` 指定的所有函数。
*   然后 Python 会看你会不会用一个神奇的 `**init**` 函数，来初始化你新创建的空对象。
*   在 `MyStuff` 类的 `**init**` 函数中，还有一个变量 `self` ，这是 Python 为我创建的空对象，我可以在里面设置变量，就像在模块、字典或其他对象里一样。
*   在这个例子中，我设置了一个 `self.tangerine` 变量，并给它 赋了一句歌词，然后我就完成了对这个对象的初始化。
*   现在 Python 可以把这个新打造的对象赋给 `thing` 变量来供我使用。这就是当你像调用函数一样调用一个类的时候，Python 所做的类似于“小型导入”的基本过程。记住，这里不是把这个类给你，而是以这个类为蓝本，创建一个同类型的副本。

你要记住，我告诉你的是一些不太准确的概念，主要是希望能基于已经学过的模块来以帮助你理解类。但事实上，类和对象会在这一点上与模块产生偏离。如果我更坦诚一点，我应该这样说：


+    类就像创建新的小型模块的蓝本或定义。 
+    实例化是你如何创建这些小型模块并同时导入它们。“实例化”的意思就是从类那里创建一个对象。 
+    你所创建的小型模块的结果被称作对象，然后你把它赋给一个变量来使用。

至此，对象和模块开始变得截然不同，以上只能是帮助你理解类和对象的一个桥梁。

### 40.1.3 获取数据

我现在有三种从获取数据的方式：

```py
1  # dict style
2 mystuff['apples']
3
4  # module style
5 mystuff.apples()
6  print(mystuff.tangerine)
7
8  # class style
9 thing =  MyStuff()
10 thing.apples()
11  print(thing.tangerine)
```

### 40.1.4 第一个类的例子

你应该已经注意到了这三种键值对（键=值）容器的相似之处，并且可能还有一大堆问题要问。先别着急问，因为下个练习会向你硬性灌输一些“面向对象的术语”。在这个练习中，我只希望你敲敲代码，让程序正常运行，这样你能在继续学习之前获得一些切身体验。

ex40.py

```py
1  class  Song(object):
2
3  def __init__(self, lyrics):
4  self.lyrics = lyrics
5
6  def sing_me_a_song(self):
7  for line in  self.lyrics:
8  print(line)
9
10 happy_bday =  Song(["Happy birthday to you",
11  "I don't want to get sued",
12  "So I'll stop right there"])
13
14 bulls_on_parade =  Song(["They rally around tha family",
15  "With pockets full of shells"])
16
17 happy_bday.sing_me_a_song()
18
19 bulls_on_parade.sing_me_a_song()
```

## 你会看到

练习 40 会话

```py
$ python3.6 ex40.py
Happy birthday to you
I don't want to get sued
So I'll stop right there
They rally around tha family
With pockets full of shells
```

## 附加练习

*   用这个方法再写一些歌，确保你明白你正在用字符列表来传歌词。
*   把歌词放在一个单独的变量里，然后把这个变量放在类里面来使用。
*   如果你能搞定这些，可以用它来做更多的事情。要是你现在没什么想法也别担心，就试试看会发生什么。然后把它们掰开、揉碎、反复研究。
*   在网上搜搜“面向对象的编程”，然后填满你的大脑。别担心你看不懂，因为几乎一半的东西我也看不懂。

## 常见问题

**为什么我在类下面用 `**init**` 函数或者其他函数的时候要用 `self` ？** 如果你不用 `self`，那么像 `cheese = 'Frank'` 这样的代码就会很含糊，计算机不知道你是指实例的 cheese 属性还是 一个叫做 cheese 的局部变量。而用 `self.cheese = 'Frank'` 的话就会很清晰，你是指实例的属性 `self.cheese` 。