# 练习 30 Else 和 if

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.35.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.35.learn-py3.md)

在上个练习中你学到了一些 if 语句，思考了它的含义和作用。在你学习更多内容之前，我会解释一下上个附加练习中的问题。首先确定你做了那些练习。

**1\. 你认为 if 对它下面的代码起什么作用？**

if 语句在代码中创建了一个“分支”（branch），有点类似于在一本冒险书中，你选择了哪个答案，就翻到对应的一页，如果你选择了不同的答案，就会去到不同的地方。if 语句就是告诉脚本，如果这个布尔表达式是 True，那就运行它下面的代码，否则的话就跳过。

**2\. 为什么 if 下面的代码要缩进 4 个空格？**

通过一行代码结尾的冒号告诉 Python 你在创建一个新的代码块，然后缩进四个空格告诉 Python 这个代码块中都有些什么。这就跟本书前半部分中你学的函数是一样的。

**3\. 如果没有缩进会发生什么？**

如果没有缩进，你很可能收到一个错误提示。Python 一般会让你在一个带 ： 的代码行下面缩进一些内容。

**4\. 你能从练习 27 里面把一些布尔表达式放进 if 语句吗？试试看。**

试试吧，你可以的。你可以把它们写得很复杂，不过复杂的东西一般风格都很糟糕。

**5\. 如果你改变 people，cats 和 dogs 的初始值会发生什么？**

因为你在比较数字，所以如果你改变了数字，不同的 if 语句将会得出不同的判断结果，那么下面某些代码块就有可能运行。回到练习中给这些变量一些不同的数值，然后看看你能否在脑中判断出来哪些代码块会运行。

把我的答案和你的比较一下，然后确保你真的理解了代码块的概念。这对你进行接下来的练习很重要。把下面的代码输入进去然后运行。

ex30.py

```py
1.  1.  `1 people =  30`
    2.  `2 cars =  40`
    3.  `3 trucks =  15`
    4.  `4`
    5.  `5`
    6.  `6  if cars > people:`
    7.  `7  print("We should take the cars.")`
    8.  `8  elif cars < people:`
    9.  `9  print("We should not take the cars.")`
    10.  `10  else:`
    11.  `11  print("We can't decide.")`
    12.  `12`
    13.  `13  if trucks > cars:`
    14.  `14  print("That's too many trucks.")`
    15.  `15  elif trucks < cars:`
    16.  `16  print("Maybe we could take the trucks.")`
    17.  `17  else:`
    18.  `18  print("We still can't decide.")`
    19.  `19`
    20.  `20  if people > trucks:`
    21.  `21  print("Alright, let's just take the trucks.")`
    22.  `22  else:`
    23.  `23  print("Fine, let's stay home then.")`
```

## 你会看到

练习 30 会话

```py
1.  `$ python3.6 ex30.py`2.  `We should take the cars.`3.  `Maybe we could take the trucks.`4.  `Alright,  let's just take the trucks.`
```

## 附加练习

> 1.  试着猜猜 elif 和 else 的作用是什么。
> 2.  改变 cars，people，和 trucks 的数值，然后追溯每一个 if 语句，看看什么会被打印出来。
> 3.  试试一些更复杂的布尔表达式，比如 cars > people 或者 trucks < cars。
> 4.  在每一行上面加上注释。

## 常见问题

**如果多个 elif 块都是 True 会发生什么？** Python 从顶部开始，然后运行第一个是 True 的代码块，也就是说，它只会运行第一个。