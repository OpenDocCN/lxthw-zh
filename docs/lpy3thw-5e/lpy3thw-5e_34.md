## 练习 31：否则和如果

在上一个练习中，你解决了一些`if 语句`，然后试图猜测它们是什么以及它们如何工作。在学习更多之前，我将通过回答你在学习练习中提出的问题来解释一切。你做了学习练习，对吧？

1.  你认为`if`对其下面的代码有什么影响？`if 语句`在代码中创建了所谓的“分支”。这有点像那些选择你自己冒险的书，如果你做出一个选择，就会被要求翻到一页，如果你选择另一条路，就会翻到另一页。`if 语句`告诉你的脚本，“如果这个布尔表达式为真，则运行其下的代码；否则跳过它。”

2.  为什么`if`下面的代码需要缩进四个空格？在一行的末尾加上冒号是告诉 Python 你将创建一个新的代码“块”，然后缩进四个空格告诉 Python 哪些代码行在该块中。这与你在本书的前半部分创建函数时所做的事情*完全*相同。

3.  如果没有缩进会发生什么？如果没有缩进，你很可能会产生 Python 错误。Python 希望你在以`:`（冒号）结尾的行之后缩进*一些*东西。

4.  你能把练习 28 中的其他布尔表达式放在`if 语句`中吗？试试看。是的，你可以，而且它们可以尽可能复杂，尽管非常复杂的东西通常是不好的风格。

5.  如果更改`people`，`cats`和`dogs`的初始值会发生什么？因为你正在比较数字，如果更改数字，不同的`if 语句`将评估为`True`，并且其下的代码块将运行。回去放入不同的数字，看看你是否能在脑海中弄清楚哪些代码块将运行。

将我的答案与你的答案进行比较，并确保你*真正*理解代码“块”的概念。这对于你做下一个练习很重要，其中你将编写所有可以使用的`if 语句`的部分。

将这个输入并使其工作。

列表 31.1：ex31.py

```py
 1   people = 30
 2   cars = 40
 3   trucks = 15
 4
 5
 6   if cars > people:
 7       print("We should take the cars.")
 8   elif cars < people:
 9       print("We should not take the cars.")
10   else:
11       print("We can't decide.")
12
13   if trucks > cars:
14       print("That's too many trucks.")
15   elif trucks < cars:
16       print("Maybe we could take the trucks.")
17   else:
18       print("We still can't decide.")
19
20   if people > trucks:
21       print("Alright, let's just take the trucks.")
22   else:
23       print("Fine, let's stay home then.")
```

### 你应该看到什么

```py
1   We should take the cars.
2   Maybe we could take the trucks.
3   Alright, let's just take the trucks.
```

#### `dis()`它

我们现在到了一个`dis()`有点太复杂的地步。让我们只选择一个代码块来学习：

```py
 1   from dis import dis
 2
 3   dis('''
 4   if cars > people:
 5       print("We should take the cars.")
 6   elif cars < people:
 7       print("We should not take the cars.")
 8   else:
 9       print("We can't decide.")
10   ''')
```

我认为学习这个最好的方法是将 Python 代码放在`dis()`输出旁边，尝试将 Python 代码的行与其字节码匹配。如果你能做到这一点，那么你将远远领先于许多甚至不知道 Python 有`dis()`的 Python 程序员。

如果你搞不清楚，不要担心。这一切都是关于尽可能推动你的知识，以找到理解 Python 的新方法。

### 学习练习

1.  试着猜猜`elif`和`else`在做什么。

2.  更改`cars`，`people`和`trucks`的数字，然后跟踪每个`if 语句`，看看将打印出什么。

3.  尝试一些更复杂的布尔表达式，比如`cars > people or trucks < cars`。

4.  在每行上方写出该行的英文描述。

### 常见学生问题

**如果多个** `elif` **块都为** `True`**会发生什么？** Python 从顶部开始运行第一个为`True`的块，因此只会运行第一个。
