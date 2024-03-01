# 练习 44.继承 Vs.包含

# 练习 44.继承 Vs.包含

在有关英雄战胜邪恶的童话中，总是有某种形式的黑暗森林。它可能是一个山洞，森林，另一个星球或者其他地方，每个人都知道英雄不应该去。当然，当不就之后坏人被你找到的时候，你发现，英雄已经去那个愚蠢的森林里杀坏人去了。看起来英雄进入了一种状态，这种状态要求英雄必须在这个邪恶的森林中冒险。

在面向对象编程中，继承就是那个黑暗森林。有经验的程序员知道要避免这种邪恶,因为他们知道,黑暗森林深处有着多重继承这个邪恶的皇后。 她喜欢那她那庞大的牙齿吃掉软件和程序员。但这个森林是如此强大，如此诱人，几乎每一个程序员都必须进入它，与邪恶的皇后战斗，尽量做到全身而退，才可以称自己是真正的程序员。你不能抗拒的继承森林的诱惑，所以你进去了。冒险之后，你试着远离那个邪恶的森林，当你再次被迫进入的时候，你会携带一支军队进入（这段翻译的太烂了，实在没办法把编程和童话联系起来！）

这是一种有趣的方式来解说我要在这节练习教你的东西，它叫做继承，当你使用它的时候，一定要当心再当心。正在森林里和女王战斗的程序员可能告诉你你必须进去。他们这么说是因为他们需要你的帮忙，可能因为他们创建了太多他们已经无法掌控的东西。但是你一定要记得：

大多数继承的用途，可以简化或用组合物所取代，并应不惜一切代价避免多重继承。

## 什么是继承

继承是用来描述一个类从它的父类那里获得大部分甚至全部父类的功能。当你写下`class Foo(Bar)`的时候，就发生了继承，这句代码的意思是“创建一个叫做 Foo 的类，并继承 Bar” 。当你执行这句的时候，编程语言使得`Foo`的实例所有的行为都跟`Bar`的实例一样。这么做，可以让你在类`Bar`中放一些通用功能，而那些需要特殊定制的函数或功能可以放在类 `Foo` 中。

当你需要做这些特殊化函数编写的时候，父子类之间有 3 中交互方法：

> 1.  子类的方法隐性继承父类方法
> 2.  子类重写父类的方法
> 3.  对子类的操作改变父类

我将按顺序给你展示这 3 种交互方式，并给你看它们的代码。

## 隐性继承

首先，我将给你展示的是隐性继承发生在你在父类中定义了方法，而在子类中没有：

```py
class Parent(object):

    def implicit(self):
        print "PARENT implicit()"

class Child(Parent):
    pass

dad = Parent()
son = Child()

dad.implicit()
son.implicit() 
```

在`class Child`下使用`pass`的目的是告诉 Python，在这里你想要一个空白的块。这里创建了一个叫做`Child`的类，但是没有在这个类中定义任何性的方法。它将从类`Parent`继承获得所有的方法。当你执行这段代码的时候，你会看到：

```py
$ python ex44a.py
PARENT implicit()
PARENT implicit() 
```

注意一下，尽管我再代码的 13 行调用了`son.implicit()`，而类`Child`并没有一个定义叫做`implicit`的方法，代码仍然正常工作了，因为它调用了`Parent`中定义的同名方法。这个高速你的是：如果你在基类(i.e., `Parent`)中定义了一个方法，那么所有的子类(i.e., `Child`) 都可以自动的获得这个功能。对于你需要在很多类中有重复的方法来说，非常方便。

## 重写方法

关于有些方法是隐式调用的问题原因在于有时候你想让子类有不同的表现。这时你想重写子类中的方法且有效的覆盖父类中的方法。要做到这一点，你只需要在子类中定义一个同名的方法就行，例如

```py
class Parent(object):

    def override(self):
        print "PARENT override()"

class Child(Parent):

    def override(self):
        print "CHILD override()"

dad = Parent()
son = Child()

dad.override()
son.override() 
```

在这个例子中，两个类中我都有一个叫做`override`的方法，所以让我们来看看当你运行此例时都发生了什么

```py
$ python ex44b.py
PARENT override()
CHILD override() 
```

你可以看到，当第 14 行执行时，它执行了父类的`override`方法，因为变量`dad`是一个父类实例，但是当第 15 行执行时，打印的是子类的`override`方法，这是因为`son`是一个子类的实例，这个子类重写了那个方法，定义了自己的版本。

