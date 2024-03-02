# 练习 48\. 更复杂的用户输入

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.53.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.53.learn-py3.md)

在之前的游戏中，你通过设置特定的字符串来控制用户的输入。比如，只有用户输入“run”，而且得是精确的“run”，游戏才能正常运行。他们要是输入了类似的短语，比如“run fast”，程序都会报错。但我们需要的是一个能让用户通过多种方式来输入的设备，同时我们可以把用户输入的内容转换成计算机能理解的语言。比如，我们可以让下面这些短语同样生效：

• open door • open the door • go THROUGH the door • punch bear • Punch The Bear in the FACE

我们应该允许用户在游戏中输入一些自然语言，并且要让游戏能读懂这些语言的含义。要做到这一点，我们需要写一个专门的模块。这个模块会有几个类一起工作来处理用户输入，这些输入会被转换成你的游戏可以可靠处理的东西。

一个简化版本的英文语言会包含以下要素：

• 用空格隔开的单词。 • 由单词构成的句子。 • 组织句子并形成含义的语法。

这意味着最先解决的问题应该是如何从用户那里获得单词，并判断这些单词是什么类型。

## 我们的游戏词汇表（lexicon）

我们需要为这个游戏创建一列可以被接受的单词，我们把它称为“词汇表”（lexicon）：

• 方向词: north, south, east, west, down, up, left, right, back • 动词: go, stop, kill, eat • 停用词（stop word）: the, in, of, from, at, it • 名词: door, bear, princess, cabinet • 数词: any string of 0 through 9 characters（0-9 字符的任何字符串）

名词方面有一个小问题，因为每个房间都可以有几组不同的名词。所以我们先选一小组词，随后再进行改进。

### 48.1.1 拆解句子

有了词汇表之后，我们就需要找一种方法来拆解句子，这样我们才能知道它们是什么。在这个例子中，我们已经定义了句子由“被空格分隔的单词”所组成。所以，我们只需要这样做：

```py
stuff = input('> ')
words = stuff.split()
```

这就是我们现在为止要搞定的所有东西，不过这些也能管用好长一段时间。

### 48.1.2 词汇表元组（Lexicon Tuples）

知道了如何把一个句子分解成单词之后，我们只需要遍历这一列单词，并搞清楚它们是什么类型即可。要做到这一点我们需要用到一个非常有用的小 Python 结构：元组（tuple）。元组是一个你不能修改的列表。把数据放进两个 `()` 中，并像列表一样用逗号隔开，就能创建一个元组：

```py
first_word =  (  'verb '  ,  'go '  )
second_word =  (  ' direction '  ,  ' north '  )
third_word =  (  ' direct ion '  ,  ' west '  )
sentence =  [ first_word , second_word , third_word ]
```

这样就创建了一对 (类型, 单词) ，你可以看着单词来进行操作。

这只是一个例子，不过基本上也是最终结果。你从用户那里获得原始输入，将其分割成单词，再分析这些单词以确定它们的类型，最后，将它们组成一个句子。

### 48.1.3 扫描输入

现在你可以开始写你的扫描器（scanner）了。这个扫描器会从用户那里获取一个原始输入字符串，并返回一个由一列 (TOKEN, WORD) 元组对组成的句子。如果一个单词不是词汇表的一部分，那么它应该仍然返回该单词，但是将 TOKEN 设置为错误标记，从而告诉用户他们搞错了。

这块很有意思，但我不会告诉你怎么做。相反，我会写一个“单元测试”，你来写扫描器，来保证单元测试能够正常运行。

### 48.1.4 异常和数字

有个小地方我要先帮一下你，那就是数字的转换。不过，要做到这一点，我们需要先使用一下欺骗（cheat）和异常（exceptions）。异常是你运行一些函数的时候收到的错误情况。或者说，就是当函数遇到错误的时候，它会“抛出”（raise）一个异常，然后你需要处理这个异常。比如，如果你在 Python 里输入这个，你就会收到一个异常：

