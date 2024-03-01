# 练习 38.列表操作

# 练习 38.列表操作

你已经学过了列表。在你学习“while 循环”的时候，你对列表进行过“追加(append)”操作，而且将列表的内容打印了出来。另外你应该还在附加题里研究过 Python 文档，看了列表支持的其他操作。这已经是一段时间以前了，所以如果你不记得了的话，就回到本书的前面再复习一遍把。

找到了吗？还记得吗？很好。那时候你对一个列表执行了`append`函数。不过，你也许还没有真正明白发生的事情，所以我们再来看看我们可以对列表进行什么样的操作。

当你看到像 mystuff.append('hello') 这样的代码时，你事实上已经在 Python 内部激发了一个连锁反应。以下是它的工作原理：

> 1.  1.Python 看到你用到了`mystuff`，于是就去找到这个变量。也许它需要倒着检查看你有没有在哪里用`=`创建过这个变量，或者检查它是不是一个函数参数，或者看它是不是一个全局变量。不管哪种方式，它得先找到 mystuff 这个变量才行。
> 2.  一旦它找到了`mystuff`，就轮到处理句点`.`(period)这个操作符，而且开始查看`mystuff`内部的一些变量了。由于`mystuff`是一个列表，Python 知道它支持一些函数。
> 3.  接下来轮到了处理`append`。Python 会将“append”和`mystuff`支持的所有函数的名称一一对比，如果确实其中有一个叫`append`的函数，那么 Python 就会去使用这个函数。
> 4.  接下来 Python 看到了括号`(` (parenthesis) 并且意识到, “噢，原来这应该是一个函数”，到了这里，它就正常会调用这个函数了，不过这里的函数还要多一个参数才行。
> 5.  这个额外的参数其实是……`mystuff`!我知道，很奇怪是不是？不过这就是 Python 的工作原理，所以还是记住这一点，就当它是正常的好了。真正发生的事情其实是 `append(mystuff, 'hello')` ，不过你看到的只是 `mystuff.append('hello')` 。

大部分时候你不需要知道这些细节，不过如果你看到一个像这样的 Python 错误信息的时候，上面的细节就对你有用了：

```py
$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> class Thing(object):
...     def test(hi):
...             print "hi"
...
>>> a = Thing()
>>> a.test("hello")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: test() takes exactly 1 argument (2 given)
>>> 
```

就是这个吗？嗯，这个是我在 Python 命令行下展示给你的一点魔法。你还没有见过`class`不过后面很快就要碰到了。现在你看到 Python 说`test() takes exactly 1 argument (2 given)` (test() 只可以接受 1 个参数，实际上给了两个)。它意味着 python 把 `a.test("hello")` 改成了`test(a,"hello")`，而有人弄错了，没有为它添加 `a`这个参数。

一下子要消化这么多可能有点难度，我们将做几个练习，让你头脑中有一个深刻的印象。下面的练习将字符串和列表混在一起，看看你能不能在里边找出点乐子来：

```py
ten_things = "Apples Oranges Crows Telephone Light Sugar"

print "Wait there are not 10 things in that list. Let's fix that."

stuff = ten_things.split(' ')
more_stuff = ["Day", "Night", "Song", "Frisbee", "Corn", "Banana", "Girl", "Boy"]

while len(stuff) != 10:
    next_one = more_stuff.pop()
    print "Adding: ", next_one
    stuff.append(next_one)
    print "There are %d items now." % len(stuff)

print "There we go: ", stuff

print "Let's do some things with stuff."

print stuff[1]
print stuff[-1] # whoa! fancy
print stuff.pop()
print ' '.join(stuff) # what? cool!
print '#'.join(stuff[3:5]) # super stellar! 
```

## 你看到的结果

```py
$ python ex38.py
Wait there are not 10 things in that list. Let's fix that.
Adding:  Boy
There are 7 items now.
Adding:  Girl
There are 8 items now.
Adding:  Banana
There are 9 items now.
Adding:  Corn
There are 10 items now.
There we go:  ['Apples', 'Oranges', 'Crows', 'Telephone', 'Light', 'Sugar', 'Boy', 'Girl', 'Banana', 'Corn']
Let's do some things with stuff.
Oranges
Corn
Corn
Apples Oranges Crows Telephone Light Sugar Boy Girl Banana
Telephone#Light 
```

## 列表能实现什么

