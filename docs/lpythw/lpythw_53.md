# 练习 49.写代码语句

# 练习 49.写代码语句

从这个小游戏的词汇扫描器中，我们应该可以得到类似下面的列表：

```py
python 2.7.1 (r271:86832, Jun 16 2011, 16:59:05) 
[GCC 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2335.15.00)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from ex48 import lexicon
>>> lexicon.scan("go north")
[('verb', 'go'), ('direction', 'north')]
>>> lexicon.scan("kill the princess")
[('verb', 'kill'), ('stop', 'the'), ('noun', 'princess')]
>>> lexicon.scan("eat the bear")
[('verb', 'eat'), ('stop', 'the'), ('noun', 'bear')]
>>> lexicon.scan("open the door and smack the bear in the nose")
[('error', 'open'), ('stop', 'the'), ('error', 'door'), ('error', 'and'), ('error', 'smack'), ('stop', 'the'), ('noun', 'bear'), ('stop', 'in'), ('stop', 'the'), ('error', 'nose')] 
```

现在让我们把它转化成游戏可以使用的东西，也就是一个`Sentence`类。

如果你还记得学校学过的东西的话，一个句子是由这样的结构组成的：主语(Subject) + 谓语(动词 Verb) + 宾语(Object)

很显然实际的句子可能会比这复杂，而你可能已经在英语的语法课上面被折腾得够呛了。我们的目的，是将上面的元组列表转换为一个`Sentence` 对象，而这个对象又包含主谓宾各个成员。

## 匹配(Match)和窥视(Peek)

为了达到这个效果，你需要四(五)样工具：

> 1.  循环访问元组列表的方法，这挺简单的。
> 2.  匹配我们的主谓宾设置中不同种类元组的方法。
> 3.  一个“窥视”潜在元组的方法，以便做决定时用到。
> 4.  跳过(skip)我们不在乎的内容的方法，例如形容词、冠词等没有用处的词汇。
> 5.  一个用来存放最终结果的`Sentence`对象

我们要把这些函数放在一个叫做`ex48.parser`的类中，再把这个类放在`ex48/parser.py`中，以便于我们能够测试它们。我们使用`peek`函数来查看元组列表中的下一个成员，做匹配以后再对它做下一步动作。

## 句子的语法

在你写代码之前，你要弄明白一个基础的英语句子的语法是如何工作的。在我们的练习中，我们准备创建一个叫做`Sentence`的类，它有如下 3 个属性：

Sentence.subject（句子的主语）这是任意一个句子的主语，大部分时候可以默认为“玩家 player”，比如一个句子“run north 向北跑”, 也就是说 "player run north 玩家向北跑"。主语应该是一个名词。

Sentence.verb（句子的谓语）这就是句子的的作用。 在 "run north" 中，谓语应该是 "run". 谓语应该是一个动词。

Sentence.object（句子的宾语） 这又是一个名词，指的是动词做了什么。在我们游戏中， 我们分辨出的方向就是宾语。在 "run north" 中，单词"north"就是宾语。在 "hit bear" 中，单词"bear" 就是宾语。

我们的程序解析器使用我们给出的函数并返回解析后的句子，转换成一个`list`或`Sentence`对象，用来接收匹配用户输入

## 关于异常(Exception)

已经简单学过关于异常的一些东西，但还没学过怎样抛出(raise)它们。这节的代码演示了如何 raise 前面定义的`ParserError`。注意`ParserError` 是一个定义为`Exception` 类型的 class。另外要注意我们是怎样使用`raise` 这个关键字来抛出异常的。

你的测试代码应该也要测试到这些异常，这个我也会演示给你如何实现。

## 程序代码

如果你希望更大的挑战，停在这里，然后只听我的描述来完成代码。当你遇到难题的时候，可以再回来看看是我如何做的。不过，尝试自己实现代码功能对你来说真的是个很好的锻炼。我要开始串讲我的代码了，你可以开始在自己的`ex48/parser.py`中输入代码。我们从异常处理开始我们的代码编写：

```py
class ParserError(Exception):
    pass 
```

这就是你创建一个可以抛出的异常类`ParserError`,接下来，我们需要一个句子类 `Sentence`：

```py
class Sentence(object):

    def __init__(self, subject, verb, obj):
        # remember we take ('noun','princess') tuples and convert them
        self.subject = subject[1]
        self.verb = verb[1]
        self.object = obj[1] 
```

到目前为止，我们没有写什么特别的代码，只是创建了两个简单的类。

在我们的问题描述中，我们需要一个函数用来看到列表中的单词并返回单词的类型：

```py
def peek(word_list):
    if word_list:
        word = word_list[0]
        return word[0]
    else:
        return None 
```

我们需要这个函数是因为，我们要基于下一个单词来选择确认我们要处理的句子是什么，然后我们可以调用另一个函数来处理这个单词，并将程序继续下去。

我们使用`match`函数来处理单词，用它来确认预期中的单词是否是正确的类型，将它移出列表，并返回该词：

