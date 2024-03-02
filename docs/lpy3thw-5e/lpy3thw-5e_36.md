## 练习 33. 循环和列表

现在你应该能够编写一些更有趣的程序了。如果你一直在跟进，你应该意识到现在你可以将所有其他学到的东西与`if-statements`和布尔表达式结合起来，使你的程序做一些聪明的事情。

然而，程序也需要快速地执行重复的事情。在这个练习中，我们将使用`for-loop`来构建和打印各种列表。当你做这个练习时，你会开始明白它们是什么。我现在不会告诉你。你必须自己弄清楚。

在使用`for-loop`之前，你需要一种方法来*存储*循环的结果。最好的方法是使用`lists`。`Lists`正是它们的名字所说的：一个按照从头到尾顺序组织的东西的容器。这并不复杂；你只需要学习一种新的语法。首先，这是如何创建`lists`的：

```py
1   hairs = ['brown', 'blond', 'red']
2   eyes = ['brown', 'blue', 'green']
3   weights = [1, 2, 3, 4]
```

你用`[`（左括号）开始`list`，这个“打开”`list`。然后你用逗号分隔每个你想要放入列表的项目，类似于函数参数。最后，用`]`（右括号）结束列表以表示它的结束。然后 Python 将获取这个列表及其所有内容，并将它们分配给变量。

警告！

这就是对于不能编码的人来说变得棘手的地方。你的大脑被教导世界是平的。还记得在上一个练习中你是如何在`if-statements`内部放置`if-statements`的吗？那可能让你的大脑感到疼痛，因为大多数人不会考虑如何在“嵌套”事物内部放置事物。在编程中，嵌套结构随处可见。你会发现调用其他函数的函数，这些函数有带有列表的`if-statements`，列表内部还有列表。如果你看到这样的结构而无法理解，拿出一支铅笔和纸，逐步手动分解，直到你理解为止。

现在我们将使用一些`for-loops`来构建一些列表并将它们打印出来：

列表 33.1：ex33.py

```py
 1   the_count = [1, 2, 3, 4, 5]
 2   fruits = ['apples', 'oranges', 'pears', 'apricots']
 3   change = [1, 'pennies', 2, 'dimes', 3, 'quarters']
 4
 5   # this first kind of for-loop goes through a list
 6   **for** number **in** the_count:
 7       **print(**f"This is count {number}"**)**
 8
 9   # same as above
10   **for** fruit **in** fruits:
11       **print(**f"A fruit of type: {fruit}"**)**
12
13   # also we can go through mixed lists too
14   **for** i **in** change:
15       **print(**f"I got {i}"**)**
16
17   # we can also build lists, first start with an empty one
18   elements = []
19
20   # then use the range function to do 0 to 5 counts
21   **for** i **in range**(0, 6):
22       **print(**f"Adding {i} to the list."**)**
23       # append is a function that lists understand
24       elements.append**(**i**)**
25
26   # now we can print them out too
27   **for** i **in** elements:
28       **print(**f"Element was: {i}"**)**
```

### 你应该看到的内容

```py
 1   This is count 1
 2   This is count 2
 3   This is count 3
 4   This is count 4
 5   This is count 5
 6   A fruit of type: apples
 7   A fruit of type: oranges
 8   A fruit of type: pears
 9   A fruit of type: apricots
10   I got 1
11   I got pennies
12   I got 2
13   I got dimes
14   I got 3
15   I got quarters
16   Adding 0 to the list.
17   Adding 1 to the list.
18   Adding 2 to the list.
19   Adding 3 to the list.
20   Adding 4 to the list.
21   Adding 5 to the list.
22   Element was: 0
23   Element was: 1
24   Element was: 2
25   Element was: 3
26   Element was: 4
27   Element was: 5
```

#### `dis()`它

这次让我们简单点，只看看 Python 如何执行`for-loop`：

```py
1   from dis import dis
2
3   dis('''
4   for number in the_count:
5       print(number)
6   ''')
```

这次我将在这里重现输出，以便我们可以分析它：

```py
 1    0 LOAD_NAME     0 (the_count) # get the count list
 2    2 GET_ITER                    # start iteration
 3    4 FOR_ITER      6 (to 18)     # for-loop jump to 18
 4    6 STORE_NAME    1 (number)    # create number variable
 5
 6    8 LOAD_NAME     2 (print)     # load print()
 7   10 LOAD_NAME     1 (number)    # load number
 8   12 CALL_FUNCTION 1             # call print()
 9   14 POP_TOP                     # clean stack
10   16 JUMP_ABSOLUTE 2 (to 4)      # jump back to FOR_ITER at 4
11
12   18 LOAD_CONST    0 (None)      # jump here when FOR_ITER done
13   20 RETURN_VALUE
```

在`FOR_ITER`操作中我们看到了一个新的东西。这个操作通过以下步骤使`for-loop`工作：

1\. 调用`the_count.__next__()`

2\. 如果`the_count`中没有更多元素，则跳转到 18

3\. 如果仍然有元素，则继续执行

4\. `STORE_NAME`然后将`the_count.__next__()`的结果赋给名为`number`的变量

这就是`for-loop`实际上所做的一切。它主要是一个单字节代码`FOR_ITER`，结合其他几个来遍历列表。

### 学习练习

1\. 看看你如何使用了`range`。查阅`range`函数以了解它。

2\. 在第 22 行完全避免了那个`for-loop`，直接将`range(0,6)`赋给`elements`，你能做到吗？

3\. 查找关于列表的 Python 文档并阅读它们。除了`append`之外，你还可以对列表进行哪些操作？

### 常见学生问题

**如何创建二维（2D）列表？** 就像这样的列表中嵌套列表：`[[1,2,3],[4,5,6]]`

**列表和数组不是一回事吗？** 这取决于语言和实现。在传统术语中，列表与数组非常不同，因为它们的实现方式不同。在 Ruby 中，它们称之为“数组”。在 Python 中，它们称之为“列表”。现在只需称之为“列表”，因为这是 Python 的称呼。

**为什么 for 循环能够使用尚未定义的变量？** 变量在循环开始时由 `for 循环` 定义，每次迭代时将其初始化为当前循环元素。

**为什么** `for i in range(1, 3):` **只循环两次而不是三次？** `range()` 函数只生成从第一个到最后一个的数字，*不包括最后一个*。因此，在上述情况下它在两处停止，而不是三处。这实际上是这种循环最常见的方式。

**`elements.append()`** 做什么？它简单地将元素附加到列表的末尾。打开 Python shell 并尝试用自己创建的列表做几个示例。每当遇到这样的情况时，总是尝试在 Python shell 中进行交互操作。
