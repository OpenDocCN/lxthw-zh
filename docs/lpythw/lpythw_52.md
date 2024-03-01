# 练习 48.更复杂的用户输入

# 练习 48.更复杂的用户输入

在以前的游戏中，你只是设置一些简单的预定义字符串作为用户输入处理，用户输入“run”，程序能正常运行，但是你输入“run fast”，程序就会运行失败。我们需要一个设备，它可以识别用户以各种方式输入的语汇。例如下面的机种表述都应该被支持才对：

> *   open door
> *   open the door
> *   go THROUGH the door
> *   punch bear
> *   Punch The Bear in the FACE

也就是说，如果用户的输入和常用英语很接近也应该是可以的，而你的游戏要识别出它们的意思。为了达到这个目的，我们将写一个模块专门做这件事情。这个模组里边会有若干个类，它们互相配合，接受用户输入，并且将用户输入转换成你的游戏可以识别的命令。

英语的简单格式是这个样子的：

> *   单词由空格隔开。
> *   句子由单词组成。
> *   语法控制句子的含义。

以最好的开始方式是先搞定如何得到用户输入的词汇，并判断出它们是什么。

## 我们的游戏词典

我在游戏里创建了下面这些语汇：

> *   表示方向: north, south, east, west, down, up, left, right, back.
> *   动词: go, stop, kill, eat.
> *   修饰词: the, in, of, from, at, it
> *   名词: door, bear, princess, cabinet.
> *   数字: 由 0-9 构成的数字。

说到名词，我们会碰到一个小问题，那就是不一样的房间会用到不一样的一组名词，不过让我们先挑一小组出来写程序，以后再做改进。

## 如何断句

我们已经有了词汇表，为了分析句子的意思，接下来我们需要找到一个断句的方法。我们对于句子的定义是“空格隔开的单词”，所以只要这样就可以了：

```py
stuff = raw_input('> ')
words = stuff.split() 
```

目前做到这样就可以了，不过这招在相当一段时间内都不会有问题。

## 词汇元组

一旦我们知道了如何将句子转化成词汇列表，剩下的就是逐一检查这些词汇，看它们是什么类型。为了达到这个目的，我们将用到一个非常好使的 Python 数据结构，叫做”元组(tuple)”。元组其实就是一个不能修改的列表。创建它的方法和创建列表差不多，成员之间需要用逗号隔开，不过方括号要换成圆括号 `()`：

```py
first_word = ('verb', 'go')
second_word = ('direction', 'north')
third_word = ('direction', 'west')
sentence = [first_word, second_word, third_word] 
```

这样我们就创建了一个(TYPE,WORD)组，让你识别出单词，并且对它执行指令。

这只是一个例子，不过最后做出来的样子也差不多。你接受用户输入，用 `split`将其分隔成单词列表，然后分析这些单词，识别它们的类型，最后重新组成一个句子。

## 扫描输入

现在你要写的是词汇扫描器。这个扫描器会将用户的输入字符串当做参数，然后返回由多个 (TOKEN, WORD) 组成的一个列表，这个列表实现类似句子的功能。如果一个单词不在预定的词汇表中，那它返回时 WORD 应该还在，但 TOKEN 应该设置成一个专门的错误标记。这个错误标记将告诉用户哪里出错了。

有趣的地方来了。我不会告诉你这些该怎样做，但我会写一个“单元测试(unit test)”，而你要把扫描器写出来，并保证单元测试能够正常通过。

## 异常和数字

有一件小事情我会先帮帮你，那就是数字转换。为了做到这一点，我们会作一点弊，使用“异常(exceptions)”来做。“异常”指的是你运行某个函数时得到的错误。你的函数在碰到错误时，就会“抛出(raise)”一个“异常”，然后你就要去处理(handle)这个异常。假如你在 Python 里写了这些东西：

```py
Python 2.7.1 (r271:86832, Jun 16 2011, 16:59:05) 
[GCC 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2335.15.00)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> int("hell")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'hell' 
```

这个`ValueError`就是`int()`函数抛出的一个异常。因为你给`int()` 的参数不是一个数字。`int()`函数其实也可以返回一个值来告诉你它碰到了错误，不过由于它只能返回整数值，所以很难做到这一点。它不能返回 -1，因为这也是一个数字。`int()`没有纠结在它“究竟应该返回什么”上面，而是提出了一个叫做`ValueError`的异常，然后你只要处理这个异常就可以了。

处理异常的方法是使用`try`和`except`这两个关键字：

```py
def convert_number(s):
    try:
        return int(s)
    except ValueError:
        return None 
```

你把要试着运行的代码放到`try`的区段里，再将出错后要运行的代码放到 `except`区段里。在这里，我们要试着调用`int()` 去处理某个可能是数字的东西，如果中间出了错，我们就抓到这个错误，然后返回`None`。

在你写的扫描器里面，你应该使用这个函数来测试某个东西是不是数字。做完这个检查，你就可以声明这个单词是一个错误单词了。

## 测试第一的挑战

测试首先是一种编程策略，你先写一段自动化测试代码，假装代码是在正常运行的，然后你再写出代码保证测试代码能正常运行。这种方法用在当你不知道代码是如何运行，但又可以想象必须使用它的时候。比如说，如果你知道你需要在另一个模块中使用一个新类,但是你不太知道如何实现这个类，那么先写出测试程序。

