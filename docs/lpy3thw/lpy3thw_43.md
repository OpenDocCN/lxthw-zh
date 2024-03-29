# 练习 39 字典，可爱的字典

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.44.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.44.learn-py3.md)

现在你要学习 Python 中的另一种数据结构——字典（Dictionary）。字典（也叫 dict）是一种和列表类似的数据存储方式。但是不同于列表只能用数字获取数据，字典可以用任何东西来获取。你可以把字典当成是一个存储和组织数据的数据库。

让我们比较一下列表和字典的作用。你看，列表可以让你做这些事情：

练习 39 Python 会话

```py
>>> things =  ['a',  'b',  'c',  'd']
>>>  print(things[1])
b
>>> things[1]  =  'z'
>>>  print(things[1])
z
>>> things
['a',  'z',  'c',  'd']
```

你可以用数字来索引列表，找到列表里面有些什么。到现在你应该能够理解这一点。但是你还要确保自己明白，你只能用数字来取出列表中的元素。

相比之下，字典能让你用几乎所有的东西，而不只是数字。是的，字典能够把一个东西和另一个东西关联起来，不管它们是什么类型。我们来看看：

练习 39 Python 会话

```py
>>> stuff =  {'name':  'Zed',  'age':  39,  'height':  6  *  12  +  2}
>>>  print(stuff['name'])
Zed
>>>  print(stuff['age'])
39
>>>  print(stuff['height'])
74
>>> stuff['city']  =  "SF"
>>>  print(stuff['city'])
SF
```

你会看到我们用了字符串（而不是数字）来从 stuff 字典中取出了我们想要的东西。我们也可以用字符串来给字典添加新的东西。而且，也可以不用字符串，我们可以这样做：

练习 39 Python 会话

```py
>>> stuff[1]  =  "Wow"
>>> stuff[2]  =  "Neato"
>>>  print(stuff[1])
Wow
>>>  print(stuff[2])
Neato
```

在这一段代码中我用了数字，所以你看，我在打印字典的时候既可以用数字也可以用字符串来作为键。我可以用任何东西。好吧，大多数东西，不过你现在就假装能够用任何东西吧。

当然，如果一个字典只能放东西那就太蠢了。下面是如何用 'del' 关键词来删除其中的东西：

练习 39 Python 会话

```py
>>>  del stuff['city']
>>>  del stuff[1]
>>>  del stuff[2]
>>> stuff
{'name':  'Zed',  'age':  39,  'height':  74}
```

## 一个字典示例

接下来我们要做一个练习，你必须非常仔细，我要求你将这个练习写下来，然后试着弄懂它做了些什么。当你把东西放进字典、随意取出、以及做其他操作的时候记得做一下笔记。

注意一下这个例子是如何把州名和它们的缩写以及州的缩写和城市映射（mapping）起来的，记住，“映射”或者说“关联”（associate）是字典的核心理念。

ex39.py

```py
1  # create a mapping of state to abbreviation
2 states =  {
3  'Oregon':  'OR',
4  'Florida':  'FL',
5  'California':  'CA',
6  'New York':  'NY',
7  'Michigan':  'MI'
8  }
9
10  # create a basic set of states and some cities in them
11 cities =  {
12  'CA':  'San Francisco',
13  'MI':  'Detroit',
14  'FL':  'Jacksonville'
15  }
16
17  # add some more cities
18 cities['NY']  =  'New York'
19 cities['OR']  =  'Portland'
20
21  # print out some cities
22  print('-'  *  10)
23  print("NY State has: ", cities['NY'])
24  print("OR State has: ", cities['OR'])
25
26  # print some states
27  print('-'  *  10)
28  print("Michigan's abbreviation is: ", states['Michigan'])
29  print("Florida's abbreviation is: ", states['Florida'])
30
31  # do it by using the state then cities dict
32  print('-'  *  10)
33  print("Michigan has: ", cities[states['Michigan']])
34  print("Florida has: ", cities[states['Florida']])
35
36  # print every state abbreviation
37  print('-'  *  10)
38  for state, abbrev in list(states.items()):
39  print(f"{state} is abbreviated {abbrev}")
40
41  # print every city in state
42  print('-'  *  10)
43  for abbrev, city in list(cities.items()):
44  print(f"{abbrev} has the city {city}")
45
46  # now do both at the same time
47  print('-'  *  10)
48  for state, abbrev in list(states.items()):
49  print(f"{state} state is abbreviated {abbrev}")
50  print(f"and has city {cities[abbrev]}")
51
52  print('-'  *  10)
53  # safely get a abbreviation by state that might not be there
54 state = states.get('Texas')
55
56  if  not state:
57  print("Sorry, no Texas.")
58
59  # get a city with a default value
60 city = cities.get('TX',  'Does Not Exist')
61  print(f"The city for the state 'TX' is: {city}")
```

