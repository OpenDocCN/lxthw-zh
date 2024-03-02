# 练习 42\. Is-A, Has-A, 对象和类

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.47.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.47.learn-py3.md)

你必须理解类和对象的区别，这是一个很重要的概念。不过问题是，类和对象之间没有什么真正的区别。它们在不同的时间点其实是同一种东西，我会用禅宗（Zen koan）来解释这一点：

## 鱼和三文鱼的区别是什么？

这个问题会让你困惑吗？坐下来认真想一分钟，我是说，鱼和三文鱼的确是有区别的，但是它们是同一种东西，对吧？三文鱼是鱼的一种，所以我说它们没什么区别。但是同时，三文鱼只是一种特定种类的鱼，它肯定不同于其他种类的鱼。三文鱼是三文鱼，而不是比目鱼。所以三文鱼和鱼是同一种东西，但是又有区别。

这个问题很令人困惑，因为大多数人不会这么去思考真实的东西，但是大家直觉上又能理解。你不需要去想鱼和三文鱼的具体区别是什么，因为你知道它们是相关的。你知道三文鱼是一种鱼，而且还有其他种类的鱼我们不用去理解。

让我们更进一步。假设你有一个水桶装了三条三文鱼，由于你是一个好人，你决定给它们三个起个名字，分别叫 Frank、Joe 和 Mary。现在想想这个问题：

## Mary 和三文鱼的区别是什么？

这也是一个很奇怪的问题。但是它好像比鱼和三文鱼的问题要简单一点。你知道 Mary 是一条三文鱼，所以她真的不一样，她只是三文鱼的一个“实例”。 Joe 和 Frank 也是三文鱼的实例。当我说“实例”的时候我指的是什么？ 我是指它们由其他三文鱼创造而来，但是现在代表了一个具有三文鱼属性的真实存在的东西。

现在回到这个让人伤脑筋的问题：鱼是一个类，三文鱼也是一个类，而 Mary 是一个对象。想几秒钟，让我们拆开来讲，看你是否理解了。

鱼是一个类，意味着它不是一个真正的东西，而是一个我们用来给具有相似属性的实例归类的词，理解了吗？比如有鳍，有鳃，生活在水里，好吧，那可能是鱼。

可能会有位 Ph.D. 跑过来说，“不，年轻人，这鱼其实是大西洋鲑，人们喜欢叫它三文鱼。”这位教授只是更详细地澄清了一下，同时创建了一个叫做“三文鱼”的新类，它有一些更特别的属性。鼻子很长，肉呈淡红色， 体型大，生活在淡水里，很好吃？那可能是三文鱼。

最后，一位厨师跑过来告诉这位 Ph.D.，“不，你看这条三文鱼，我叫她 Mary，我等会儿要用她做一道很好吃的生鱼片。” 现在你有了一个叫做 Mary 的三文鱼实例（也是鱼的实例），她是真实存在的，能填饱你的肚子。她已经变成了一个对象。

现在你明白了：Mary 是一种三文鱼，三文鱼是一种鱼。对象一种类，类是另一种类。

## 代码怎么写

这是个很奇怪的概念，不过说实话，你只用在你创建新类和使用类的时候才用担心它。我会教你两个识别一个东西是类还是对象的小技巧。

首先，你需要学习两个信号词：“is-a”（是…）和“has-a”（有…）。当你表达对象和类的相互关系时，你用“is-a”。当你指对象和类相互引用时，你用“has-a”。

现在，过一遍这些代码，然后把 `##??` 替换为注释，说明下一行代表了 is-a 还是 has-a 的关系，以及是什么关系。我在代码最开始已经列出了一些示例，你需要完成剩余的部分。

记住，is-a 指的是鱼和三文鱼之间的关系，has-a 指的是三文鱼和鳃的关系。

ex42.py

