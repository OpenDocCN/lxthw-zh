# 练习 41 学着去说面向对象

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.46.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.46.learn-py3.md)

在这个练习中，我要教你如何去说“面向对象”。我所做的就是给你一些你需要了解的词和定义。然后我会给出一些需要填空的句子让你去理解。最后，你要完成一个大练习，从而在大脑中巩固这些句子。

## 词汇训练

（注：为了方便理解，定义保留英文原文。）

**类（class）** ：告诉 Python 创建一个新类型的东西（Tell Python to make a new type of thing）。

**对象（object）**两种含义：最基本类型的东西, 任何实例。（the most basic type of thing, and any instance of something.）

**实例（instance）** ：当你告诉 Python 创建一个类的时候你所得到的东西。（What you get when you tell Python to create a class.）

**def** ：你如何在类里面定义一个函数。（How you define a function inside a class.）

**self** ：在一个类的函数里面，self 是被访问的实例/对象的一个变量。（Inside the functions in a class, self is a variable for the instance/object being accessed.）

**继承（inheritance）** ：关于一个类能从另一个类那里继承它的特征的概念，很像你和你的父母。（The concept that one class can inherit traits from another class, much like you and your parents.）

**组合（composition）** ：关于一个类可以由其他一些类构成的概念, 很像一辆车包含几个轮子。（The concept that a class can be composed of other classes as parts, much like how a car has wheels.）

**属性（attribute）** ：类所拥有的从组合那里得到的特性，通常是变量。（A property classes have that are from composition and are usually variables.）

**is-a** ：一种用来表达某物继承自一种东西的表述, 就像“三文鱼是一种鱼”。（A phrase to say that something inherits from another, as in a “salmon” is a “fish.”）

**has-a** ：一种用来表达某物是由一些东西组成或具有某种特性的表述，就像“三文鱼有一个嘴巴”。（A phrase to say that something is composed of other things or has a trait, as in “a salmon has-a mouth.”）

花点时间为这些术语做一些闪词卡（flash cards）并记住它们，虽然在你完成这个练习之前单纯的记忆没有任何意义，但你必须要先了解这些基础的词汇。

## 短语训练

接下来是一些 Python 代码片段以及右边的解释。

**`class X(Y)`** ： 创建一个名为 X 并继承自 Y 的类。 (“Make a class named X that is-a Y.”)

**`class X(object): def **init**(self, J)`**类 X 有一个带有 self 和 J 参数的 `**init**` 函数。 (“class X has-a `**init**` that takes self and J parameters.”)

**`class X(object): def M(self, J)`**： 类 X 有一个带有 self 和 J 参数的 M 函数。 (“class X has-a function named M that takes self and J parameters.”)

**`foo = X()`**： 设 foo 为类 X 的一个实例。 (“Set foo to an instance of class X.”)

**`foo.M(J)`**从 foo 那里获取 M 函数，并用 self 和 J 参数来调用它。 (“From foo, get the M function, and call it with parameters self, J.”)

**`foo.K = Q`**从 foo 那里获取 K 属性，并设它为 Q。 (“From foo, get the K attribute, and set it to Q.”)

在上述每一句中，当你看到 X, Y, M, J, K, Q, 以及 foo, 你可以把它们当做空格，比如，我还可以把这些句子写成：

*   “Make a class named ??? that is-a Y.” （创建一个名为 ??? 的类，它继承自 Y。）

*   “class ??? has-a `**init**` that takes self and ??? parameters.” （类 ??? 有一个带了 self 和 ??? 参数的 `**init**`。）

*   “class ??? has-a function named ??? that takes self and ??? parameters.” （类 ??? 有一个名为 ??? 的函数，这个函数带有 self 和 ??? 两个参数。）

*   “Set foo to an instance of class ???.” （设 foo 为类 ??? 的一个实例。）

*   “From foo, get the ??? function, and call it with self=??? and parameters ???.” （从 foo 那里获取 ??? 函数，并用 `self=???` 以及参数 ??? 来调用它。）

*   “From foo, get the ??? attribute, and set it to ???.” （从 foo 那里获取 ??? 属性，把它设为 ???。）

同样地，把这些短语写到一些闪词卡上，然后记一记。把 Python 代码片段放在正面，解释的句子放在背面，你必须每次都正确说出每一个短语的意思。不是说得类似就行，而是要一模一样。

## 综合训练

最后一项准备工作是把词汇训练和短语训练结合在一起，以下是训练内容：

*   做一个短语卡然后练习记忆。

*   把它翻过来，读句子，如果在句子中看到词汇训练中的词汇，就找到相应的词汇卡片。

*   练习记忆这些词汇卡片。

*   坚持练习，要是你感到有些累，就休息一下再继续。

## 一个阅读测试