休息以下，在继续下面的内容之前，尝试练习这两种方法。

## 之前或之后改变父类

第三种使用继承的方式比较特别，你想在父类版本的方法执行行为前后给出些提示，你首先像上个例子那样重写了方法，接着你使用一个 Python 内建的叫做`super`的方法得到了父类版本的方法调用。以下这个例子就是这么做的，你可以感受一下上面的描述是什么意思。

```py
class Parent(object):

    def altered(self):
        print "PARENT altered()"

class Child(Parent):

    def altered(self):
        print "CHILD, BEFORE PARENT altered()"
        super(Child, self).altered()
        print "CHILD, AFTER PARENT altered()"

dad = Parent()
son = Child()

dad.altered()
son.altered() 
```

重要的地方在于 9-11 行，在`son.altered()`被调用前我做了如下操作：

> 1.  因为我已经重写了子类的`Child.altered`方法，第 9 行的运行结果应该和你的期待是一样
> 2.  在这个例子中，我打算使用`super`来得到父类的`Parent.altered`版本。
> 3.  在第 10 行，我调用了`super(Child, self).altered()`方法, 这个方法能够意识到继承的发生，并给你获得类`Parent`。你可以这样读这行代码“调用`super`，参数为`Child`和`self`,然后不管它返回什么，调用方法`altered` ”
> 4.  在这种情况下，父类的`Parent.altered`版本执行，并打印出父类的信息。
> 5.  最后，代码从`Parent.altered` 返回， `Child.altered` 方法继续打印出剩下的信息。

运行了程序之后，你应该能看到下面的内容：

```py
$ python ex44c.py
PARENT altered()
CHILD, BEFORE PARENT altered()
PARENT altered()
CHILD, AFTER PARENT altered() 
```

## 三种组合使用

为了论证上面的三种方式，我有一个最终版本的文件，该文件给你展示了每一种继承方式的交互：

```py
class Parent(object):

    def override(self):
        print "PARENT override()"

    def implicit(self):
        print "PARENT implicit()"

    def altered(self):
        print "PARENT altered()"

class Child(Parent):

    def override(self):
        print "CHILD override()"

    def altered(self):
        print "CHILD, BEFORE PARENT altered()"
        super(Child, self).altered()
        print "CHILD, AFTER PARENT altered()"

dad = Parent()
son = Child()

dad.implicit()
son.implicit()

dad.override()
son.override()

dad.altered()
son.altered() 
```

通读每一行代码，不管有没有被重写，写一个注释用来解释每一行实现了什么，然后将代码运行起来，确认你的结果和你的期望是否一致：

```py
$ python ex44d.py
PARENT implicit()
PARENT implicit()
PARENT override()
CHILD override()
PARENT altered()
CHILD, BEFORE PARENT altered()
PARENT altered()
CHILD, AFTER PARENT altered() 
```

## 使用`super()`的原因

这看起来应该是常识，但是随后我们即将进入一个叫做所多重继承的麻烦事。 多重继承是指当你定义一个的类的时候，从一个或多个类继承，例如:

```py
class SuperFun(Child, BadStuff):
    pass 
```

上述代码的意思是, "创建一个叫做`SuperFun`的类，它同时继承类`Child` 和类 `BadStuff` ."

在这个例子中，只要你隐式的调用任何`SuperFun`的实例，Python 把必须从类`Child`和`BadStuff`查询可能的函数，但是，查找也需要一个顺序。为了做到这点，Python 使用"方法解析顺序"(MRO)和一种叫做 C3 的运算法则来直接获得。

因为 MRO 是复杂的，并使用了明确定义的算法，Python 不能让你来获得正确的 MRO，相反的，Python 提供给你`super()`方法，它用来处理所有这一切你需要改变类型的行为，如同我在`Child.altered`所实现的。使用`super()`你不必担心得到的是否是正确的方法，Python 会帮你找到正确的那个。

## `__init__`中使用`super()`

`super()`最常见的用途是在基类的`__init__`方法里。这通常是你需要在子类里实现什么事情，然后完成父类初始化的地方。以下是在类`Child`中这样做的一个简单的例子:

```py
class Child(Parent):

    def __init__(self, stuff):
        self.stuff = stuff
        super(Child, self).__init__() 
```