```py
1  ## Animal is-a object (yes, sort of confusing) look at the extra credit（附加练习）
2  class  Animal(object):
3  pass
4
5  ## ??
6  class  Dog(Animal):
7
8  def __init__(self, name):
9  ## ??
10  self.name = name
11
12  ## ??
13  class  Cat(Animal):
14
15  def __init__(self, name):
16  ## ??
17  self.name = name
18
19  ## ??
20  class  Person(object):
21
22  def __init__(self, name):
23  ## ??
24  self.name = name
25
26  ## Person has-a pet of some kind
27  self.pet =  None
28
29  ## ??
30  class  Employee(Person):
31
32  def __init__(self, name, salary):
33  ## ?? hmm what is this strange magic?
34  super(Employee,  self).__init__(name)
35  ## ??
36  self.salary = salary
37
38  ## ??
39  class  Fish(object):
40  pass
41 
42  ## ??
43  class  Salmon(Fish):
44  pass
45 
46  ## ??
47  class  Halibut(Fish):
48  pass
49 
50 
51  ## rover is-a Dog
52 rover =  Dog("Rover")
53 
54  ## ??
55 satan =  Cat("Satan")
56 
57  ## ??
58 mary =  Person("Mary")
59 
60  ## ??
61 mary.pet = satan
62 
63  ## ??
64 frank =  Employee("Frank",  120000)
65 
66  ## ??
67 frank.pet = rover
68 
69  ## ??
70 flipper =  Fish()
71 
72  ## ??
73 crouse =  Salmon()
74 
75  ## ??
76 harry =  Halibut()
```

## 关于 类名(object)

我一直强迫你使用 `类名(object)`，但一直没跟你解释为什么要这样用。刚才你已经学了类和对象的区别，现在我就可以告诉你原因了。因为如果我早告诉你的话，你可能会晕掉，也就学不会这门技术了。

真正的原因是在 Python 早期，它对于类的定义在很多方面都是严重有问题的。当他们承认这一点的时候已经太迟了，所以逼不得已，他们需要支持这种有问题的类。为了解决已有的问题，他们需要引入一种“新类”，这样的话“旧类”还能继续使用，而你也有一个新的正确的类可以使用了。

这就用到了“类即是对象”的概念。他们决定用小写的“object”这个词作为一个类，让你在创建新类时从它继承下来。有点晕吧？一个类继承自另一个类，而后者虽然是个类，名字却叫“object”。不过在定义类的时候，别忘记要从 object 继承就好了。

的确如此。一个词的不同就让这个概念变得更难理解，让我不得不现在才讲给你。现在你可以试着去理解“一个是对象的类”这个概念了，如果你感兴趣的话。

不过我还是建议你别去理解了，干脆完全忘记旧格式和新格式类的区别吧，就假设 Python 的类永远都要求你加上 `(object)` 好了，你的脑力要留着思考更重要的问题。

## 附加练习

*   研究一下为什么 Python 添加了这个奇怪的叫做 object 的类，它究竟有什么含义呢？
*   有没有可能把一个类当作对象来使用呢？
*   在习题中为 animals、fish、还有 people 添加一些函数，让它们做一些事情。看看当函数在 Animal 这样的“基类(base class)”里和在 Dog 里有什么区别。
*   找找别人的代码，弄明白里面的 is-a 和 has-a 的关系。
*   使用列表和字典创建一些新的一对多的“has-many”的关系。
*   你认为会有一种“has-many”的关系吗？阅读一下关于“多重继承(multiple inheritance)”的资料，然后尽量避免这种用法。

## 常见问题

**这些 `## ??` 注释是做什么的？** 这些是一些注释的填空，你需要在那里填上正确的 “is-a”或“has-a” 的概念。把这个练习再读一遍，看看其他的注释，你就明白我的意思了。

**`self.pet = None`有什么意义？** 这样确保 `self.pet` 这个类的属性被设为默认的 None。

**`super(Employee, self).**init**(name)` 是干什么的？** 这是你运行父类的 **init** 方法的一种可靠方式。搜索一下 “python3.6 super”，读读那些对你有利有弊的各种建议。