现在我有一个小的 Python 脚本来帮助你掌握这些词汇和短语，并且能够无限运行。这段脚本很简单，你应该能够看明白，它所做的事情就是用一个叫做 urllib 的图书馆来下载一列单词。以下是脚本代码，你需要输入到 oop_test.py 这个文件里来使用：

ex41.py

```py
1  import random
2  from urllib.request import urlopen
3  import sys
4
5 WORD_URL =  "http://learncodethehardway.org/words.txt"
6 WORDS =  []
7
8 PHRASES =  {
9  "class %%%(%%%):":
10  "Make a class named %%% that is-a %%%.",
11  "class %%%(object):\n\tdef __init__(self, ***)"  :
12  "class %%% has-a __init__ that takes self and *** params.",
13  "class %%%(object):\n\tdef ***(self, @@@)":
14  "class %%% has-a function *** that takes self and @@@ params.",
15  "*** = %%%()":
16  "Set *** to an instance of class %%%.",
17  "***.***(@@@)":
18  "From *** get the *** function, call it with params self @@@.",
19  "***.*** = '***'":
20  "From *** get the *** attribute and set it to '***'."
21  }
22
23  # do they want to drill phrases first
24  if len(sys.argv)  ==  2  and sys.argv[1]  ==  "english":
25 PHRASE_FIRST =  True
26  else:
27 PHRASE_FIRST =  False
28
29  # load up the words from the website
30  for word in urlopen(WORD_URL).readlines():
31 WORDS.append(str(word.strip(), encoding="utf-8"))
32
33
34  def convert(snippet, phrase):
35 class_names =  [w.capitalize()  for w in
36 random.sample(WORDS, snippet.count("%%%"))]
37 other_names = random.sample(WORDS, snippet.count("***"))
38 results =  []
39 param_names =  []
40
41  for i in range(0, snippet.count("@@@")):
42 param_count = random.randint(1,3)
43 param_names.append(', '.join(
44 random.sample(WORDS, param_count)))
45
46  for sentence in snippet, phrase:
47 result = sentence[:]
48
49  # fake class names
50  for word in class_names:
51 result = result.replace("%%%", word,  1)
52
53  # fake other names
54  for word in other_names:
55 result = result.replace("***", word,  1)
56
57  # fake parameter lists
58  for word in param_names:
59 result = result.replace("@@@", word,  1)
60
61 results.append(result)
62
63  return results
64
65
66  # keep going until they hit CTRL-D
67  try:
68  while  True:
69 snippets = list(PHRASES.keys())
70 random.shuffle(snippets)
71
72  for snippet in snippets:
73 phrase = PHRASES[snippet]
74 question, answer = convert(snippet, phrase)
75  if PHRASE_FIRST:
76 question, answer = answer, question
77
78  print(question)
79
80 input("> ")
81  print(f"ANSWER: {answer}\n\n")
82  except  EOFError:
83  print("\nBye")
```

运行这个脚本，试着用“面向对象的短语”来把它翻译成自然语言，你应该能看到短语字典有两种形式，你只用输入正确的那个就行。

## 练习从自然语言到代码

接下来你应该选择用“english”选项来运行这段代码，然后用相反的方式来练习：

```py
$ python oop_test.py english
```

记住，这些短语在用一些废话，学习阅读这些代码的一部分原因就是试着不再去给这些变量和类的名字赋予这么多意义。通常当人们看到像“cork”（软木塞）这样的词时，会对它的含义感到很困惑。在上述例子中，“cork”只是一个随机选取的类的名字。别给它赋予太多含义，而是试着用我教你的方式来对待它。

## 读更多代码

你现在需要继续读更多的代码，并在这些代码中复习你之前学过的短语。试着找到尽可能多的包含类的文件，然后跟着如下要求去做：

*   给出每个类的名字，以及其他的类从它那里继承了什么。

*   在每个类下面，列出它所拥有的函数以及它们的参数。

*   列出所有它用 self 使用的属性。

*   对于每个属性，给出它继承自哪个类。

这些练习的目的是过一遍真实的代码，并试着把你学过的短语和它们的用法匹配和关联起来。如果你做足了训练，你会开始看到这些匹配模式（match patterns）呼之欲出，而不再是一些你不明白的空格或字符。

## 常见问题

**`result = sentence[:]` 是干什么用的？** 这是 Python 复制一个列表的方式。它用的是列表的切片（slice）语法 `[:]`，能够很快地创建一个从第一个元素到最后一个元素的列表切片。

**这个脚本好难运行！** 到目前为止你应该能够让它正常运行。虽然它确实有几个小地方比较烦人，但是并不复杂。试着用你目前为止所学过的东西来调试它。把每一行输入进去，并且确保和我的一模一样，然后遇到不明白的地方就在网上查查。

**还是很难！** 你可以这样做。慢点敲，一个字符一个字符地敲，但是要保证准确，然后弄明白每个词的意思。