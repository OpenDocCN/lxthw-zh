# 练习 39.字典,可爱的字典

# 练习 39.字典,可爱的字典

接下来我要教你另外一种让你伤脑筋的容器型数据结构，因为一旦你学会这种容器，你将拥有超酷的能力。这是最有用的容器：字典(dictionary)。

Python 将这种数据类型叫做 “dict”，有的语言里它的名称是 “hash”。这两种名字我都会用到，不过这并不重要，重要的是它们和列表的区别。你看，针对列表你可以做这样的事情：

```py
>>> things = ['a', 'b', 'c', 'd']
>>> print things[1]
b
>>> things[1] = 'z'
>>> print things[1]
z
>>> things
['a', 'z', 'c', 'd'] 
```

你可以使用数字作为列表的索引，也就是你可以通过数字找到列表中的元素。你现在应该了解列表的这些特性，而你也应了解，你也只能通过数字来获取列表中的元素。

而 dict 所作的，是让你可以通过任何东西找到元素，不只是数字。是的，字典可以将一个物件和另外一个东西关联，不管它们的类型是什么，我们来看看：

```py
>>> stuff = {'name': 'Zed', 'age': 39, 'height': 6 * 12 + 2}
>>> print stuff['name']
Zed
>>> print stuff['age']
39
>>> print stuff['height']
74
>>> stuff['city'] = "San Francisco"
>>> print stuff['city']
San Francisco 
```

你将看到除了通过数字以外，我们还可以用字符串来从字典中获取 stuff ，我们还可以用字符串来往字典中添加元素。当然它支持的不只有字符串，我们还可以做这样的事情：

```py
>>> stuff[1] = "Wow"
>>> stuff[2] = "Neato"
>>> print stuff[1]
Wow
>>> print stuff[2]
Neato
>>> stuff
{'city': 'San Francisco', 2: 'Neato', 'name': 'Zed', 1: 'Wow', 'age': 39, 'height': 74} 
```

在这段代码中，我使用了数字，当我打印 stuff 的时候，你可以看到，不止有数字还有字符串作为字典的 key。事实上，我可以使用任何东西，这么说并不准确，不过你先这么理解就行了。

当然了，一个只能放东西进去的字典是没啥意思的，所以我们还要有删除的方法，也就是使用`del` 这个关键字：

```py
>>> del stuff['city']
>>> del stuff[1]
>>> del stuff[2]
>>> stuff
{'name': 'Zed', 'age': 36, 'height': 74} 
```

## 一个字典实例

接下来我们要做一个练习，你必须非常仔细，我要求你将这个练习写下来，然后试着弄懂它做了些什么。注意一下这个例子中是如何对应这些州和它们的缩写，以及这些缩写对应的州里的城市。 记住, "映射" 是字典中的关键概念.

```py
# create a mapping of state to abbreviation
states = {
    'Oregon': 'OR',
    'Florida': 'FL',
    'California': 'CA',
    'New York': 'NY',
    'Michigan': 'MI'
}

# create a basic set of states and some cities in them
cities = {
    'CA': 'San Francisco',
    'MI': 'Detroit',
    'FL': 'Jacksonville'
}

# add some more cities
cities['NY'] = 'New York'
cities['OR'] = 'Portland'

# print out some cities
print '-' * 10
print "NY State has: ", cities['NY']
print "OR State has: ", cities['OR']

# print some states
print '-' * 10
print "Michigan's abbreviation is: ", states['Michigan']
print "Florida's abbreviation is: ", states['Florida']

# do it by using the state then cities dict
print '-' * 10
print "Michigan has: ", cities[states['Michigan']]
print "Florida has: ", cities[states['Florida']]

# print every state abbreviation
print '-' * 10
for state, abbrev in states.items():
    print "%s is abbreviated %s" % (state, abbrev)

# print every city in state
print '-' * 10
for abbrev, city in cities.items():
    print "%s has the city %s" % (abbrev, city)

# now do both at the same time
print '-' * 10
for state, abbrev in states.items():
    print "%s state is abbreviated %s and has city %s" % (
        state, abbrev, cities[abbrev])

print '-' * 10
# safely get a abbreviation by state that might not be there
state = states.get('Texas')

if not state:
    print "Sorry, no Texas."

# get a city with a default value
city = cities.get('TX', 'Does Not Exist')
print "The city for the state 'TX' is: %s" % city 
```

