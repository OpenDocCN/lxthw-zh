# 练习 40.模块, 类和对象

# 练习 40.模块, 类和对象

Python 是一门“面向对象编程语言”。这意味着在 Python 中有一个叫做类的概念，你能通过类用一种特殊的方式构建你的软件。使用类的概念，能给你的程序增添一致性，这样你可以用一种很轻松方便的方式调用他们。至少，这是面向对象的理论。

我现在要通过使用你已经知道的字典和模块等来教你开始学习面向对象编程、类和对象。我的问题是面向对象编程（OOP）只是普通的怪异。你要为之而奋斗，努力尝试理解我讲的内容，编写代码，在下一个练习中，我会更深入的讲解。

我们要开始了。

## 模块就像字典

你知道字典是如何被创建以及使用的，它用来将一个事物对应到另一个事物。意思就是说如果你有一个字典，字典中包括一个 key "apple"，那么你就可以实现：

```py
mystuff = {'apple': "I AM APPLES!"}
print mystuff['apple'] 
```

记住“从 X 获取 Y”的说法，然后想一想模块（module）。你之前已经写过一些模块，你应该知道它们：

> 1.  包含一些函数和变量的 python 文件
> 2.  你可以导入这个文件
> 3.  你可以用`.`操作符访问这个模块的函数和变量

想象一下我有一个叫做`mystuff.py`的模块，在这个模块中有一个叫做`apple`的函数，下面是 `mystuff.py` 模块的代码：

```py
# this goes in mystuff.py
def apple():
    print "I AM APPLES!" 
```

当我写完以上代码，我就可以通过 import 来调用`mystuff`模块，并访问`apple`函数：

```py
import mystuff
mystuff.apple() 
```

我还可以增加一个叫做`tangerine`的变量:

```py
def apple():
    print "I AM APPLES!"

# this is just a variable
tangerine = "Living reflection of a dream" 
```

可以用相同的方法来访问：

```py
import mystuff

mystuff.apple()
print mystuff.tangerine 
```

返回再看字典，你应该发现模块的使用跟字典是相似的，只不过语法不同，我们比较一下：

```py
mystuff['apple'] # get apple from dict
mystuff.apple() # get apple from the module
mystuff.tangerine # same thing, it's just a variable 
```

也就是说我们在 Python 中有一套通用的模式：

> 1.  有一个 key=value 模式的容器
> 2.  通过 key 从容器中获取数据

在字典中，key 是一个字符串，写法为`[key]`,在模块中，key 是一个标识符，写法为`.key`，在其余的地方，他们几乎是一样的。

## 类就像模块

你可以认为一个模块就是一个可以存放 Python 代码的特殊字典，这样你就可以通过`.`操作符访问它。Python 还有一个另外的结构提供相似的功能，就是类（class）。类的作用是组织一系列的函数和数据并将它们放在一个容器里，这样你可以通过`.`操作符访问到它们。

如果我想创建一个类似`mystuff`的类，我需要这样做：

```py
class MyStuff(object):

    def __init__(self):
        self.tangerine = "And now a thousand years between"

    def apple(self):
        print "I AM CLASSY APPLES!" 
```

这相比于模块复杂一些，对比之下肯定会有不同，但是你应该能返现这个类就像写一个包含`apple()`方法的“迷你”`mystuff`模块一样.让你困惑的地方可能是`__init__()`这个方法以及使用`self.tangerine`给`tangerine`赋值。

这正是为什么要使用类而不是仅有模块的原因：你可以使用`Mystuff`这个类，还可以用它来创建更多个`Mystuff`，而他们之间也不会互相冲突。当你导入一个模块时，你的整个项目也就只有一个这个模块。

在你理解这些之前，你需要明白什么是“对象”，以及如何像使用`Mystuff.py`模块一样使用`Mystuff`这个类。

## 对象就像导入

