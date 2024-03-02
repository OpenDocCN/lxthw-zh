# 练习 49\. 创建句子

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.54.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.54.learn-py3.md)

从我们这个小游戏的词汇扫描器中，我们应该可以得到类似下面的列表：

Exercise 49 Python 会话

```py
1.  `Python  3.6.0  (default,  Feb  2  2017,  12:48:29)`2.  `[GCC 4.2.1  Compatible  Apple LLVM 7.0.2  (clang-700.1.81)] on darwi Type  "help",  "copyright",  "credits"  or  "license"  for more information.`3.  `>>>  from ex48 import lexicon`4.  `>>> lexicon.scan("go north")`5.  `[('verb',  'go'),  ('direction',  'north')]`6.  `>>> lexicon.scan("kill the princess")`7.  `[('verb',  'kill'),  ('stop',  'the'),  ('noun',  'princess')]`8.  `>>> lexicon.scan("eat the bear")`9.  `[('verb',  'eat'),  ('stop',  'the'),  ('noun',  'bear')]`
```

以上对更长的句子也管用，比如：`lexicon.scan("open the door and smack the bear in the nose")`。

现在让我们把这个转换成游戏可以使用的东西，比如句子类（Sentence class）。不知你是否还记得小学时候学过一个句子的简单结构：

主语(Subject) + 谓语(动词 Verb) + 宾语(Object)

显然，实际的句子比这个复杂，你可能已经在英语语法课上被搞得头大。我们的目的，是将上面的元组列表转换为一个 Sentence 对象，而这个对象又包含主谓宾各个要素。

## 匹配和窥探（Peek）

为此我们需要四样工具：

*   循环访问元组列表的方法，这挺简单的。
*   匹配我们的主谓宾设置中不同种类元组的方法。
*   一个“窥视”潜在元组的方法，以便做决定时用到。
*   跳过(skip)我们不在乎的内容的方法，比如停用词（stop word）。
*   一个用以存放结果的句子类。我们要把这些函数放到一个叫做 `ex48.parser` 模块中（将文该件命名为 `ex48/parser.py`） ，以方便对其进行测试。我们使用 `peek` 函 数来执行“查看元组列表中的下一个元素，然后做匹配、取出来并进行处理”这一系列动作。

## 句子语法

在写代码之前，你需要先理解一下英语句子的基本语法。在我们的语法解析器（parser）中，我们想要产生一个包含三种属性的句子对象：

`Sentence.subject` 这是任何句子的主语，但是大多数时候可以默认为“玩家”（player），因为比如“run north”其实就是“player run north”。这应该是一个名词。

`Sentence.verb` 这是句子的动作。在“run north”中，就是“run”。这是一个动词。

`Sentence.object` 这是另一个名词，指的是动作所作用的对象（即宾语，object）。在我们的游戏中，我们所分的方向就是宾语。所以在“run north”里面，这个“north”就是宾语。在“hit bear”里面，“bear”就是宾语。

然后，我们的解析器需要使用我们所描述的函数，给出的扫描过的句子，把它转换成一列句子对象来和输入内容进行匹配。

## 关于异常

你已经简单学过一些关于异常的东西，但还没学过怎样“抛出”(raise)异常。这节的代码就演示了如何抛出前面定义的 `ParserError`。注意，系统用类来赋予异常的类型。另外还要注意我们是如何使用 raise 这个关键字来抛出异常的。

你的测试代码也应该要测试到这些异常，我随后会演示给你看如何实现。

## 解析器代码（The Parser Code）

如果你想要额外的挑战，现在就停下来，试着根据我的描述来写。如果遇到问题，你可以回来看看我是如何做的，但是尝试自己实现解析器是很好的实践。现在我会过一遍代码，以便你可以将其输入到 `ex48/parser.py` 中。我们以一个解析错误异常来开始我们的解析器：

parser.py

```py
1  class  ParserError(Exception):
2  pass
```

这也是你如何创建你自己的 `ParserError` exception 类的方法。下面，我们需要创建 Sentence object：

parser.py

```py
1  class  Sentence(object):
2
3  def __init__(self, subject, verb, obj):
4  # remember we take ('noun','princess') tuples and convert them.
5  self.subject = subject[1]
6  self.verb = verb[1]
7  self.object  = obj[1]
```

这些代码目前为止没什么特别的。你只是在创建简单的类。

**ai 酱注：** 接下来的这些函数不需要缩进，它们不是 Sentence 类下面的函数，而是独立的函数！

在我们的问题描述中，我们需要一个能够“窥探”一列单词并返回其类型的函数：

parser.py

```py
1  def peek(word_list):
2  if word_list:
3 word = word_list[0]
4  return word[0]
5  else:
6  return  None
```

我们之所以需要这个函数，是因为我们得基于下一个词是什么来判断我们正在处理的句子是什么类型。然后我们可以调用另一个函数来消灭（consume）那个字并往下进行。

要消灭一个单词，我们要用到 `match` 函数，这个函数可以确认当前单词是不是正确的类型，是的话就把它从列表中拿出来，然后返回这个单词。

parser.py

```py
1  def match(word_list, expecting):
2  if word_list:
3 word = word_list.pop(0)
4
5  if word[0]  == expecting:
6  return word
7  else:
8  return  None
9  else:
10  return  None
```

