## 练习 23：入门列表

大多数编程语言都有一种将数据存储在计算机内部的方法。一些语言只有原始内存位置，但当情况如此时，程序员很容易犯错误。在现代语言中，你会得到一些核心的存储数据的方式，称为“数据结构”。数据结构将数据片段（整数、字符串，甚至其他数据结构）组织在一些有用的方式中。在这个练习中，我们将学习一种称为“`list`”或“`Array`”的序列式数据结构，具体取决于语言。

Python 最简单的序列数据结构是`list`，它是一组有序的事物。你可以随机访问`list`的元素，按顺序访问，扩展它，缩小它，以及对实际生活中的一系列事物做的几乎任何其他操作。

制作`list`的方法如下：

```py
1   fruit = ["apples", "oranges", "grapes"];
```

就是这样。只需在要放入`list`的事物周围加上`[`（左方括号）和`]`（右方括号），并用逗号分隔它们。你甚至可以将任何东西放入`list`中，甚至其他`lists`：

```py
1   inventory = [ ["Buick", 10], ["Corvette", 1], ["Toyota", 4]];
```

在这段代码中，我有一个`list`，而且这个`list`里面有三个`lists`。每个`list`里面都有一个汽车类型的名称和库存数量。仔细研究这个并确保你能够在阅读时将其分解。在其他数据结构中存储`lists`在`lists`内部是非常常见的。

### 访问列表的元素

如果你想要`inventory list`的第一个元素怎么办？那么你库存中有多少辆别克汽车呢？你可以这样做：

```py
1   # get the buick record
2   buicks = inventory[0]
3   buick_count = buicks[1]
4   # or in one move
5   count_of_buicks = inventory[0][1]
```

在注释之后的前两行代码中，我进行了一个两步过程。我使用`inventory[0]`代码来获取*第一个*元素。如果你不熟悉编程语言，大多数语言从 0 开始，而不是 1，因为在大多数情况下这样数学运算更好。在变量名后面紧跟`[]`告诉 Python 这是一个“容器”，并表示我们要“用这个值索引到这个东西中”，在这种情况下是 0。在下一行中，我取出`buicks[1]`元素，并从中获取`10`。

你不必这样做，因为你可以将`[]`的用法链接在一起，以便在进行深入研究`list`时逐步深入。在代码的最后一行中，我用`inventory[0][1]`来实现这一点，它的意思是“获取第 0 个元素，然后获取*那个*元素”。

这里是你可能会犯错误的地方。第二个`[1]`并不意味着获取整个`["Buick",` [rcurvearrowse] `10]`。它不是线性的，而是“递归”的，意味着它深入到结构中。你正在获取`["Buick",` [rcurvearrowse] `10]`中的`10`。更准确地说，它只是前两行代码的组合。

### 练习列表

列表足够简单，但你需要练习访问非常复杂`lists`的不同部分。重要的是，你能够*正确地*理解如何索引到嵌套`list`中的元素。最好的方法是在 Jupyter 中使用这样的`list`进行练习。

这段代码中我有一系列的`lists`。你需要像平常一样输入这段代码，然后使用 Python 访问元素，以便得到与我相同的答案。

### 代码

要完成这个挑战，你需要这段代码：

代码清单 23.1：ex23.py

```py
 1   fruit = [
 2       ['Apples', 12, 'AAA'], ['Oranges', 1, 'B'],
 3       ['Pears', 2, 'A'], ['Grapes', 14, 'UR']]
 4
 5   cars = [
 6       ['Cadillac', ['Black', 'Big', 34500]],
 7       ['Corvette', ['Red', 'Little', 1000000]],
 8       ['Ford', ['Blue', 'Medium', 1234]],
 9       ['BMW', ['White', 'Baby', 7890]]
10   ]
11
12   languages = [
13       ['Python', ['Slow', ['Terrible', 'Mush']]],
14       ['JavaSCript', ['Moderate', ['Alright', 'Bizarre']]],
15       ['Perl6', ['Moderate', ['Fun', 'Weird']]],
16       ['C', ['Fast', ['Annoying', 'Dangerous']]],
17       ['Forth', ['Fast', ['Fun', 'Difficult']]],
18   ]
```

可以复制粘贴这段代码，因为这个练习的重点是学习如何访问数据，但如果你想要额外练习输入 Python 代码，那么可以手动输入。

### 挑战

我会给你一个名为`list`的列表和列表中的一段数据。你的任务是找出你需要获取该信息的索引。例如，如果我告诉你`fruit 'AAA'`，那么你的答案是`fruit[0][2]`。你应该试着在脑海中通过查看代码来完成这个任务，然后在 Jupyter 中测试你的猜测。

#### 水果挑战

你需要从`fruit`变量中获取所有这些元素：

+   12

+   ‘AAA’

+   2

+   ‘橙子’

+   ‘葡萄’

+   14

+   ‘苹果’

#### 汽车挑战

你需要从`cars`变量中获取所有这些元素：

+   ‘大’

+   ‘红色’

+   1234

+   ‘白色’

+   7890

+   ‘黑色’

+   34500

+   ‘蓝色’

#### 语言挑战

你需要从`languages`变量中获取所有这些元素：

+   ‘缓慢’

+   ‘好的’

+   ‘危险’

+   ‘快速’

+   ‘困难’

+   ‘有趣’

+   ‘烦人’

+   ‘奇怪’

+   ‘适中’

### 最终挑战

现在你需要弄清楚这段代码拼出了什么：

```py
1   cars[1][1][1]
2   cars[1][1][0]
3   cars[1][0]
4   cars[3][1][1]
5   fruit[3][2]
6   languages[0][1][1][1]
7   fruit[2][1]
8   languages[3][1][0]
```

不要首先在 Jupyter 中运行这段代码。相反，尝试手动计算每行将拼出什么，然后在 Jupyter 中测试。