练习 48 Python 会话

```py
Python  3.6.0  (default,  Feb  2  2017,  12:48:29)
[GCC 4.2.1  Compatible  Apple LLVM 7.0.2  (clang-700.1.81)] on darwi Type  "help",  "copyright",  "credits"  or  "license"  for more information.
>>>  int("hell")
Traceback  (most recent call last):
File  "<stdin>", line 1,  in  <module>
ValueError: invalid literal for  int()  with  base  10:  'hell'
```

这个 `ValueError` 就是 `int()` 函数抛出来的一个异常，因为你放进 `int()` 里面的不是一个数字。这个 `int()` 函数本来应该给你返回一个值，告诉你它遇到了一个错误。但是，因为它只能返回整数，所以它很难直接告诉你。它不能返回 -1，因为这是一个数字。所以，与其绞尽脑汁地思考遇到错误的时候应该返回什么，`int()` 函数直接抛出了一个 `ValueError` 异常让你来处理。

你可以通过使用 try 和 except 关键词来处理异常：

ex48_convert.py

```py
1  def convert_number(s):
2  try:
3  return  int(s)
4  except  ValueError:
5  return  None
```

你把你想要 “try” 的代码放在 `try` 区域，然后把出现错误后要运行的代码放在 `except` 区域。在这个例子中，我们想要尝试对某个数字调用 `int()` 函数，如果出错了，我们“捕获”（catch）这个错误，然后返回 `None`。

在你写的扫描器里，你可以用这个函数来测试一个东西是不是数字，你还应该在声明一个单词是错误的之前，把这个作为最后一道检验来执行一下。

## 一个测试优先挑战

测试优先（Test first）是编写自动化测试时用到的一个编程策略，这个策略先假装你的代码能正常运行，然后你再去写代码，从而让这个测试能真正运行。当你无法可视化代码的实现过程，但是又能够想象出自己会如何做的时候，这种方法会很有效。比如，如果你知道如何在另一个模块中使用一个新类，但是你还不太知道如何实现这个类，那么你可以先写测试代码。

接下来，你要用我提供给你的一个测试来写代码，并让它正常运行。要完成这个练习，你需要遵循如下步骤：

*   先完成我给你的测试中的一小部分。
*   看它会正常运行还是会报错，这样你就能知道这个测试其实就是在确认一个特性能否正常运行。
*   在你的源文件 `lexicon.py` 里写代码，让这个测试能够运行通过。
*   重复这个过程直到你把测试中的所有东西都完全实现。当你到第三步的时候，也可以结合我们写代码的其他方法：

*   如果你需要的话，创建一些 “骨架” 函数或者类。

*   在其中写一些注释，解释函数是如何运行的。
*   把注释描述的东西用代码写出来。
*   移除和代码重复的注释。这种写代码的方法被称为“伪代码”（psuedo code），如果你不知道如何实现某些东西，但是可以用自己的话来描述它，那么这种方法就非常有效。

把“测试优先”和“伪代码”策略相结合，我们就有了这个编程的简要步骤：

*   写一些会失败的测试代码。
*   编写测试所需要的骨架函数/模块/类。
*   用自己的话通过注释来填充这些骨架，解释它是如何运行的。
*   用代码来替换注释，直到测试能运行通过。
*   重复。在这个练习中，你会通过我给你的测试，实现 `lexicon.py` 模块，来练习这个方法。

## 你需要测试

以下是你需要用到的测试用例 `tests/lexicon_tests.py`，但是先别输入：

lexicon_tests.py

