## 练习 19：函数和变量

现在你将把函数与你从之前练习中了解到的变量结合起来。如你所知，变量给数据片段一个名称，这样你就可以在程序中使用它。如果你有这段代码：

```py
1   x = 10
```

然后你创建了一个名为`x`的数据片段，它等于数字 10。

你还知道你可以像这样带参数调用函数：

```py
1   def print_one(arg1):
2       print(f"arg1: {arg1}")
```

参数`arg1`是类似于之前的`x`的变量，只是当你像这样*调用*函数时为你创建：

```py
1   print_one("First!")
```

在练习 18 中，你学习了当你调用函数时 Python 如何运行它们，但如果你这样做会发生什么：

```py
1   y = "First!"
2   print_one(y)
```

不直接使用`"First!"`调用`print_one`，而是将`"First!"`赋给`y`，然后将`y`传递给`print_one`。这样会起作用吗？这里有一小段代码示例，你可以在 Jupyter 中测试一下：

```py
1   def print_one(arg1):
2       print(f"arg1: {arg1}")
3
4   y = "First!"
5   print_one(y)
```

这展示了如何将变量的概念`y = "First!"`与调用使用这些变量的函数相结合。在进行这个较长的练习之前，研究这个并尝试自己的变化，但首先给一点建议：

1.  这个很长，如果你在 Jupyter 中觉得难以管理，那么尝试将其输入到一个`ex19.py`文件中在终端中运行。

2.  通常情况下，你应该一次只输入几行代码，但如果你只输入函数的第一行，你会遇到问题。你可以使用`pass`关键字来解决这个问题，像这样：`def some_func(some_arg): pass`。`pass`关键字是用来创建一个空函数而不会引发错误的方法。

3.  如果你想看到每个函数在做什么，你可以使用“调试打印”像这样：`print` `(">>>> 我在这里", something)`。这将打印出一条消息，帮助你“跟踪”代码并查看每个函数中的`something`是什么。

列表 19.1：ex19.py

```py
 1   **def** cheese_and_crackers(cheese_count, boxes_of_crackers):
 2       **print(**f"You have {cheese_count} cheeses!"**)**
 3       **print(**f"You have {boxes_of_crackers} boxes of crackers!"**)**
 4       **print(**"Man that's enough for a party!"**)**
 5       **print(**"Get a blanket.\n"**)**
 6
 7
 8   **print(**"We can just give the function numbers directly:"**)**
 9   cheese_and_crackers**(**20, 30**)**
10
11
12   **print(**"OR, we can use variables from our script:"**)**
13   amount_of_cheese = 10
14   amount_of_crackers = 50
15
16   cheese_and_crackers**(**amount_of_cheese, amount_of_crackers**)**
17
18
19   **print(**"We can even do math inside too:"**)**
20   cheese_and_crackers**(**10 + 20, 5 + 6**)**
21
22
23   **print(**"And we can combine the two, variables and math:"**)**
24   cheese_and_crackers**(**amount_of_cheese + 100, amount_of_crackers + 1000**)**
```

### 你应该看到的内容

```py
 1   We can just give the function numbers directly:
 2   You have 20 cheeses!
 3   You have 30 boxes of crackers!
 4   Man that's enough for a party!
 5   Get a blanket.
 6
 7   OR, we can use variables from our script:
 8   You have 10 cheeses!
 9   You have 50 boxes of crackers!
10   Man that's enough for a party!
11   Get a blanket.
12
13   We can even do math inside too:
14   You have 30 cheeses!
15   You have 11 boxes of crackers!
16   Man that's enough for a party!
17   Get a blanket.
18
19   And we can combine the two, variables and math:
20   You have 110 cheeses!
21   You have 1050 boxes of crackers!
22   Man that's enough for a party!
23   Get a blanket.
```

### 学习练习

1.  你记得一次只输入几行代码吗？在填充之前使用`pass`创建一个空函数了吗？如果没有，删除你的代码然后重新做一遍。

2.  将`cheese_and_crackers`的名称拼错，然后查看错误消息。现在修复它。

3.  删除数学中的一个`+`符号，看看你会得到什么错误。

4.  修改数学内容，然后尝试预测你将得到什么输出。

5.  更改变量并尝试猜测这些更改后的输出。

### 常见学生问题

这个练习目前还没有问题，但你可以通过 help@learncodethehardway.org 向我提问以获取帮助。也许你的问题会出现在这里。