## 你看到的结果

```py
$ python ex39.py
----------
NY State has:  New York
OR State has:  Portland
----------
Michigan's abbreviation is:  MI
Florida's abbreviation is:  FL
----------
Michigan has:  Detroit
Florida has:  Jacksonville
----------
California is abbreviated CA
Michigan is abbreviated MI
New York is abbreviated NY
Florida is abbreviated FL
Oregon is abbreviated OR
----------
FL has the city Jacksonville
CA has the city San Francisco
MI has the city Detroit
OR has the city Portland
NY has the city New York
----------
California state is abbreviated CA and has city San Francisco
Michigan state is abbreviated MI and has city Detroit
New York state is abbreviated NY and has city New York
Florida state is abbreviated FL and has city Jacksonville
Oregon state is abbreviated OR and has city Portland
----------
Sorry, no Texas.
The city for the state 'TX' is: Does Not Exist 
```

## 字典能做什么

字典是另一个数据结构的例子，和列表一样，是编程中最常用的数据结构之一。 字典是用来做映射或者存储你需要的键值对，这样当你需要的时候，你可以通过 key 来获取它的值。同样，程序员不会使用一个像“字典”这样的术语，来称呼那些不能像一个写满词汇的真实字典正常使用的事物，所以我们只要把它当做真实世界中的字典来用就好。

假如你想知道这个单词"Honorificabilitudinitatibus"的意思。你可以很简单的把它复制粘贴放进任何一个搜索引擎中找到答案。我们真的可以说一个搜索引擎就像一个巨大的超级复杂版本的《牛津英语词典》(OED).在搜索引擎出现之前，你可能会这样做：

> 1.  走进图书馆，找到一本字典，我们称这本字典为 OED
> 2.  你知道单词"honorificabilitudinitatibus" 以字母 'H'开头，所以你查看字典的小标签，找到以 'H' 开头的部分.
> 3.  然后你会浏览书页，直到找到"hon"开头的地方。
> 4.  然后你再翻过一些书页，直到找到 "honorificabilitudinitatibus" 或者找到以 "hp" 开头的单词，发现这个词不在我们的字典中。
> 5.  当你找到这个条目，你就可以仔细阅读并弄明白它的意思。

这个过程跟我们在程序中使用字典的是相似的，你会映射（"mapping"）找到这个单词"honorificabilitudinitatibus"的定义。Python 中的字典就跟真实世界中的这本牛津词典（OED）差不多。

## 定义自己的字典类

这节练习的最后一段代码给你演示了如何使用你刚学会的 list 来创建一个字典数据结构。这段代码可能有些难以理解，所以如果你要花费你很长的时间去弄明白代码额含义也不要担心。代码中会有一些新的知识点，它确实有些复杂，还有一些事情需要你上网查找

为了使用 Python 中的`dict`保存数据，我打算把我的数据结构叫做`hashmap`,这是字典数据结构的另一个名字。你要把下面的代码输入一个叫做`hashmap.py`的文件，这样我们就可以在另一个文件 `ex39_test.py`中执行它。