我将给你一份测试代码，你需要写出代码，保证测试代码能正常工作。为了完成这个任务，你可以看看下面的流程：

> 1.  创建一小部分我给你的测试代码
> 2.  确保它运行失败,你知道测试实际上是确认功能的工作原理。
> 3.  到你的源代码文件`lexicon.py`中，写出能使测试代码通过的代码
> 4.  重复以上工作直到你实现测试中的所有点

当你做到 3 的时候，和其他编写代码的方法相结合也是很好的方法：

> 1.  编写你需要的函数或类的基本框架
> 2.  添加注释，解释说明这个函数是如何运行的
> 3.  按照描述中的注释写代码
> 4.  去掉注释

这种写代码的方法被称作“psuedo code”，用在你不知道该如何实现某些功能，但是会用自己的语言来描述这个功能的时候。

结合“test first”和“psuedo code”策略，我们得出一个编程的简易流程：

> 1.  写一些运行失败的测试用例
> 2.  写出测试要用的函数、方法、类的基本结构
> 3.  用自己的语言填充这些框架，解释它们的功能
> 4.  用代码替换注释，直到测试代码运行通过
> 5.  重复

在这节练习中，你将通过运行我给你的测试程序逆向运行`lexicon.py`来实践这个方法。

## 　你应该测试的东西

这里是你要用到的测试文件：

```py
from nose.tools import *
from ex48 import lexicon

def test_directions():
    assert_equal(lexicon.scan("north"), [('direction', 'north')])
    result = lexicon.scan("north south east")
    assert_equal(result, [('direction', 'north'),
                          ('direction', 'south'),
                          ('direction', 'east')])

def test_verbs():
    assert_equal(lexicon.scan("go"), [('verb', 'go')])
    result = lexicon.scan("go kill eat")
    assert_equal(result, [('verb', 'go'),
                          ('verb', 'kill'),
                          ('verb', 'eat')])

def test_stops():
    assert_equal(lexicon.scan("the"), [('stop', 'the')])
    result = lexicon.scan("the in of")
    assert_equal(result, [('stop', 'the'),
                          ('stop', 'in'),
                          ('stop', 'of')])

def test_nouns():
    assert_equal(lexicon.scan("bear"), [('noun', 'bear')])
    result = lexicon.scan("bear princess")
    assert_equal(result, [('noun', 'bear'),
                          ('noun', 'princess')])

def test_numbers():
    assert_equal(lexicon.scan("1234"), [('number', 1234)])
    result = lexicon.scan("3 91234")
    assert_equal(result, [('number', 3),
                          ('number', 91234)])

def test_errors():
    assert_equal(lexicon.scan("ASDFADFASDF"), [('error', 'ASDFADFASDF')])
    result = lexicon.scan("bear IAS princess")
    assert_equal(result, [('noun', 'bear'),
                          ('error', 'IAS'),
                          ('noun', 'princess')]) 
```

你需要用项目框架写出一个新的项目，就像你在练习 47 中做的一样。然后你需要创建这个测试用例以及你会用到的`lexicon.py`，看看测试用例顶部，看看它是如何被导入的。

接下来，按照我给你的提示写一些测试用例。看看我是如何做的：

> 1.  在测试用例顶部写上导入（import），并保证它正常运行
> 2.  创建第一个测试用例`test_directions`的空版本，并保证它正常运行
> 3.  写出测试用例`test_directions`的第一行，保证它运行失败
> 4.  到`lexicon.py`文件，创建一个空的`scan`方法
> 5.  运行测试用例，至少保证`scan`方法运行，即便测试用例运行失败
> 6.  为`scan`写出伪代码注释，用来说明`scan`如何通过`test_directions`测试
> 7.  写出与注释相匹配的代码，保证`test_directions`测试通过
> 8.  回到方法`test_directions`，写完剩下的行
> 9.  回到`lexicon.py`中的`scan`方法，补全代码直到`test_directions`测试通过
> 10.  这样，当你的第一个测试通过，你移动到下一个测试重复以上步骤。

只要你坚持在每次执行此过程中的一小块，你可以成功将大问题分解成更小的问题来解决。就像爬山的时候，你把整段路程分成一小段一小段。

## 附加题

> 1.  改进单元测试，让它覆盖到更多的语汇。
> 2.  向语汇列表添加更多的语汇，并且更新单元测试代码。
> 3.  让你的扫描器能够识别任意大小写的词汇。更新你的单元测试。
> 4.  找出另外一种转换为数字的方法。
> 5.  我的解决方案用了 37 行代码，你的是更长还是更短呢？

## 常见问题

### Q: 为什么我一直有这个报错`ImportErrors`？

> 导入异常通常有以下几点原因：1，在你的模块（modules）目录下没有生成`__init__.py`文件；2，你在错误的目录下启动服务；3，你导入的模块有拼写错误；4，你的`PYTHONPATH`没有设置成`.`。

### Q: `try-except`和`if-else`有什么区别？

> `try-expect`是用来处理模块抛出的异常，永远都不能用`if-else`代替。

### Q: 有没有办法能实现在等待用户输入的时候，游戏也一样运行

> 我假设一种情况，你想实现用户在反应不够快的情况下会遭到怪物的攻击，这是可能的，但是它涉及的模块和技术是本书范围之外的。