除了我在`__init__`中初始化父类之前定义了一些变量，这个跟上面的例子`Child.altered`几乎是一样的。

## 包含

继承是有用的， 但另一种方式仅仅是用其他类和模块就做到了同样的事情， 而没有使用隐性继承。如果你看一下使用继承的三种方式，其中的两种方法涉及编写新的代码来替换或改变父类功能。这可以很容易地通过调用模块函数复制。下面是一个例子：

```py
class Other(object):

    def override(self):
        print "OTHER override()"

    def implicit(self):
        print "OTHER implicit()"

    def altered(self):
        print "OTHER altered()"

class Child(object):

    def __init__(self):
        self.other = Other()

    def implicit(self):
        self.other.implicit()

    def override(self):
        print "CHILD override()"

    def altered(self):
        print "CHILD, BEFORE OTHER altered()"
        self.other.altered()
        print "CHILD, AFTER OTHER altered()"

son = Child()

son.implicit()
son.override()
son.altered() 
```

在这段代码中，我没有使用名字`Parent`，因为没有父子的`is-a`关系了。这是一个`has-a`关系,在这个关系中`Child``has-a``Other`被用来保证代码的正常工作。当我运行代码时，看到以下输出：

```py
$ python ex44e.py
OTHER implicit()
CHILD override()
CHILD, BEFORE OTHER altered()
OTHER altered()
CHILD, AFTER OTHER altered() 
```

你可以看到`Child`和`Other`中的大部分代码实现了相同的功能。唯一的不同之处在于我必须定义一个 `Child.implicit` 方法去做一个动作. 然后我可以问问自己，如果我需要一个`Other`类，是不是只要把它放在一个叫做`other.py`的模块中就可以?

## 什么时候用继承，什么时候用包含

继承与包含的问题可以归结为试图解决可重复使用代码的问题。你不想在你的软件中有重复的代码，因为这不是高效的干净的代码。继承通过创建一种机制，让你在基类中有隐含的功能来解决这个问题。而包含则是通过给你的模块和函数可以在其他类别被调用来解决这个问题。

如果这两种方案都能解决代码复用问题的话，哪一个更合适呢？答案是主观的，这看起来是令人难以相信的，但是我会给你 3 个指导性原则：

> 1.  不惜一切代价避免多重继承，因为它太复杂太不可靠。如果你必须要使用它，那么一定要知道类的层次结构，并花时间找到每一个类是从哪里来的。
> 2.  将代码封装为模块，这样就可以在许多不同的地方或情况使用。
> 3.  只有当有明显相关的可重用的代码，且在一个共同概念下时，可以使用继承。

不要变成规则的奴隶。关于面向对象编程要记住的是：这是一个程序员创建打包和共享代码的社会习俗。因为它是一个社会习俗，但在 Python 的法典中，你可能会因为跟你合作的人而被迫避开这些规则。在这种情况下，了解他们是如何使用规则的，然后去适应形势。

## 附加题

这节练习中只有一个附加题，因为这其实是一个很大的练习。阅读 `http://www.python.org/dev/peps/pep-0008/` 并尝试将它应用到你的代码中。你会发现，有些内容跟你从这本书学到的不同，但是现在你应该能够理解他们的建议，并将其应用到自己的代码中。本书中剩余部分的代码可能会也可能不会遵循这些准则，这个要取决于这些准则是否会使代码更加混乱。我建议你也这样做，因为理解比让大家都对你深奥的知识有印象更重要。

## 常见问题

### Q: 我如何更好的解决我以前没有遇到的问题？

> 更好的解决问题的办法只有一个，那就是尽量多的自己解决遇到的问题。通常，人们遇到一个棘手的问题，就会冲出去寻找答案。当你必须要把事情做好的时候，这种方法很好，但是如果你有时间的话，最好还是自己想办法解决这个问题。尽你所能的思考这个问题，尝试一切可能的办法，直到你解决这个问题。在此之后你找到的答案，你觉得会更加令人满意，而且你还会得到更好的解决问题的方法。

### Q: 对象不是复制的类吗？

> 在某些语言里(比如 JavaScript) 是这样的。这些被称为原型的语言，这些语言中对象和类没有什么不同之处。然而在 Python 中，类作为模板，可以生成新对象，类似于如何使用模具制造硬币。