同样的，这个也非常简单，但是你要确保你能理解这些代码。还要确保你能理解我为什么要用这种方式来实现它。我需要窥探列表中的单词来决定我正在处理的句子是什么类型，然后我需要匹配这些单词来创建我的 Sentence。

我需要的最后一个东西是跳过对句子无用的单词的方法。这些单词被标记为“stop words” (type ’stop’) ，比如“the”、“and”、和“a”等。

parser.py

```py
1  def skip(word_list, word_type):
2  while peek(word_list)  == word_type:
3 match(word_list, word_type)
```

记住，skip 不只跳过一个单词，它会跳过所有它所找到的那个类型的单词。比如，如果有人输入 “scream at the bear”，你只会得到“scream”和“bear”这两个词。

这是我们解析函数的基本设定，有了这个函数，我们就可以解析任何我们想要解析的文本。这个解析器非常简单，所以剩余的函数也很简短。

首先，我们可以试着解析一个动词:

parser.py

```py
1  def parse_verb(word_list):
2 skip(word_list,  'stop')
3
4  if peek(word_list)  ==  'verb':
5  return match(word_list,  'verb')
6  else:
7  raise  ParserError("Expected a verb next.")
```

我们跳过了任何的 stop words，然后提前进行了窥探，确保下一个单词是“verb”（动词）类型。如果不是，就会抛出 `ParserError` 并说明原因。如果是“verb”，那就进行匹配，并把它从列表中拿出来。处理宾语的函数同理：

parser.py

```py
1  def parse_object(word_list):
2 skip(word_list,  'stop')
3 next_word = peek(word_list)
4
5  if next_word ==  'noun':
6  return match(word_list,  'noun')
7  elif next_word ==  'direction':
8  return match(word_list,  'direction')
9  else:
10  raise  ParserError("Expected a noun or direction next.")
```

同样地，跳过 stop words，先窥探，然后基于内容决定句子是否正确。尽管在 `parse_object` 函数中，我们需要同时处理“noun”（名词）和 “direction words”（方向词）作为可能的宾语。主语也是一样，但是因为我们想要用隐含的“player”名词，所以我们要这样用 peek：

parser.py

```py
1  def parse_subject(word_list):
2 skip(word_list,  'stop')
3 next_word = peek(word_list)
4
5  if next_word ==  'noun':
6  return match(word_list,  'noun')
7  elif next_word ==  'verb':
8  return  ('noun',  'player')
9  else:
10  raise  ParserError("Expected a verb next.")
```

这些都准备好了以后，我们最终的 `parse_sentence` 函数会非常简单：

parser.py

```py
1  def parse_sentence(word_list):
2 subj = parse_subject(word_list)
3 verb = parse_verb(word_list)
4 obj = parse_object(word_list)
5
6  return  Sentence(subj, verb, obj)
```

## 玩一玩解析器

要看这个如何运行，你可以这样做：

练习 49a Python 会话

```py
1.  `Python  3.6.0  (default,  Feb  2  2017,  12:48:29)`2.  `[GCC 4.2.1  Compatible  Apple LLVM 7.0.2  (clang-700.1.81)] on darwi Type  "help",  "copyright",  "credits"  or  "license"  for more informa`3.  `>>>  from ex48.parser import  *`4.  `>>> x = parse_sentence([('verb',  'run'),  ('direction',  'north')])`5.  `>>> x.subject`6.  `'player'`7.  `>>> x.verb`8.  `'run'`9.  `>>> x.object`10.  `'north'`11.  `>>> x = parse_sentence([('noun',  'bear'),  ('verb',  'eat'),  ('stop',  'the'),`12.  `...  ('noun',  'honey')])`13.  `>>> x.subject`14.  `'bear'`15.  `>>> x.verb`16.  `'eat'`17.  `>>> x.object`18.  `'honey'`
```

**ai 酱注：** 这里要先切换到 skeleton 目录，在运行 python，因为引入模块那里是从 ex48.parser 导入的，说明不能在 ex48 这个目录下运行。

试着把句子映射成句子中正确的对，比如，你会怎么说“the bear run south”？

## 你需要测试

对于练习 49，编写一个完整的测试，以确认代码中的所有内容都是有效的。把测试放在 `tests/parser_tests.py` 中，就像上个练习中的测试文件那样。还要试着给解析器错误的句子来产生异常。

通过使用 nose 文档中的 `assert_raise` 函数来检查异常。学习如何使用它，这样你就可以编写预期会失败的测试，这在测试中是非常重要的。通过阅读 nose 文档来了解这个功能（以及其他功能）。

完成之后，你应该知道这段代码是如何工作的，以及如何为其他人的代码写测试，即使他们不希望你这样做。相信我，这是一个非常有用的技能。

## 附加练习

*   改变 `parse_ methods`，试着把它们放到一个类中，而不是只当做方法来用。你更喜欢哪种设计？

*   提高 parser 对于错误输入的抵御能力，这样即使用户输入了你预定义语汇之外的词语，你的程序也能正常运行下去。

*   改进语法，让它可以处理更多的东西，例如数字。

*   想想在游戏里你的 Sentence 类可以对用户输入做哪些有趣的事情。

## 常见问题

**`assert_raises` 老是弄不对。** 确认你写成了 `assert_raises(exception, callable, parameters)` 而不 是 `assert_raises(exception, callable(parameters))` 。注意第二个格式，它所做的其实是将函数的返回值作为参数传到 `assert_raises` 中，这样做是错误的。你必须把函数和它的参数分别传入 `assert_raises` 中。