假设你打算创建一个基于钓鱼的电脑游戏。如果你不知道什么是钓鱼，花点时间在网上找到相关资料看一看。要做到这些，你需要里了解一些关于“扑克牌”的概念，并将它们变成你的 Python 程序。你必须用 python 写出知道如何玩一副虚拟扑克牌的代码，这样人们就能把你的游戏当成真实的游戏来玩，即使它不是真的。你需要的是一副“扑克牌”结构，而程序员就称之为“数据结构”。

什么是数据结构呢？如果你仔细想想，数据结构其实就是一种正式的构造（组织）一些数据（事实）的方法。真的就是这么简单，尽管一些数据结构十分错综复杂，它们也仅仅是在程序中存储数据的方式而已，这样你就能用不同的方式访问它们。

我将在下一节练习中更深入的讲解这些，但是列表是程序员常用的数据结构之一。它们只是数据的有序列表，你可以通过线性索引来存储或访问它们。什么？记住我说过的话，只是因为一个程序员说过“列表是一个列表”并不意味着它比真实世界中的列表复杂多少。 让我们以扑克牌为例：

> 1.  你有一堆有值的卡片。
> 2.  这些卡片式一堆，一列，或者可以从头到尾排列这些卡片。
> 3.  你可以随机的从顶部、中部或者底部取出卡片。
> 4.  如果你想找到某张特殊的卡片, 你必须一张一张的检索这些卡片。

让我们看看我说过什么：

“一个有序的列表”是的，扑克牌有第一张和最后一张"有一些你要存储的事物"是的，卡片就是我要存储的东西"可以随机访问"是的，在这副牌中我可以任意取出一张."是线性的"是的，如果我想找到特定的一张牌，我必须从头开始按顺序查找。"有索引的"差不多, 如果我让你找到一副扑克牌的第 19 张，你就必须按照顺序去数，直到你找到这一张。在 python 的列表中，计算机可以直接跳到你给出的索引处。这就是一个列表做的所有的事情，这么解释应该给了你一个在编程中找到列表概念的方法吧。编程中的每一个概念通常都有与真实世界相关联，至少在真实世界是有用的。如果你能找出虚拟的概念在真实世界中对应的概念，那你也可以通过这些找到数据结构到底是做什么的。

## 什么情况可以使用列表

当你有一些有东西能匹配列表数据结构的有用特性时，使用列表:

> 1.  如果你需要维护一组次序，记住，这是把次序编成列表，而不是给次序排序，列表不会帮你排序。
> 2.  如果你需要根据一个随机数访问列表内容，记住，这时候基数从 0 开始。
> 3.  如果你需要从头到尾操作列表内容，记住，这就是 for 循环。

## 附加题

> 1.  将每一个被调用的函数以上述的方式翻译成 Python 实际执行的动作。比如`more_stuff.pop()` 是 `pop(more_stuff)`.
> 2.  将这两种方式翻译为自然语言。
> 3.  上网阅读一些关于“面向对象编程(Object Oriented Programming)”的资料。晕了吧？嗯，我以前也是。别担心。你将从这本书学到足够用的关于面向对象编程的基础知识，而以后你还可以慢慢学到更多。
> 4.  查一下 Python 中的 “class” 是什么东西。不要阅读关于其他语言的 “class” 的用法，这会让你更糊涂。
> 5.  如果你不知道我讲的是些什么东西，别担心。程序员为了显得自己聪明，于是就发明了 Opject Oriented Programming，简称为 OOP，然后他们就开始滥用这个东西了。如果你觉得这东西太难，你可以开始学一下 “函数编程(functional programming)”。
> 6.  找出 10 种可以放在列表中的例子，并用它们写一些脚本。

## 常见问题

### Q：你没有说说不要用 while 循环？

> 是的，请记住，当需要的时候，你可以打破规则，只有蠢人才会一直一味的遵从规则。

### Q:`join(' ', stuff)`为什么没有生效？

> 文档中关于 join 的内容，写的没有意义，`join`是使用一个字符串将列表内容链接起来的一个方法，你可以试试这么写`' '.join(stuff).`.

### Q: 为什么你用了一个 while 循环？

> 试着用 for 循环改写一下，看看哪个更简单

### Q: `stuff[3:5]`实现了什么功能？

> 这句代码从`stuff`中获取了一个子集，包含 stuff 的第 3 和第 4 个元素，没有包含第 5 个元素。它和`range(3,5)`的工作原理相近。