```py
def match(word_list, expecting):
    if word_list:
        word = word_list.pop(0)

        if word[0] == expecting:
            return word
        else:
            return None
    else:
        return None 
```

相当简单是不是，不过还是要确认你理解了这些代码以及为什么我是这么写的。我需要依据我看到的列表中的下一个单词来决定我现在处理的句子的类型，然后再用这个单词创建我的`Sentence`.

最后，我们需要一个方法来跳过句子中我们不关心的单词。这些单词会被打上“停用词”（stop 类型的词）的标签，比如"the","and"以及"a"等：

```py
def skip(word_list, word_type):
    while peek(word_list) == word_type:
        match(word_list, word_type) 
```

记住`skip`不只跳过一个单词而是跳过所有该类型的词，也就是说，如果有人输入了“scream at the bear”，经过处理最后会得到"scream" 和 "bear".

以上是我们分析函数的基本结构，我可以用它们来处理我们需要的任何文本，尽管我们的程序非常简单，剩下的函数也都是非常短的。

首先，我们来完成解析动词的部分：

```py
def parse_verb(word_list):
    skip(word_list, 'stop')

    if peek(word_list) == 'verb':
        return match(word_list, 'verb')
    else:
        raise ParserError("Expected a verb next.") 
```

我们跳过所有"stop"类型的词，然后提前获得下一个单词，并确认它是"verb"类型，如果不是，则抛出一个异常`ParserError`说明为什么不是。如果是"verb"类型，则使用"match"处理，将它移出列表。一个处理"sentence"类的类似函数：

```py
def parse_object(word_list):
    skip(word_list, 'stop')
    next_word = peek(word_list)

    if next_word == 'noun':
        return match(word_list, 'noun')
    elif next_word == 'direction':
        return match(word_list, 'direction')
    else:
        raise ParserError("Expected a noun or direction next.") 
```

重复操作，跳过"stop"类型的词，提前判断下一个词，决定下一个"sentence".在函数`parse_object`中，我们需要同时处理“名词”和类似宾语的“方向”，解析主语的方法也是一样的，但是当我们处理隐藏的名词"player"的时候，我们需要用到"peek"：

```py
def parse_subject(word_list):
    skip(word_list, 'stop')
    next_word = peek(word_list)

    if next_word == 'noun':
        return match(word_list, 'noun')
    elif next_word == 'verb':
        return ('noun', 'player')
    else:
        raise ParserError("Expected a verb next.") 
```

所有的方式都准备好之后，我们最后一个函数`parse_sentence`也是非常简单的：

```py
def parse_sentence(word_list):
    subj = parse_subject(word_list)
    verb = parse_verb(word_list)
    obj = parse_object(word_list)

    return Sentence(subj, verb, obj) 
```

## 试玩这个游戏

为了弄明白程序是如何运行，你可以像这样试玩：

```py
Python 2.7.1 (r271:86832, Jun 16 2011, 16:59:05) 
[GCC 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2335.15.00)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from ex48.parser import *
>>> x = parse_sentence([('verb', 'run'), ('direction', 'north')])
>>> x.subject
'player'
>>> x.verb
'run'
>>> x.object
'north'
>>> x = parse_sentence([('noun', 'bear'), ('verb', 'eat'), ('stop', 'the'), ('noun', 'honey')])
>>> x.subject
'bear'
>>> x.verb
'eat'
>>> x.object
'honey' 
```

## 你应该测试的东西

为《习题 49》写一个完整的测试方案，确认代码中所有的东西都能正常工作，把测试代码放到文件`tests/parser_tests.py`中，测试代码中也要包含对异常的测试——输入一个错误的句子它会抛出一个异常来。

使用`assert_raises`这个函数来检查异常，在 `nose` 的文档里查看相关的内容，学着使用它写针对“执行失败”的测试，这也是测试很重要的一个方面。从`nose`文档中学会`assert_raises`以及一些别的函数的使用方法。

写完测试以后，你应该就明白了这段程序的工作原理，而且也学会了如何为别人的程序写测试代码。 相信我，这是一个非常有用的技能。

## 附加题

> 1.  修改 `parse_`函数（方法），将它们放到一个类里边，而不仅仅是独立的方法函数。这两种程序设计你喜欢哪一种呢？
> 2.  提高 `parser`的容错能力，这样即使用户输入了你预定义语汇之外的词语，你的程序也能正常运行下去。
> 3.  改进语法，让它可以处理更多的东西，例如数字。
> 4.  想想在游戏里你的`Sentence`类可以对用户输入做哪些有趣的事情。

## 常见问题

### Q: 我好像不能让`assert_raises`正常运行

> 确认你写的是`assert_raises(exception, callable, parameters)`而不是`assert_raises(exception, callable(parameters))`。注意一下第二种写法中，调用了函数`callable`并将返回值传递给`assert_raises`，这种写法是错误的，你应该把要调用的函数也作为参数传递给`assert_raises`。