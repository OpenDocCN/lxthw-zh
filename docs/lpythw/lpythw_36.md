# 练习 32.循环和列表

# 练习 32.循环和列表

现在你应该有能力写更有趣的程序出来了。如果你能一直跟得上，你应该已经看出将“if 语句”和“布尔表达式”结合起来可以让程序作出一些智能化的事情。

out.我们的程序还需要能快速的完成很多重复的工作。这节习题，我们将使用`for 循环`来创建并打印一些列表。在练习的过程中，你会逐渐明白它们是怎么回事，我不会告诉你答案的，你要自己去找出来。

在你开始使用 for 循环之前，你需要在某个位置存放循环的结果。最好的方法是使用列表（list），顾名思义，列表就是一个按顺序存放东西的容器。它并不复杂，你只是要学习一点新的语法。首先我们看看如何创建列表：

```py
hairs = ['brown', 'blond', 'red']
eyes = ['brown', 'blue', 'green']
weights = [1, 2, 3, 4] 
```

你要做的是以 `[`（左方括号）开头“打开”列表，然后写下你要放入列表的东西，用逗号隔开，就跟函数的参数一样，最后用`]`（右方括号）结束列表的定义。然后 Python 接收这个列表以及里边所有的内容，将其赋给一个变量。

> **Warning:**对于不会编程的人来说这是一个难点。习惯性思维告诉你的大脑大地是平的。记得上一个练习中的 if 语句嵌套吧？你可能觉得要理解它有些难度，因为生活中一般人不会去像这样的问题，但这样的问题在编程中几乎到处都是。你会看到一个函数调用另外一个包含 if 语句的函数，其中又有嵌套列表的列表。如果你看到这样的东西一时无法弄懂，就用纸笔记下来，手动分割代码，直到弄懂为止。

现在我们将使用循环创建一些列表，然后将它们打印出来:

```py
the_count = [1, 2, 3, 4, 5]
fruits = ['apples', 'oranges', 'pears', 'apricots']
change = [1, 'pennies', 2, 'dimes', 3, 'quarters']

# this first kind of for-loop goes through a list
for number in the_count:
    print "This is count %d" % number

# same as above
for fruit in fruits:
    print "A fruit of type: %s" % fruit

# also we can go through mixed lists too
# notice we have to use %r since we don't know what's in it
for i in change:
    print "I got %r" % i

# we can also build lists, first start with an empty one
elements = []

# then use the range function to do 0 to 5 counts
for i in range(0, 6):
    print "Adding %d to the list." % i
    # append is a function that lists understand
    elements.append(i)

# now we can print them out too
for i in elements:
    print "Element was: %d" % i 
```

## 你看到的结果

```py
$ python ex32.py
This is count 1
This is count 2
This is count 3
This is count 4
This is count 5
A fruit of type: apples
A fruit of type: oranges
A fruit of type: pears
A fruit of type: apricots
I got 1
I got 'pennies'
I got 2
I got 'dimes'
I got 3
I got 'quarters'
Adding 0 to the list.
Adding 1 to the list.
Adding 2 to the list.
Adding 3 to the list.
Adding 4 to the list.
Adding 5 to the list.
Element was: 0
Element was: 1
Element was: 2
Element was: 3
Element was: 4
Element was: 5 
```

## 附加题

> 1.  注意一下`range`的用法。查一下 `range` 函数并理解它。
> 2.  在第 22 行，你是否可以直接将`elements`赋值为`range(0,6)`，而无需使用 for 循环？
> 3.  在 Python 文档中找到关于列表的内容，仔细阅读以下，除了 append 以外列表还支持哪些操作？

## 常见问题

### Q: 如何定义一个两层（2D）的列表？

> 就是一个列表在另一个列表里面，比如`[[1,2,3],[4,5,6]]`

### Q: 列表和数组不是同一种东西吗？

> 依赖于语言和实现方式。在经典设计角度，由于数组列表的实现方式不同，数组列表是非常不同的。在 Ruby 中程序员称之为数组。在 Python 中,他们称之为列表。因为现在是 Python 调用它们，所以我们就称呼它为列表。

### Q: 为什么 for 循环可以使用一个没有定义过的变量？

> 在 for 循环开始的时候，就会定义这个变量， 并初始化。

### Q: 为什么`for i in range(1, 3):`只循环了两次？

> `range()`函数循环的次数不包括最后一个。所以`range(1,3)`只循环到 2,这是这种循环最常用的方法。

### Q: `elements.append()`实现什么功能？

> 它能实现在列表的末尾追加一个元素。打开 Python 解析器，自己写一个列表做些实验。当你遇到这类问题的时候，都可以在 Python 的解析器中做些实验，自己找到问题的答案。