## 你会看到

练习 39 会话

```py
$ python3.6 ex39.py

NY State has: New York
OR State has: Portland
----------
Michigan's abbreviation is: MI
Florida's abbreviation is: FL
----------
Michigan has: Detroit
Florida has: Jacksonville
----------
Oregon is abbreviated OR
Florida is abbreviated FL
California is abbreviated CA
New York is abbreviated NY
 Michigan is abbreviated MI
----------
CA has the city San Francisco
MI has the city Detroit
FL has the city Jacksonville
NY has the city New York
OR has the city Portland
----------
Oregon state is abbreviated OR
and has city Portland
Florida state is abbreviated FL
and has city Jacksonville
California state is abbreviated CA
and has city San Francisco
New York state is abbreviated NY
and has city New York
Michigan state is abbreviated MI
and has city Detroit` 
----------
Sorry, no Texas.The city for the state 'TX' is: Does Not Exist
```

## 字典能做什么

字典是另一种数据结构的例子，在编程中和列表一样常用。字典是用来把你想要存储的东西映射或关联到一些键（keys），以便你能够获取到它们。同样的，程序员们不会用“字典”这个词来指代跟现实生活中的字典没有关系的东西。所以，让我们来看一个现实世界的例子。

假设你想查查“Honorificabilitudinitatibus”这个词的意思。现在你只需要把这个词复制粘贴到一个搜索引擎就能得到答案。可以说搜索引擎就像一个超级复杂版本的牛津英语字典。在没有搜索引擎之前，你可能会这么做：

*   去图书馆找到一本字典，让我们假设你要找牛津字典。
*   你知道“honorificabilitudinitatibus”以字母 H 开头，所以你在书的侧边找那个小小的 H 。
*   然后你在 H 部分翻页寻找直到接近以“hon”开头的单词。
*   继续翻了几页之后你终于找到了“honorificabilitudinitatibus”，或者你已经翻到以“hp”开头的单词了，你才意识到牛津字典里根本没有这个词。
*   一旦你找到了这个词，你会看看它的定义，以弄明白它的意思。这个过程基本上就是字典的工作原理，你把“honorificabilitudinitatibus”这个词映射到它的定义上。而 Python 中的字典和现实世界中的牛津字典非常类似。

## 附加练习

*   给你所在的国家或其他国家建立城市和州/地区的类似映射。
*   找找 Python 的字典文档，试试多进行一些操作。
*   看看你不能用字典做什么。很重要的一点是它们没有次序，试着玩玩看。

## 常见问题

**列表和字典有哪些区别?** 列表是元素的有序排列。而字典是把一些元素（称为“键”，keys）和另一些元素（称为“值”，values）匹配起来。

**我能用字典做什么？** 当你需要用一个东西去查另一个东西的时候。其实，你可以把字典称为“查询表”（look up tables）。

**我能用列表做什么？** 可以用于任何有序排列的东西，同时你只需要用数字索引来查找它们。

**如果我需要一个字典，但我又想让它们有序排列怎么办呢？** 去看看 Python 中的 collections.OrderedDict 数据结构。可以在网上找找相关文档。