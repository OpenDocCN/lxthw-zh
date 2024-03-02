# 练习 4 变量和名字

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.9.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.9.learn-py3.md)

现在你已经能用 `print` 打印东西了，也能用 Python 做数学计算了。接下来我们要学习变量。在编程中，变量就是给某个东西起的名字，就像“写这本书的人”名叫“Zed”一样。程序员用这些变量让代码读起来更像自然语言。如果他们不给软件里面的东西起名字，当他们再次阅读他们写的代码时就会毫无头绪。

如果你在做这个练习的时候卡住了，记得我交给你的技巧，寻找不同点，并专注细节：

*   在每行代码上面写上注释，跟自己解释这行代码的作用。
*   倒着读你的 `.py` 文件。
*   大声把你的 `.py` 文件读出来，字符也要读。ex4.py

```py
1 cars =  100
2 space_in_a_car =  4.0
3 drivers =  30
4 passengers =  90
5 cars_not_driven = cars - drivers
6 cars_driven = drivers
7 carpool_capacity = cars_driven * space_in_a_car
    8.  `8 average_passengers_per_car = passengers / cars_driven` 
9
10
11  print("There are", cars,  "cars available.")
12  print("There are only", drivers,  "drivers available.")
13  print("There will be", cars_not_driven,  "empty cars today.")
14  print("We can transport", carpool_capacity,  "people today.")
15  print("We have", passengers,  "to carpool today.")
16  print("We need to put about", average_passengers_per_car,
17  "in each car.")
```

| 警告！ |
| --- |
| `space*in_a_car*` *中的* `是下划线，我们会在以后的练习中经常用它来代替变量名之间的空格。` |

## 你会看到

练习 4 会话

```py
1.  `$ python3.6 ex4.py`2.  `There are 100 cars available.`3.  `There are only 30 drivers available.`4.  `There will be 70 empty cars today.`5.  `We can transport 120.0 people today.`6.  `We have 90 to carpool today.`7.  `We need to put about 3.0  in each car.`
```

## 附加练习

当我第一次写这个程序的时候我出了一个小错误，Python 是这样告诉我的：

```py
1.  `Traceback  ( most recent call last  ):`2.  `File  "ex4.py"  , line 8  ,  in  <module>`3.  `average_passengers_per_car = car_pool_capacity / passenger`4.  `NameError  : name ' car_pool_capacity '  is  not  defined`
```

用你自己的话解释这段错误信息，要用行号并解释清楚为什么。

## 更多附加练习：

*   我给 `space_in_a_car` 赋予了 4.0 而不是 4，小数部分有必要加吗？如果只写 4 会怎么样？
*   记住，4.0 是一个浮点数，浮点数就是有小数点的数字，要得到一个浮点数，你就得写成 `4.0` 而不是 `4`。
*   给每一个变量写一些注释。
*   确定你知道 `=` 就是给一个变量名（比如`cars_driven`，`passengers`）赋一个值（可以是数字、字符串等等）。
*   记住 `_` 是个下划线。
*   像之前的练习一样把 Python3.6 当做一个计算器来运行，然后用变量名来做运算，比如用得比较多的 i、x、j 等。

## 常见问题

**`=` 和 `==` 有什么区别？** `=` 把右边的值赋给左边的变量。`==` 用来检测左右两边的东西是不是有同样的值。你会在练习 27 中学到这块内容。

**我们能把 `x = 100` 写成 `x=100` 吗？** 可以，但这种格式不好，加上空格阅读体验更好。

**你说的“倒着读文件”是什么意思？**很简单，假如你有一个 16 行代码的文件，从第 16 行开始，和我文件中的第 16 行开始对比，然后是第 15 行等等，直到你把整个文件过完。

**为什么给 `space_in_a_car` 赋值要用 4.0？**主要是为了让你知道什么是浮点数，以及问出这个问题，可以参考附加练习。