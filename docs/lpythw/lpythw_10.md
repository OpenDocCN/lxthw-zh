# 练习 6.字符串和文本

# 练习 6.字符串和文本

虽然你已经在程序中写过字符串了，你还没学过它们的用处。在这节练习中我们将使用复杂的字符串来建立一系列的变量，从中你将学到它们的用途。首先我们解释一下字符串是什么。

字符串通常是指你想要展示给别人的、或者是你想要从程序里“导出”的一小段字符。Python 可以通过文本里的双引号`"`或者单引号`'`识别出字符串来。这在你以前的 print 练习中你已经见过很多次了。如果你把单引号或者双引号括起来的文本放到 print 后面，它们就会被 python 打印出来。

字符串可以包含格式化字符`%s`，这个你之前也见过的。你只要将格式化的变量放到字符串中，再紧跟着一个百分号 `%`(percent)，再紧跟着变量名即可。 唯一要注意的地方，是如果你想要在字符串中通过格式化字符放入多个变量的时候，你需要将变量放到 `( )` 圆括号(parenthesis)中，而且变量之间用`,` 逗号(comma)隔开。就像你逛商店说“我要买牛奶、面包、鸡蛋、汤”一样，只不过程序员说的是”(milk, eggs, bread, soup)”。

我们将练习输入大量的字符串、变量、和格式化字符，并且将它们打印出来。我们还将练习使用简写的变量名。程序员喜欢用高难度的简写来节约打字时间，所以我们现在就提早学会这个，这样你就能读懂并且写出这些东西了。

```py
x = "There are %d types of people." % 10
binary = "binary"
do_not = "don't"
y = "Those who know %s and those who %s." % (binary, do_not)

print x
print y

print "I said: %r." % x
print "I also said: '%s'." % y

hilarious = False
joke_evaluation = "Isn't that joke so funny?! %r"

print joke_evaluation % hilarious

w = "This is the left side of..."
e = "a string with a right side."

print w + e 
```

## 你看到的结果

```py
$ python ex6.py
There are 10 types of people.
Those who know binary and those who don't.
I said: 'There are 10 types of people.'.
I also said: 'Those who know binary and those who don't.'.
Isn't that joke so funny?! False
This is the left side of...a string with a right side. 
```

## 附加题

> 1.  通读程序，并给每一行加上注释，解释下这行的作用。
> 2.  找到所有的”字符串包含字符串”的位置，总共有四个位置。
> 3.  你确定只有四个位置吗？你怎么知道的？也许我在骗你呢。
> 4.  解释一下为什么用`+`连起来 w 和 e 就可以生成一个更长的字符串。

## 常见问题

### Q:`%r` 和 `%s`有什么不同?

> 用`%r`显示的是变量“原始”的数据值，`%r`在打印的时候能够重现它代表的对象，但其他的符号用来给用户显示变量值。看下面的例子理解一下：
> 
> > text = "I am %d years old." % 22 > > print "I said: %s." % text > > print "I said: %r." % text
> 
> 返回的结果：
> 
> > I said: I am 22 years old.. > > I said: 'I am 22 years old.'. // %r 给字符串加了单引号

### Q:我遇到这个报错:not all arguments converted during string formatting.

> 你要重新检查你的代码是否跟示例中的一样。发生这个错误的原因是你写的`%`的格式化字符串数量大于你给出的变量数量。再检查一遍，看你的代码哪里出错了。

### Q:为什么用`'(单引号)`标识字符串而不是其他的符号?

> 大部分情况下这只是一种风格，在一个用双引号标识的字符串内部我也会用单引号来标识其中子串。看看代码的第 10 行我是如何使用单双引号的。如果你认为一个笑话很好笑，你能否些 I`hilarious = True`? 答案当时是可以，而且，我们会在习题 27 中学到布尔值 。