```py
def new(num_buckets=256):
    """Initializes a Map with the given number of buckets."""
    aMap = []
    for i in range(0, num_buckets):
        aMap.append([])
    return aMap

def hash_key(aMap, key):
    """Given a key this will create a number and then convert it to
    an index for the aMap's buckets."""
    return hash(key) % len(aMap)

def get_bucket(aMap, key):
    """Given a key, find the bucket where it would go."""
    bucket_id = hash_key(aMap, key)
    return aMap[bucket_id]

def get_slot(aMap, key, default=None):
    """
    Returns the index, key, and value of a slot found in a bucket.
    Returns -1, key, and default (None if not set) when not found.
    """
    bucket = get_bucket(aMap, key)

    for i, kv in enumerate(bucket):
        k, v = kv
        if key == k:
            return i, k, v

    return -1, key, default

def get(aMap, key, default=None):
    """Gets the value in a bucket for the given key, or the default."""
    i, k, v = get_slot(aMap, key, default=default)
    return v

def set(aMap, key, value):
    """Sets the key to the value, replacing any existing value."""
    bucket = get_bucket(aMap, key)
    i, k, v = get_slot(aMap, key)

    if i >= 0:
        # the key exists, replace it
        bucket[i] = (key, value)
    else:
        # the key does not, append to create it
        bucket.append((key, value))

def delete(aMap, key):
    """Deletes the given key from the Map."""
    bucket = get_bucket(aMap, key)

    for i in xrange(len(bucket)):
        k, v = bucket[i]
        if key == k:
            del bucket[i]
            break

def list(aMap):
    """Prints out what's in the Map."""
    for bucket in aMap:
        if bucket:
            for k, v in bucket:
                print k, v 
```

上面的代码创建了一个叫做`hashmap`的模块，你需要把这个模块 import 到文件 `ex39_test.py` 中，并让这个文件运行起来：

```py
import hashmap

# create a mapping of state to abbreviation
states = hashmap.new()
hashmap.set(states, 'Oregon', 'OR')
hashmap.set(states, 'Florida', 'FL')
hashmap.set(states, 'California', 'CA')
hashmap.set(states, 'New York', 'NY')
hashmap.set(states, 'Michigan', 'MI')

# create a basic set of states and some cities in them
cities = hashmap.new()
hashmap.set(cities, 'CA', 'San Francisco')
hashmap.set(cities, 'MI', 'Detroit')
hashmap.set(cities, 'FL', 'Jacksonville')

# add some more cities
hashmap.set(cities, 'NY', 'New York')
hashmap.set(cities, 'OR', 'Portland')

# print out some cities
print '-' * 10
print "NY State has: %s" % hashmap.get(cities, 'NY')
print "OR State has: %s" % hashmap.get(cities, 'OR')

# print some states
print '-' * 10
print "Michigan's abbreviation is: %s" % hashmap.get(states, 'Michigan')
print "Florida's abbreviation is: %s" % hashmap.get(states, 'Florida')

# do it by using the state then cities dict
print '-' * 10
print "Michigan has: %s" % hashmap.get(cities, hashmap.get(states, 'Michigan'))
print "Florida has: %s" % hashmap.get(cities, hashmap.get(states, 'Florida'))

# print every state abbreviation
print '-' * 10
hashmap.list(states)

# print every city in state
print '-' * 10
hashmap.list(cities)

print '-' * 10
state = hashmap.get(states, 'Texas')

if not state:
  print "Sorry, no Texas."

# default values using ||= with the nil result
# can you do this on one line?
city = hashmap.get(cities, 'TX', 'Does Not Exist')
print "The city for the state 'TX' is: %s" % city 
```

你应该发现这段代码跟我们在这节开始时写的代码几乎相同，除了它使用了你新实现的 HashMap。通读代码并且确信你明白这段代码中的每一行是如何与`ex39.py`中的代码实现相同的功能。

## 代码分析

这个 `hashmap` 只不过是"拥有键值对的有插槽的列表"，用几分钟时间分析一下我说的意思：

"一个列表"在 `hashmap` 函数中，我创建了一个列表变量`aMap`，并且用其他的列表填充了这个变量。"有插槽的列表"最开始这个列表是空的,当我给这个数据结构添加键值对之后，它就会填充一些插槽或者其他的东西"拥有键值对"表示这个列表中的每个插槽都包含一个`(key, value)`这样的元素或者数据对。

