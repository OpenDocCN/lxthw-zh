# 练习 44 继承和组合

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.49.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.49.learn-py3.md)

在英雄打败坏人的童话故事中，总有一个类似黑暗森林的东西。它可能是一个洞穴、一片森林、另一个星球，或者只是一些每个人都知道的英雄不应该去的地方。当然，在介绍了坏人之后不久，你就会发现，是的，英雄不得不去那个愚蠢的森林杀死坏人。似乎英雄总是不停地陷入需要他冒着生命危险待在邪恶森林里这个情境。

你很少能读到一些英雄足够聪明、能完全避免这种境地的童话故事，你永远不会听到一个英雄说：“等等，如果我离开去公海发财，离开我的宝贝儿，我会死的，然后她就得嫁给一个叫汉珀丁克（Humperdink）的丑王子。汉珀丁克！我想我会留在这里，做一个经营租赁业务的农场男孩。”如果他这么做了，就不会有火灾沼泽、死亡、复活、剑战、巨人，或者任何类型的故事。正因为如此，这些故事中的森林似乎就像个黑洞一样存在着，不管主人公做什么，它都会把他拖进去。

在面向对象编程中，继承（inheritance）就是邪恶的森林。有经验的程序员知道要避免这种邪恶，因为他们知道在“继承”这个黑暗森林的深处，是邪恶的女王“多重继承”（Multiple Inheritance）。她喜欢吃软件和程序员，用她那巨大的复杂的牙齿，咀嚼堕落者的血肉。但是森林是如此强大、如此诱人，以至于几乎每个程序员都必须深入其中，在他们可以自称为真正的程序员之前，尝试带着邪恶皇后的人头活着出来。你根本无法抗拒继承森林的吸引力，所以你会不可避免地进去。在这次冒险之后，你要学会离开那座愚蠢的森林，如果你被迫再次进入森林，你需要带一支军队。

这是一种用来讲授“继承”的非常有趣的方式。你们需要小心使用继承。目前正在森林里与女王搏斗的程序员可能会告诉你必须进去。他们这样说是因为他们需要你的帮助，因为他们所创造的可能对他们来说太多而难以驾驭。但你应该永远记住这一点：继承的大多数用法都可以用组合（composition）来简化或替换。并且无论如何都要避免多重继承。

## 什么是继承？

继承用来表明一个类将从其父类那里获得大多数或所有特性。无论何时你写 `class Foo(Bar)`，继承都会隐式地发生，它的意思是“创建一个继承自 Bar 的 Foo 类”。当你这样做的时候，编程语言会让你对 Foo 的实例所做的任何动作都能像对 Bar 的实例所做的那样生效。这样做可以让你把公共函数功能放在 Bar 类中，然后在 Foo 类中按需将该功能专门化。

当你在做这种专门化时，有三种父类和子类可以交互的方法：

*   对子类的行为意味着对父类的行为。

*   子类上的操作会覆盖父类上的操作。

*   子类上的操作会更改父类上的操作。

现在，我会依次演示这些方法以及它们的代码。

### 44.1.1 隐式继承（Implicit Inheritance）

首先，我会向你展示当你在父类而不是子类中定义一个函数时发生的隐式动作。

ex44a.py

```py
1  class  Parent(object):
2
3  def  implicit(self):
4  print("PARENT implicit()")
5
6  class  Child(Parent):
7  pass
8
9 dad =  Parent()
10 son =  Child()
11
12 dad.implicit()
13 son.implicit()
```

在子类 Child 下面使用 pass 是告诉 Python 你需要一个空块的方式。这样就创建了一个名为 Child 的类，但是并没有什么新的内容需要定义。相反，它将继承父类的所有行为。当你运行这个代码，你会得到:

Exercise 44a 会话

```py
$ python3.6 ex44a.py
PARENT implicit()
PARENT implicit()
```