```py
1  from nose.tools import  *
2  from ex48 import lexicon
3
4
5  def test_directions():
6 assert_equal(lexicon.scan("north"),  [('direction',  'north')])
7 result = lexicon.scan("north south east")
8 assert_equal(result,  [('direction',  'north'),
9  ('direction',  'south'),
10  ('direction',  'east')])
11
12  def test_verbs():
13 assert_equal(lexicon.scan("go"),  [('verb',  'go')])
14 result = lexicon.scan("go kill eat")
15 assert_equal(result,  [('verb',  'go'),
16  ('verb',  'kill'),
17  ('verb',  'eat')])
18
19
20  def test_stops():
21 assert_equal(lexicon.scan("the"),  [('stop',  'the')])
22 result = lexicon.scan("the in of")
23 assert_equal(result,  [('stop',  'the'),
24  ('stop',  'in'),
25  ('stop',  'of')])
26
27
28  def test_nouns():
29 assert_equal(lexicon.scan("bear"),  [('noun',  'bear')])
30 result = lexicon.scan("bear princess")
31 assert_equal(result,  [('noun',  'bear'),
32  ('noun',  'princess')])
33
34  def test_numbers():
35 assert_equal(lexicon.scan("1234"),  [('number',  1234)])
36 result = lexicon.scan("3 91234")
37 assert_equal(result,  [('number',  3),
38  ('number',  91234)])
39
40
41  def test_errors():
42 assert_equal(lexicon.scan("ASDFADFASDF"),
43  [('error',  'ASDFADFASDF')])
44 result = lexicon.scan("bear IAS princess")
45 assert_equal(result,  [('noun',  'bear'),
46  ('error',  'IAS'),
47  ('noun',  'princess')])
```

你可能想用这个项目骨架来创建一个新项目，就像练习 47 中一样。那么你需要创建这个测试用例，以及它所用的 lexicon.py 文件。看看这个测试用例的最上面，它是如何引入模块以及作何用途的。

接下来，按照我给你的步骤，编写这个测试的一部分。比如这是我所做的：

*   写出最上面的 import 部分，让它运行。
*   创建第一个测试用例 `test_directions` 的空版本，确保它能正常运行。
*   写出 `test_directions` 测试用例的第一行，让它运行失败。
*   然后去 `lexicon.py` 文件，创建一个空的 `scan` 函数。
*   运行测试，确保至少 `scan` 能成功运行，哪怕整体运行失败。
*   填入伪代码注释，解释 `scan` 如何工作，并让 `test_directions` 运行通过。
*   撰写与注释匹配的代码，直到 `test_directions` 运行通过。
*   回到 `test_directions` 并撰写余下各行。
*   回到 `lexicon.py` 的 `scan` 函数，撰写其内容，并让新的测试代码通过。
*   完成之后，你就有了你的第一个运行通过的测试，之后你就可以移步下一个测试。只要你依照这个步骤依次完成一小块，你就可以成功地把一个大问题分解成很多可以解决的小问题。这个过程就像把攀登一座高峰转化为跨越一座座小山。

## 附加练习

*   改进单元测试，确保你能测试更多的词汇表。
*   丰富词汇表，再更新单元测试。
*   确保你的扫描器能处理用户输入的大小写，更新测试，确保这一点能成功运行。
*   找找其他可以转化数字的方法。
*   我的解决方案有 37 行，你的更长还是更短呢？

## 常见问题

**为什么我一直收到 `ImportErrors`？** `ImportErrors` 通常由四种情况造成： 1\. 你没有在包含模块的目录中创建 `**init**.py`。 2\. 你处在错误的目录下。 3\. 你因为拼写错误引入了错误的模块。 4\. 你的 PYTHONPATH 没有设置到 `.`，所以你无法从当前目录加载模块。

**`try-except` 和 `if-else` 的区别是什么？** `try-expect` 仅用于处理异常，绝对不要将它作为 `if-else` 使用。

**有没有办法让游戏在等待用户输入的时候不间断地运行？** 我猜想你是想把游戏做得更高级，当用户反应过慢就被怪物杀死之类的。这个是可以做到，不过需要用到更高级的模块和编程技巧，本书不会涉及这些内容。