如果我的这个描述仍旧没让你弄明白是什么意思，花点时间在纸上画一画它们，直到你搞明白为止。实际上，手动在纸上运算是让你弄明白它们的好办法。

你现在知道数据是如何被组织起来的，你还需要知道它每个操作的算法。算法指的是你做什么事情的步骤。它是是数据结构运行起来的代码。我们接下来要逐个分析下代码中用到的操作， 下面是在 `hashmap`算法中一个通用的模式：

> 1.  把一个关键字转换成整数使用哈希函数: `hash_key`.
> 2.  Convert this hash to a bucket number using a `%`(模除) 操作.
> 3.  Get this bucket from the `aMap` list of buckets, and then traverse it to find the slot that contains the key we want.

操作`set` 实现以下功能,如果 key 值存在，则替换原有的值，不存在则创建一个新值。

下面我们逐个函数分析一下 hashmap 的代码，让你明白它是如何工作的。 跟我一起分析并确保你明白每一行代码的意思。给每一行加上注释，确保你明白他们是做什么的。就是如此简单，我建议你对下面提到的每一行代码都花点时间在 Python shell 或者纸上多练习练习:

new 首先，我以创建一个函数来生成一个 hashmap 开始，也被称为初始化。 我先创建一个包含列表的变量，叫做`aMap`,然后把列表`num_buckets`放进去， `num_buckets`用来存放我给 hashmap 设置的内容。 后面我会在另一个函数中使用`len(aMap)` 来查找一共有多少个 buckets。确信你明白我说的。

hash_key 这个看似简单的函数是一个 dict 如何工作的核心。它是用 Python 内建的哈希函数将字符串转换为数字。Python 为自己的字典数据结构使用此功能，而我只是复用它. 你应该启动一个 Python 控制台，看看它是如何工作的. 当我拿到 key 对应的数字的时候, 我使用 `%` (模除) 操作和 `len(aMap)` 来获得一个放置这个 key 的位置。你应该知道，`%` (模除) 操作将会返回除法操作的余数。我也可以使用这个方法来限制大数，将其固为较小的一组数字。如果你不知道我在说什么，使用 Python 解析器研究一下。

get_bucket 这个函数使用`hash_key`来找到一个 key 所在的“bucket”。当我在`hash_key`函数中进行`%len(aMap)`操作的时候，我知道无论我获得哪一个 `bucket_id`都会填充进 `aMap` 列表中. 使用 `bucket_id` 可以找到一个 key 所在的“bucket” 。

get_slot 这个函数使用`get_bucket`来获得一个 key 所在的“bucket”， 它通过查找 bucket 中的每一个元素来找到对应的 key。找到对应的 key 之后，它会返回这样一个元组`(i, k, v)`，i 表示的是 key 的索引值，k 就是 key 本身，v 是 key 对应的值。你现在已经了解了足够字典数据结构运行的原理。它通过 keys、哈希值和模量找到一个 bucket，然后搜索这个 bucket，找到对应的条目。它有效的减少了搜索次数。

get 这是一个人们需要`hashmap`的最方便的函数。它使用`get_slot`来获得 元组`(i, k, v)` 但是只返回`v`. 确定你明白这些默认变量是如何运行的，以及`get_slot`中`(i, k, v)` 分派给`i`, `k`, `v`的变量是如何获得的。

set 设置一个`key/value`键值对，并将其追加到字典中，保证以后再用到的时候可以获取的到。但是，我希望我的`hashmap`每个 key 值存储一次。为了做到这点， 首先，我要找到这个 key 是不是已经存在，如果存在，我会替换它原来的值，如果不存在，则会追加进来。这样做会比简单的追加慢一些，但是更满足`hashmap`使用者的期望。如果你允许一个 key 有多个 value，你需要使用 `get`方法查阅所有的“bucket”并返回一个所有 value 的列表。这是平衡设计的一个很好的例子。现在的版本是你可以更快速的 `get`, 但是会慢一些 `set`.

