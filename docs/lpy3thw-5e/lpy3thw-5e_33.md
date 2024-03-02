## 练习 30：假如

这是你将要输入的下一个 Python 脚本，它向你介绍了`if`语句。输入这个代码，确保它能够完美运行，然后我们将看看你的练习是否有所收获。

列表 30.1：ex30.py

```py
 1   people = 20
 2   cats = 30
 3   dogs = 15
 4
 5
 6   **if** people < cats:
 7       **print(**"Too many cats! The world is doomed!"**)**
 8
 9   **if** people > cats:
10       **print(**"Not many cats! The world is saved!"**)**
11
12   **if** people < dogs:
13       **print(**"The world is drooled on!"**)**
14
15   **if** people > dogs:
16       **print(**"The world is dry!"**)**
17
18
19   dogs += 5
20
21   **if** people >= dogs:
22       **print(**"People are greater than or equal to dogs."**)**
23
24   **if** people <= dogs:
25       **print(**"People are less than or equal to dogs."**)**
26
27
28   **if** people == dogs:
29       **print(**"People are dogs."**)**
```

### 你应该看到的内容

```py
1   Too many cats! The world is doomed!
2   The world is dry!
3   People are greater than or equal to dogs.
4   People are less than or equal to dogs.
5   People are dogs.
```

#### `dis()` 它

在接下来的几个练习中，我希望你运行`dis()`在你正在学习的一些代码上，以便更深入地了解它是如何工作的：

```py
1   from dis import dis
2
3   dis('''
4   if people < cats:
5       print("Too many cats! The world is doomed!")
6   ''')
```

这*不*是你在编程时通常会做的事情。我只是希望你在这里这样做，以便为你理解正在发生的事情提供另一种可能的方式。如果`dis()`并没有真正帮助你更好地理解代码，那么随意这样做并忘记它。

要研究这个问题，只需将 Python 代码放在这个`dis()`输出旁边，然后尝试识别与字节码匹配的 Python 代码行。

### 练习题

在这个练习中，试着猜测`if`语句是什么以及它的作用是什么。在继续下一个练习之前，尝试用自己的话回答这些问题：

1.  你认为`if`对下面的代码有什么影响？

2.  为什么`if`下面的代码需要缩进四个空格？

3.  如果没有缩进会发生什么？

4.  你能否在`if`语句中放入来自练习 28 的其他布尔表达式？试一试。

5.  如果你改变`people`、`cats`和`dogs`的初始值会发生什么？

### 常见学生问题

**`+=`是什么意思？** 代码`x += 1`与`x = x + 1`相同，但输入更少。你可以称之为“递增运算符”。对于`-=`和许多其他表达式，你以后会学到的也是一样。