注意，即使我在第 16 行调用了 `son.implicit()`，并且 Child 里面也没有定义一个隐式函数，它仍然可以正常运行，它调用了在 Parent 中定义的那个函数。这表明如果将函数放在基类中(比如 Parent），然后所有子类（比如 Child）会自动获得这些特性。对于需要写很多重复代码的类来说非常方便。

### 44.1.2 显式继承（Override Explicitly）

隐式调用函数的问题在于，有时你希望子类的行为有所不同。在本例中，你希望覆盖子类中的函数，从而有效地替换功能。为此，你只需要在 Child 中定义一个同名函数。例如:

ex44b.py

```py
1  class  Parent(object):
2
3  def  override(self):
4  print("PARENT override()")
5
6  class  Child(Parent):
7
8  def  override(self):
9  print("CHILD override()")
10
11 dad =  Parent()
12 son =  Child()
13
14 dad.override()
15 son.override()
```

在这个例子中，两个类都有一个名为 override 的函数，让我们看看当你运行它的时候会发生什么：

Exercise 44b 会话

```py
$ python3.6 ex44b.py
PARENT override()
CHILD override()
```

如你所见，当第 14 行运行时，它运行了 Parent.override 函数，因为那个变量（dad）是一个 Parent。但是当第 15 行运行时，它打印了 Child.override 信息。因为 son 是 Child 的一个实例，Child 通过定义它自己的版本来重写了那个函数。

现在休息一下，在继续之前尝试研究一下这两个概念。

### 44.1.3 修改前后

第三种使用继承的方式是覆盖的一种特殊情况，你希望在父类的版本运行之前或之后更改行为。你首先像上一个示例那样覆盖该函数，然后使用名为 super 的 Python 内置函数调用父类版本。

下面是一个示例，帮助你理解这个描述:

ex44c.py

```py
1  class  Parent(object):
2
3  def altered(self):
4  print("PARENT altered()")
5
6  class  Child(Parent):
7
8  def altered(self):
9  print("CHILD, BEFORE PARENT altered()")
10  super(Child,  self).altered()
11  print("CHILD, AFTER PARENT altered()")
12
13 dad =  Parent()
14 son =  Child()
15
16 dad.altered()
17 son.altered()
```

这里比较重要的是 9-11 行，在 Child 中，当调用 `son.altered()` 时，我其实做了以下事情:

*   因为在 `Child.altered` 版本运行时，我就重写了 Parent.altered 。第 9 行就按照你的预期执行了。

*   在这个例子中，我想做一个之前和之后的对比，所以在第 9 行之后，我想使用 super 来获得 `Parent.altered` 版本。

*   在第 10 行，我调用 `super(Child, self).altered()`，它意识到需要继承，并会为你获取 Parent 类。你应该能够把这个理解为“使用参数 Child 和 self 来调用 super，然后在它返回的任何地方调用 altered 函数”。

*   此时，Parent.altered 版本的函数运行，并打印出 Parent 的信息。

*   最后，它从 Parent.altered 返回。Child.altered 函数继续打印出之后的信息。

如果你运行这段代码，你会看到:

Exercise 44c 会话

```py
$ python3.6 ex44c.py
PARENT altered()
CHILD, BEFORE PARENT altered()
PARENT altered()
CHILD, AFTER PARENT altered()

```

### 44.1.4 三者结合

为了解释以上所有情况，我有一个最终版本，用一个文件来说明继承的每种交互情况：

ex44d.py

```py
1  class  Parent(object):
2
3  def  override(self):
4  print("PARENT override()")
5
6  def  implicit(self):
7  print("PARENT implicit()")
8
9  def altered(self):
10  print("PARENT altered()")
11
12  class  Child(Parent):
13
14  def  override(self):
15  print("CHILD override()")
16
17  def altered(self):
18  print("CHILD, BEFORE PARENT altered()")
19  super(Child,  self).altered()
20  print("CHILD, AFTER PARENT altered()")
21
22 dad =  Parent()
23 son =  Child()
24
25 dad.implicit()
26 son.implicit()
27
28 dad.override()
29 son.override()
30
31 dad.altered()
32 son.altered()
```

过一遍这段代码的每一行，然后给每一行加上注释，说明它的作用，以及它是否进行了重写, 然后运行它，看是否与你的预期相符：

Exercise 44d 会话

```py
$ python3.6 ex44d.py
PARENT implicit()
PARENT implicit()
PARENT override()
CHILD override()
PARENT altered()
CHILD, BEFORE PARENT altered()
PARENT altered()
CHILD, AFTER PARENT altered()
```

### 用 super() 的理由

这似乎是常识，但是我们遇到了多重继承的麻烦。多重继承是指你定义了一个继承自一个或多个类的类，就像这样:

```py
class  SuperFun  (Child,  BadStuff):
pass
```

这就像是在说“创建一个名为 SuperFun 的类，它同时继承自 Child 类和 BadStuff 类。”

在这种情况下，每当你对任何 SuperFun 的实例执行隐式操作时，Python 都必须在 Child 类和 BadStuff 类的层级结构中查找可能的函数，不过它需要以一致的顺序来执行这项操作。为了做到这一点，Python 使用了“方法解析顺序”(method resolution order，MRO)和一种被称为 C3 的算法。

因为 MRO 非常复杂，并且使用了定义良好的算法，所以 Python 不能让你自己来处理 MRO。而是提供了 `super()` 函数，它可以在你需要更改类似动作的地方为你解决这个问题，就像我在 `Child.altered` 中所做的那样。使用 `super()`，你不用担心是否正确，Python 会为你找到正确的函数。

44.2.1 用 `**init**` 来使用 super()

`super()` 最常用的用法其实是在基类中使用 `**init**` 函数。这通常是你在一个子类中唯一需要做一些操作，然后在父类中完成初始化的地方。下面是一个在用在子类上的简单例子:

```py
1.  class  Child  (Parent):

3.  def __init__(self, stuff):
4.  self.stuff = stuff
5.  super(Child,  self).__init__(  )
```

这和上面例子中的 `Child.altered` 很像，除了我在用 `Parent.**init**` 给 Parent 做初始化之前在 `**init**` 里面设置了一些参数。

### 组合

继承很有用，但是还有一种能实现相同效果的方法，就是使用其他类和模块，而不是依赖于隐式继承。如果你看看使用继承的三种方法，其中两种都涉及编写新代码来替换或更改函数功能。这很容易通过调用模块中的函数来复制。例如：

ex44e.py

```py
1  class  Other(object):
2
3  def  override(self):
4  print("OTHER override()")
5
6  def  implicit(self):
7  print("OTHER implicit()")
8
9  def altered(self):
10  print("OTHER altered()")
11
12  class  Child(object):
13
14  def __init__(self):
15  self.other =  Other()
16
17  def  implicit(self):
18  self.other.implicit()
19
20  def  override(self):
21  print("CHILD override()")
22
23  def altered(self):
24  print("CHILD, BEFORE OTHER altered()")
25  self.other.altered()
26  print("CHILD, AFTER OTHER altered()")
27
28 son =  Child()
29
30 son.implicit()
31 son.override()
32 son.altered()
```

在这段代码中，我没有使用 Parent 这个名字，因为不存在父子 is-a 关系，而是一个 has-a 关系，其中 Child 有一个（has-a） Other 来完成它的工作。当我运行这段代码，会得到以下输出：

Exercise 44e 会话

```py
$ python3.6 ex44e.py
OTHER implicit()
CHILD override()
CHILD, BEFORE OTHER altered()
OTHER altered()
CHILD, AFTER OTHER altered()
```

可以看到，Child 和 Other 中的大多数代码都是相同的，可以完成相同的事情。唯一的区别是我必须定义一个 `Child.implicit` 函数来完成这个动作。然后我可以问自己是否需要这个 Other 作为一个类，我是否可以将它放入一个名为 `Other.py` 的模块中？

## 何时使用继承或组合

“继承与组合”的问题可以归结为试图解决可复用代码的问题。你不希望在你的软件中到处都有重复的代码，因为这不够简洁和高效。继承通过在基类中创建隐含特性的机制来解决这个问题。组合通过提供模块以及调用其他类中的函数来解决这个问题。

如果这两个解决方案都解决了复用问题，那么在哪种情况下用哪个方案比较合适呢？答案非常主观，但我会给你我的三个指导方针来帮你做选择：

*   无论如何都要避免多重继承，因为它太复杂而且不可靠。如果你被它困住了，那么要准备好了解一下类的层次结构，并花时间找出所有内容的来源。

*   使用组合将代码打包到模块中，这些模块可以用于许多不同的、不相关的地方和情境。

*   只有当存在明显相关的可复用代码片段，并且这些代码片段符合单个通用概念，或者由于你使用了某些东西而别无选择时，你才可以使用继承。

不要成为这些规则的奴隶。关于面向对象编程，需要记住的一点是，它完全是程序员为了打包和共享代码而创建的一种社会约定。因为这是一种社会惯例，并且在 Python 中已经形成了这种惯例，你可能会因为与你一起工作的人而被迫绕过这些规则。在这种情况下，弄明白他们是如何使用每一种东西，然后努力适应这种情况。

## 附加练习

这个练习只有一个附加练习，因为这节课是一个大练习。请阅读 [`www.python.org/dev/peps/pep-0008/`](http://www.python.org/dev/peps/pep-0008/) 并开始在你的代码中使用它。你会注意到其中一些和你在本书中所学的不太一样，但是现在你应该能够理解它们的建议并且用在自己的代码中。本书中的其余代码是否遵循这些指导原则，取决于它是否会让代码变得更加混乱。我建议你也这样做，因为理解比你把深奥的规则强加给别人更重要。

## 常见问题

**如何才能更好地解决我之前没有遇到过的问题？**要想更好地解决问题，唯一的方法就是自己解决尽可能多的问题。通常情况下，人们遇到一个难题，就会冲出去寻找答案。当你着急完成工作的时候，这没问题。但是如果你有时间自己解决，那就花时间去解决。停下来，尽可能长时间地思考这个问题，尝试所有可能的方案，直到你把它解决或者放弃。在这之后，你找到的答案会更令人满意，你最终也会更擅长解决问题。

**对象不就是类的拷贝吗？**在某些语言中（如 JavaScript），这是对的。这些被称为原型语言，除了用法之外，对象和类之间没有太多区别。然而，在 Python 中，类充当“铸造”（mint）新对象的模板，类似于使用模具（die） 来铸造硬币的概念。