delete 删除一个 key, 找到 key 对应的 bucket，并将其从列表中删除。因为我选择一个 key 只能对应一个 value，当我找到一个相应的 key 的时候，我就可以停止继续查找和删除。如果我选择允许一个 key 可以对应多个 value 的话，我的删除操作也会慢一些，因为我要找到所有 key 对应的 value，并将其删除。

list 最后的功能仅仅是一个小小的调试功能，它能打印出`hashmap` 中的所有东西，并且能帮助你理解字典的细微之处。

在所有的函数之后，我有一点点的测试代码，可以确保他们正常工作。

## 三级列表

正如我在讨论中提到的， 由于我选择 `set` 来重写 (替换) 原有的 keys，这会让`set`执行的慢一些，但是这决定能让其他的一些函数快一些。如果我想要一个`hashmap`允许一个 key 对应多个 value，但又要求所有函数仍然执行的很快，怎么办

我要做的就是让每个“bucket”中的插槽的值都是一个列表。这意味着我要给字典再增加第三级列表。这种`hashmap`仍然满足字典的定义。我说过， "每一个 key 可以有对个 value"的另一种说法就是"每一个 key 有一个 value 的列表"。

## 你应该看到的结果（again）

```py
$ python ex39_test.py
Traceback (most recent call last):
  File "ex39_test.py", line 1, in <module>
    import hashmap
ImportError: No module named hashmap 
```

## 什么时候选择字典，什么时候选择列表

如同我在练习 38 中提到的，列出有特定的特性，帮助你控制和组织需要放在表结构的东西。 字典也一样，但是`dict`的特性是与列表不同的，因为他们是用键值对映射来工作的。当遇到下面情况的时候，可以使用字典：

> 1.  你要检索的东西是以一些标识为基础的，比如名字、地址或其他一切可以作为 key 的东西。
> 2.  你不需要这些东西是有序的。词典通常不会有序的概念，所以你必须使用一个列表。
> 3.  你想要通过 key 增删一个元素。

也就是说，如果你要用一个非数字的 key，使用`dict`，如果你需要有序的东西，使用`list`.

## 附加题

> 1.  用自己国家的州和城市做一些类似的映射关系
> 2.  在 Python 文档中找到 dictionary 的相关的内容，学着对 dict 做更多的操作。
> 3.  找出一些 dict 无法做到的事情。例如比较重要的一个就是 dict 的内容是无序的，你可以检查一下看看是否真是这样。
> 4.  阅读 python 的关于断言的功能，然后修改 hashmap 的代码，给每一个测试增加一些断言相关的代码，替换原来的打印代码。比如，你可以断言第一个操作返回"Flamenco Sketches" 而不是直接打印出"Flamenco Sketches" 。
> 5.  有没有注意到`list`方法没有按照你增加元素的顺序把它们列出来？这是字典不维持秩序的一个例子，如果你将代码进行分析，你就会明白为什么。
> 6.  像写`list`方法一样写一个`dump`方法，实现备份字典内所有内容的功能
> 7.  确定你知道`hash`在代码中实现了什么功能，它是一个特殊的函数，能将字符串转化为整数。在网上找到相关文档，了解在程序设计中，什么是哈希函数。

## 常见问题

### Q：字典和列表的区别？

> list 是一个有序的项目列表，dict 是匹配一些项目（称为“键”）和其他项目（称为“值”）。

### Q: 我怎样使用字典？

> 当你需要通过一个值来访问另一个值的时候，使用字典。实际上，你可以把字典称作“对照表”

### Q: 我怎样使用列表？

> 对任何需要有序的事情集合使用列表，你只需要通过他们的数值索引来访问它们。

### Q:加入我需要一个字典，但是又需要是有序的，怎么办？

> 看看 python 中`collections.OrderedDict`这个数据结构。网上搜索相关的文档。