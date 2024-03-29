# 练习 25 更更多练习

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.30.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.30.learn-py3.md)

接下来我们要做更多包含函数和变量的练习，来确保你完全掌握这些东西。这个练习你应该能直接输入、拆解并理解。

不过，这个练习有一些不同，你不是运行它，而是要把它导入 Python 然后自己运行这个函数。

ex25.py

```py
1  def break_words(stuff):
2  """This function will break up words for us."""
3 words = stuff.split(' ')
4  return words
5
6  def sort_words(words):
7  """Sorts the words."""
8  return sorted(words)
9
10  def print_first_word(words):
11  """Prints the first word after popping it off."""
12 word = words.pop(0)
13  print(word)
14
15  def print_last_word(words):
16  """Prints the last word after popping it off."""
17 word = words.pop(-1)
18  print(word)
19
20  def sort_sentence(sentence):
21  """Takes in a full sentence and returns the sorted words
22      words = break_words(sentence)
23      return sort_words(words)
24
25  def print_first_and_last(sentence):
26      """Prints the first and  last words of the sentence."""
27      words = break_words(sentence)
28      print_first_word(words)
29      print_last_word(words)
30
31  def print_first_and_last_sorted(sentence):
32      """Sorts the words then prints the first and  last one.""
33 words = sort_sentence(sentence)
34 print_first_word(words)
35 print_last_word(words)
```

首先，用 `python3.6 ex25.py` 来运行这个脚本，找出你出错的地方，并把它们改正过来。然后对照“你会看到”部分看看运行结果是否一样。

## 你会看到

在这个练习中我们要在 python3.6 翻译器（interpreter）里与 `ex25.py` 文件交互，之前我们在做计算的时候也交互过。你在终端里这样运行 python3.6（Windows 下直接输入 `python`）：

```py
$ python3.6
Python  3.6.0rc2  (v3.6.0rc2:800a67f7806d,  Dec  16  2016,  14:12:21)
[GCC 4.2.1  (Apple  Inc. build 5666)  (dot 3)] on darwin
Type  "help "  ,  "copyright"  ,  "credits"  or  "license"  for more info
>>>
```

你的输出结果应该和我的一样，你可以在提示符（即 `>` ）后面输入 Python 代码，它会直接运行。我希望你用这种方式输入这个练习的每一行代码，然后看看会如何：

练习 25 会话

```py
1  import ex25
2 sentence =  "All good things come to those who wait."
3 words = ex25.break_words(sentence)
4 words
5 sorted_words = ex25.sort_words(words)
6 sorted_words
7 ex25.print_first_word(words)
8 ex25.print_last_word(words)
9 words
10 ex25.print_first_word(sorted_words)
11 ex25.print_last_word(sorted_words)
12 sorted_words
13 sorted_words = ex25.sort_sentence(sentence)
14 sorted_words
15 ex25.print_first_and_last(sentence)
16 ex25.print_first_and_last_sorted(sentence)
```

以下是交互模式下输入的结果： 练习 25 Python 会话

```py
Python  3.6.0  (default,  Feb  2  2017,  12:48:29)
[GCC 4.2.1  Compatible  Apple LLVM 7.0.2  (clang-700.1.81)] on darwi
Type  "help",  "copyright",  "credits"  or  "license"  for more informa
>>>  import ex25
>>> sentence =  "All good things come to those who wait."
>>> words = ex25.break_words(sentence)
>>> words
['All',  'good',  'things',  'come',  'to',  'those',  'who',  'wait.']
>>> sorted_words = ex25.sort_words(words)
>>> sorted_words
['All',  'come',  'good',  'things',  'those',  'to',  'wait.',  'who']
>>> ex25.print_first_word(words)
All
>>> ex25.print_last_word(words)
wait.
>>> words
['good',  'things',  'come',  'to',  'those',  'who']
>>> ex25.print_first_word(sorted_words)
All
>>> ex25.print_last_word(sorted_words)
who
>>> sorted_words
['come',  'good',  'things',  'those',  'to',  'wait.']
>>> sorted_words = ex25.sort_sentence(sentence)
>>> sorted_words
['All',  'come',  'good',  'things',  'those',  'to',  'wait.',  'who']
>>> ex25.print_first_and_last(sentence)
All
wait.
>>> ex25.print_first_and_last_sorted(sentence)
All
who
```

当你过完每一行，保证你能找到在 `ex25.py` 中运行的函数，并且理解了每个函数是如何运行的。如果你得到了不同的结果或者出现错误，你得把代码改正过来，然后退出 `python3.6` ，重新进入。

## 附加练习

*   弄明白“你会看到”中各行的作用是什么，确保你理解你是如何在 ex25 模块中运行你的函数的。
*   试试输入 `help(ex25)` 以及 `help(ex25.break_words)`（**要在交互练习后输入，否则无法成功运行**）。注意你是如何获取到关于这个模块的帮助的，以及帮助是如何放在 ex25 的每一个函数后面的 `"""` 字符串里的。 这些特殊的字符串被称为文件注释，我们会在后面看到更多。
*   输入 `ex25.` 很无聊，可以走个捷径：`from ex25 import *` ，意思就是从 ex25 导入所有东西，程序员总喜欢倒着说。打开一个新会话，看看你的函数会如何。
*   试着拆解你的文件，看看当你用它的时候，它在 Python 里是什么样的。你得先输入 `quit()` 来退出 python，再重新加载它。

## 常见问题

**有些函数我什么都没打印出来。**你可能有些函数忘了在后面输入 `return`。检查一遍你的代码，确保每一行都是对的。

**当我输入 `import ex25` 之后，我收到了 `-bash: import: command not found.`** 注意看“你会看到”部分我是怎么做的。我是在 Python 里面运行的，而不是在 Terminal，也就是说，你得先运行 Python。

**当我输入 `import ex25.py` 时收到了这样的错误：`ImportError: No module named ex25`。** 不要在后面加 `.py` ，Python 知道文件是以 `.py` 结尾的，所以你只用输入 `ex25` 即可。

**我运行的时候遇到了这个错误：`SyntaxError: invalid syntax`。**这意味着你漏掉了某些东西，比如少了一个 " 或者类似一对的符号。任何时候你只要收到这样的报错信息，你就从它提到的错的那行开始检查，看是不是所有字符都输入正确了，然后再回过头检查这一行上面的行是不是都输入正确了。

**`words.pop` 函数是如何改变 `words` 变量的？**这是个很复杂的问题，但是在本例中 `words` 是一个列表，正因为如此你可以给它一些命令。这就类似于当你操作文件和很多其他东西时候它们是如何运行的一样。

**在函数里我什么时候应该用 `print` 而不是 `return` 呢？**通过函数，`return` 能够给调用这个函数的那行代码返回一个结果，你可以把函数当成通过参数获取输入通过 `return` 返回输出。`print` 跟这个就完全不相关了，它只是把输出结果打印到终端。