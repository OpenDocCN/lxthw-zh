## 练习 4：变量和名称

现在你可以用`print`打印东西，还可以进行数学运算。下一步是学习关于变量的知识。在编程中，变量只不过是某物的名称，类似于我的名字“Zed”是“写这本书的人类”的名称。程序员使用这些变量名称使他们的代码更像英语，并且因为他们的记忆力不好。如果他们在软件中不使用良好的名称，当他们再次阅读代码时就会迷失方向。

如果你在这个练习中遇到困难，记住你到目前为止学到的找出差异和专注细节的技巧：

1.  在每一行上面写一个注释，用英语解释它的作用。

2.  反向阅读你的 Python 代码。

3.  大声朗读你的 Python 代码，甚至说出字符。

列表 4.1: ex4.py

```py
 1   cars = 100
 2   space_in_a_car = 4.0
 3   drivers = 30
 4   passengers = 90
 5   cars_not_driven = cars - drivers
 6   cars_driven = drivers
 7   carpool_capacity = cars_driven * space_in_a_car
 8   average_passengers_per_car = passengers / cars_driven
 9
10
11   **print(**"There are", cars, "cars available."**)**
12   **print(**"There are only", drivers, "drivers available."**)**
13   **print(**"There will be", cars_not_driven, "empty cars today."**)**
14   **print(**"We can transport", carpool_capacity, "people today."**)**
15   **print(**"We have", passengers, "to carpool today."**)**
16   **print(**"We need to put about", average_passengers_per_car,
17         "in each car."**)**
```

信息

`space_in_a_car`中的`_`被称为下划线字符。如果你还不知道如何输入它，请找出如何输入。我们经常使用这个字符在变量名中的单词之间放置一个虚拟空格。

### 你应该看到的结果

```py
1   There are 100 cars available.
2   There are only 30 drivers available.
3   There will be 70 empty cars today.
4   We can transport 120.0 people today.
5   We have 90 to carpool today.
6   We need to put about 3.0 in each car.
```

### 练习

当我第一次编写这个程序时，我犯了一个错误，Python 像这样告诉我：

```py
1   Traceback (most recent call last):
2     Cell In[1], line 8, in <module>
3       average_passengers_per_car = car_pool_capacity / passenger
4   NameError: name 'car_pool_capacity' is not defined
```

用你自己的话解释这个错误。确保使用行号并解释原因。

这里有更多练习：

1.  我用 4.0 代表`space_in_a_car`，但这是必要的吗？如果只是 4 会发生什么？

2.  记住 4.0 是一个`浮点数`。它只是一个带有小数点的数字，你需要用 4.0 而不是只有 4，这样它就是浮点数了。

3.  在每个变量赋值上面写注释。

4.  确保你知道`=`被称为什么（等于号），它的目的是给数据（数字、字符串等）命名（`cars_driven`、`passengers`）。

5.  记住`_`是一个下划线字符。

6.  尝试像之前一样从终端运行`python3`作为计算器，并使用变量名进行计算。常用的变量名还有`i`、`x`和`j`。

### 常见学生问题

**`=`（单等号）和** `==` **（双等号）之间有什么区别？** `=`（单等号）将右侧的值赋给左侧的变量。`==`（双等号）测试两个值是否相同。你以后会学到这个。

**我们可以写** `x=100` **而不是** `x = 100`**吗？** 可以，但这是不好的形式。你应该在操作符周围添加空格，这样更容易阅读。

**“反向阅读文件（代码）”是什么意思？** 非常简单。想象你有一个有 16 行代码的文件。从第 16 行开始，将其与我在第 16 行的代码进行比较。然后再对第 15 行进行同样的操作，依此类推，直到你将所有代码都反向阅读完。

**为什么你在** `space_in_a_car` **中使用** `4.0`**？** 主要是为了让你了解什么是浮点数，并提出这个问题。参见*练习*部分。
