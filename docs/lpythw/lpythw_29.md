# 练习 25.更多更多的练习

# 练习 25.更多更多的练习

我们将做一些关于函数和变量的练习，以确认你真正掌握了这些知识。这节练习对你来说可以说是：写程序，逐行研究，弄懂它。

过这节练习还是有些不同，你不需要运行它，取而代之，你需要将它导入到 python 里通过自己执行函数的方式运行。

```py
def break_words(stuff):
    """This function will break up words for us."""
    words = stuff.split(' ')
    return words

def sort_words(words):
    """Sorts the words."""
    return sorted(words)

def print_first_word(words):
    """Prints the first word after popping it off."""
    word = words.pop(0)
    print word

def print_last_word(words):
    """Prints the last word after popping it off."""
    word = words.pop(-1)
    print word

def sort_sentence(sentence):
    """Takes in a full sentence and returns the sorted words."""
    words = break_words(sentence)
    return sort_words(words)

def print_first_and_last(sentence):
    """Prints the first and last words of the sentence."""
    words = break_words(sentence)
    print_first_word(words)
    print_last_word(words)

def print_first_and_last_sorted(sentence):
    """Sorts the words then prints the first and last one."""
    words = sort_sentence(sentence)
    print_first_word(words)
    print_last_word(words) 
```

首先以正常的方式`python ex25.py`运行，找出里边的错误，并修正。然后你需要跟着下面的答案部分完成这节练习。

## 你看到的结果

在这节练习中，我们将在 Python 解析器中，以交互的方式和你写的`ex25.py`文件交流，你可以像下面这样在命令行中启动 python 解析器：

```py
$ python
Python 2.7.1 (r271:86832, Jun 16 2011, 16:59:05)
[GCC 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2335.15.00)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

你的输出应该和我类似，在`&gt;`符号之后，你可以输入并立即执行 python 代码。我希望你用这种方式逐行输入下方的 python 代码，并看看他们有什么用：

```py
import ex25
sentence = "All good things come to those who wait."
words = ex25.break_words(sentence)
words
sorted_words = ex25.sort_words(words)
sorted_words
ex25.print_first_word(words)
ex25.print_last_word(words)
words
ex25.print_first_word(sorted_words)
ex25.print_last_word(sorted_words)
sorted_words
sorted_words = ex25.sort_sentence(sentence)
sorted_words
ex25.print_first_and_last(sentence)
ex25.print_first_and_last_sorted(sentence) 
```

这是我做出来的样子：

```py
Python 2.7.1 (r271:86832, Jun 16 2011, 16:59:05) 
[GCC 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2335.15.00)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import ex25
>>> sentence = "All good things come to those who wait."
>>> words = ex25.break_words(sentence)
>>> words
['All', 'good', 'things', 'come', 'to', 'those', 'who', 'wait.']
>>> sorted_words = ex25.sort_words(words)
>>> sorted_words
['All', 'come', 'good', 'things', 'those', 'to', 'wait.', 'who']
>>> ex25.print_first_word(words)
All
>>> ex25.print_last_word(words)
wait.
>>> words
['good', 'things', 'come', 'to', 'those', 'who']
>>> ex25.print_first_word(sorted_words)
All
>>> ex25.print_last_word(sorted_words)
who
>>> sorted_words
['come', 'good', 'things', 'those', 'to', 'wait.']
>>> sorted_words = ex25.sort_sentence(sentence)
>>> sorted_words
['All', 'come', 'good', 'things', 'those', 'to', 'wait.', 'who']
>>> ex25.print_first_and_last(sentence)
All
wait.
>>> ex25.print_first_and_last_sorted(sentence)
All
who 
```

当你写完这些代码，确保你能在`ex25.py`中找到运行的函数，并且明白它们每一个都是如何工作的。如果你的运行结果出错或者跟我的结果不一样，你就需要检查并修复你的代码，重启 python 解析器，再次运行程序。

## 附加题

> 1.  研究答案中没有分析过的行，找出它们的来龙去脉。确认自己明白了自己使用的是模块`ex25`中定义的函数。
> 2.  试着执行`help(ex25)`和`help(ex25.break_words)`。这是你得到模块帮助文档的方式。 所谓帮助文档就是你定义函数时放在`"""`之间的东西，它们也被称作`documentation comments （文档注解）`，后面你还会看到更多类似的东西。
> 3.  重复键入`ex25.` 是很烦的一件事情。有一个捷径就是用`from ex25 import *`的方式导入模组。这相当于说：“我要把 ex25 中所有的东西 import 进来。”程序员喜欢说这样的倒装句，开一个新的会话，看看你所有的函数是不是已经在那里了。
> 4.  把你脚本里的内容逐行通过 python 编译器执行，看看会是什么样子。你可以通过输入`quit()`来退出 Python。

## 常见问题

### Q: 我的某些函数没有打印输出任何值

> 你的函数末尾可能缺少`return`语句，检查你的文件，确保每一行代码的正确性。

### Q: 我输入`import ex25`的时候遇到报错`import: command not found`.

> 仔细观察“你看到的结果”部分，看我是如何运行程序的。我是在 python 解析器里而不是在命令行运行程序。你应该先运行 python 解析器。

### Q: 当我输入`import ex25.py`的时候，我遇到报错`ImportError: No module named ex25.py`.

> 不要加上`.py`。Python 知道文件是以`.py`结尾的，所以你只要输入`import ex25`就可以了。

### Q:运行程序是，遇到报错信息`SyntaxError: invalid syntax`

> 这个信息说明在报错的这一行或之前的某一行你可能少写了一个`(` 或者 `"` 或者其它的语法错误。当你遇到这个报错的时候，从报错的行开始，向上检查是否每一行代码都是正确的。

### Q:函数`words.pop`是如何改变变量`words`的值的？

> 这是一个复杂的问题,在这个实例中，`words`是一个列表，所以你可以调用它的一些命令，而它也会保留这些命令的结果。这类似于文件的工作原理。

### Q: 什么情况下，我可以在函数中用`print`代替`return`？

> `return`是从函数给出的代码行调用的函数的结果。你可以把函数理解成 通过参数获取输入，并通过`return`返回输出,而`print`是与这个过程完全无关的，它只负责在终端打印输出。