如果一个类就像一个迷你模块，那么类也会有一个类似`import`的概念，这个概念被称为实例化，这只是对创建一种更虚幻更聪明的叫法。当一个类被实例化，你就得到一个类的对象。

实例化类的方法就是像调用函数一样调用这个类：

```py
thing = MyStuff()
thing.apple()
print thing.tangerine 
```

第一行就是实例化的操作，这个操作多像是在调用一个函数啊。当然了，python 在幕后帮你做了一系列的事情，我带你来看看具体的调用步骤：

> 1.  python 查找 `MyStuff()` 并确认它是你已经定义过的类
> 2.  python 创建一个空的对象，该对象拥有你在类中用`def`创建的所有函数
> 3.  python 看你是否创建了`__init__`函数，如果有，调用该方法初始化你新创建的空对象
> 4.  在`MyStuff`中，`__init__`方法有一个额外的变量`self`，这是 python 为我创建的一个空的对象，我可以在其上设置变量。
> 5.  然后，我给`self.tangerine`设置一首歌词，然后初始化这个对象
> 6.  python 可以使用这个新创建好的对象，并将其分配给我可以使用的变量`thing`。

这就是当你调用一个类的时候，python 做的事情。记住，这并不是把类给你，而是把类作为蓝本来创建这种类型东西的副本。

我给了你一个类的简单工作原理，这样你就可以基于你所了解的模块，建立你对类的理解。事实上，在这一点上，类和对象与模块是有区别的：

> *   类是用来创建迷你模块的蓝本或定义
> *   实例化是如何创建这些小模块，并在同一时间将其导入。实例化仅仅是指通过类创建一个对象。
> *   由此产生的迷你模块被称为对象，你可以将其分配给一个变量，让它开始运行

在这一点上，对象和模块的表现不同，这只是提供一种让你理解类和对象的方法。

## 从一个事物中获取事物

现在我提供给你 3 中方法从一个事物中获取另一个：

```py
# dict style
mystuff['apples']

# module style
mystuff.apples()
print mystuff.tangerine

# class style
thing = MyStuff()
thing.apples()
print thing.tangerine 
```

## 类的举例

你应该可以看到在这三个 key=value 的容器类型有一定的相似性，你也可能有一堆问题.记住这些问题，下一节练习会训练你关于“面向对象的词汇”。这节练习中，我只想让你输入这些代码并保证它能正常运行，这样能让你再继续下一节练习之前获得一些经验。

```py
class Song(object):

    def __init__(self, lyrics):
        self.lyrics = lyrics

    def sing_me_a_song(self):
        for line in self.lyrics:
            print line

happy_bday = Song(["Happy birthday to you",
                   "I don't want to get sued",
                   "So I'll stop right there"])

bulls_on_parade = Song(["They rally around tha family",
                        "With pockets full of shells"])

happy_bday.sing_me_a_song()

bulls_on_parade.sing_me_a_song() 
```

## 你应该看到的内容

```py
$ python ex40.py
Happy birthday to you
I don't want to get sued
So I'll stop right there
They rally around tha family
With pockets full of shells 
```

## 附加题

> 1.  用本节学到的内容多写几首歌，确定你明白你把一个字符串的列表作为歌词传递进去。
> 2.  把歌词放进一个单独的变量，再把这个变量传递给类
> 3.  看看你能不能让这个类做更多的事情，如果没什么想法也没关系，试试看，会有什么
> 4.  在网上搜索一些“面向对象编程”的资料，尝试让你的大脑填满这些资料。如果这些资料对你没有用，也没关系，这些东西有一半对我来说也是没有意义的。

## 常见问题

### Q：为什么我在类里创建`__init__`或其他函数的时候需要使用`self`?

> 如果你不实用`self`，像这种代码`cheese = 'Frank'`就是不明确的. 代码并不清楚你指的是实例的`cheese`属性，还是一个叫做`cheese`d 的全局变量。如果你使用`self.cheese='Frank'`代码就会十分清楚你指的就是实例中的属性`self.cheese`.