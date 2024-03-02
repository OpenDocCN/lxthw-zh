## 练习 24：初级字典

在这个练习中，我们将使用前一个练习中的相同数据来学习字典或 dicts。

### 键/值结构

你经常在不知不觉中使用`key=value`数据。当你阅读一封电子邮件时，你可能会有：

```py
1   From: j.smith@example.com
2   To: zed.shaw@example.com
3   Subject: I HAVE AN AMAZING INVESTMENT FOR YOU!!!
```

左边是键（From，To，Subject），它们与右边的`:`后的内容*映射*在一起。程序员说键被“映射”到值，但他们也可以说“设置为”，比如，“我将`From`设置为`j.smith@example.com`”。在 Python 中，我可能会使用一个数据对象来写这封电子邮件：

```py
1   email = {
2       "From": "j.smith@example.com",
3       "To": "zed.shaw@example.com",
4       "Subject": "I HAVE AN AMAZING INVESTMENT FOR YOU!!!"
5   };
```

通过以下方式创建数据对象：

1.  用`{`（大括号）打开它

2.  写入键，这里是一个字符串，但可以是数字，或几乎任何东西

3.  写入一个`:`（冒号）

4.  写入值，可以是 Python 中有效的任何内容

一旦你这样做，你可以像这样访问这封 Python 电子邮件：

```py
1   email["From"]
2   'j.smith@example.com'
3
4   email["To"]
5   'zed.shaw@example.com'
6
7   email["Subject"]
8   'I HAVE AN AMAZING INVESTMENT FOR YOU!!!'
```

你会注意到这与你访问模块中的变量和函数的方式非常相似，你需要`require`。使用`.`（点）是你可以访问 Python 中许多数据结构部分的主要方式。你也可以使用前一个练习中的`[]`语法来访问这些数据：

```py
1   email['To']
2   'zed.shaw@example.com'
3
4   email['From']
5   'j.smith@example.com'
```

与`list`索引的唯一区别是你使用字符串（'From'）而不是整数。但是，如果你愿意，你也可以使用整数作为键（后面会详细介绍）。

### 将列表与数据对象结合

编程中的一个常见主题是将组件组合以获得令人惊讶的结果。有时惊喜是崩溃或错误。其他时候，惊喜是一种新颖的完成某项任务的方式。无论如何，当你进行新颖的组合时发生了什么并不是真正的惊喜或秘密。对于*你*来说可能是惊喜的，但语言规范中通常会有一个解释（即使这个原因绝对愚蠢）。你的计算机中没有魔法，只有你不理解的复杂性。

将数据对象放入`lists`中的一个很好的例子。你可以这样做：

```py
1   messages = [
2     {to: 'Sun', from: 'Moon', message: 'Hi!'},
3     {to: 'Moon', from: 'Sun', message: 'What do you want Sun?'},
4     {to: 'Sun', from: 'Moon', message: "I'm awake!"},
5     {to: 'Moon', from: 'Sun', message: 'I can see that Sun.'}
6   ];
```

一旦我这样做了，我现在可以使用`list`语法来访问数据对象，就像这样：

```py
 1   messages[0].to
 2   'Sun'
 3
 4   messages[0].from
 5   'Moon'
 6   messages[0].message
 7   'Hi!'
 8
 9   messages[1]['to']
10   'Moon'
11
12   messages[1]['from']
13   'Sun'
14
15   messages[1]['message']
16   'What do you want Sun?'
```

注意我在`messages[0]`后面立即使用`.`（点）语法的方式？再次尝试结合功能，看看它们是否有效，如果有效，找出原因，因为总会有一个原因（即使它很愚蠢）。

### 代码

现在，你将重复使用`lists`的练习，并写出我精心制作的三个数据对象。然后，你将把它们输入到 Python 中，并尝试访问我给你的数据。记得尝试在脑海中完成这个任务，然后用 Python 检查你的工作。你还应该练习对`list`和`dict`结构进行这样的操作，直到你有信心可以访问内容。你会意识到数据是相同的，只是被重新构造了。

列表 24.1: ex24.py

```py
 1   fruit = [
 2       {kind: 'Apples',  count: 12, rating: 'AAA'},
 3       {kind: 'Oranges', count: 1,  rating: 'B'},
 4       {kind: 'Pears',   count: 2,  rating: 'A'},
 5       {kind: 'Grapes',  count: 14, rating: 'UR'}
 6   ];
 7
 8   cars = [
 9       {type: 'Cadillac', color: 'Black', size: 'Big', miles: 34500},
10       {type: 'Corvette', color: 'Red', size: 'Little', miles: 1000000},
11       {type: 'Ford', color: 'Blue', size: 'Medium', miles: 1234},
12       {type: 'BMW', color: 'White', size: 'Baby', miles: 7890}
13   ];
14
15   languages = [
16       {name: 'Python', speed: 'Slow', opinion: ['Terrible', 'Mush']},
17       {name: 'JavaScript', speed: 'Moderate', opinion: ['Alright', 'Bizarre'
         ↪] ]},
18       {name: 'Perl6', speed: 'Moderate', opinion: ['Fun', 'Weird']},
19       {name: 'C', speed: 'Fast', opinion: ['Annoying', 'Dangerous']},
20       {name: 'Forth', speed: 'Fast', opinion: ['Fun', 'Difficult']},
21   ];
```

### 你应该看到的结果

请记住，你在这里进行了一些复杂的数据访问操作，所以要慢慢来。你必须遍历你分配给模块的`data`变量，然后访问`lists`，接着是数据对象，有时还有另一个`list`。

### 挑战

我会给你完全相同的数据元素集，你需要找出获取这些信息所需的索引。例如，如果我告诉你`fruit 'AAA'`，那么你的答案是`fruit[0].rating`。你应该试着在脑海中通过查看代码来做到这一点，然后在`python` shell 中测试你的猜测。

#### 水果挑战

你需要从`fruit`变量中取出所有这些元素：

+   12

+   ‘AAA’

+   2

+   ‘橙子’

+   ‘葡萄’

+   14

+   ‘苹果’

#### 汽车挑战

你需要从`cars`变量中取出所有这些元素：

+   ‘大的’

+   ‘红色的’

+   1234

+   ‘白色的’

+   7890

+   ‘黑色的’

+   34500

+   ‘蓝色的’

#### 语言挑战

你需要从`languages`变量中取出所有这些元素：

+   ‘慢的’

+   ‘好的’

+   ‘危险的’

+   ‘快的’

+   ‘困难的’

+   ‘有趣的’

+   ‘烦人的’

+   ‘奇怪的’

+   ‘适度的’

### 最终挑战

你的最终挑战是编写出写出与练习 23 中相同歌词的 Python 代码。再次慢慢来，试着在脑海中完成再看看你是否做对了。如果你做错了，花时间理解为什么错了。作为对比，我在脑海中一次性写出了歌词，没有出错。我也比你有更多经验，所以你可能会犯一些错误，那也没关系。

你不知道这些是歌词吗？这是一首由王子演唱的歌曲叫做“Little Red Corvette”。在继续阅读本书之前，你现在被命令听 10 首王子的歌曲，否则我们就不能再做朋友了。再也不能！
