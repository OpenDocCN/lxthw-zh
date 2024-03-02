# 练习 5 更多变量和打印

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.10.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.10.learn-py3.md)

现在我们要输入更多的变量并把它们打印出来。这次我们将用一个叫做“格式字符串”的东西。每次你用引号把一段文本引起来，你就是在创建一个字符串。字符串是你让计算机呈现给人看的内容。你可以打印字符串、把字符串保存到文件、或者发送到网络服务器等等。

字符串真的非常方便。你将在这个练习中学习如何创建包含变量的字符串。把你需要的变量放在 `{}` 里面就可以把变量嵌入在字符串中。你还需要在字符串前面加上字母 `f` （代表 format），比如 `f"Hello, {somevar}"`。双引号前面的 `f` 是为了告诉 python3： “这个字符串需要被格式化，把这些变量放在那儿。”

同样的，输入以下内容，哪怕你不理解，确保准确无误。

ex5.py

```py
1 my_name =  'Zed A. Shaw'
2 my_age =  35  # not a lie
3 my_height =  74  # inches
4 my_weight =  180  # lbs
5 my_eyes =  'Blue'
6 my_teeth =  'White'
7 my_hair =  'Brown'
8
9  print(f"Let's talk about {my_name}.")
10  print(f"He's {my_height} inches tall.")
11  print(f"He's {my_weight} pounds heavy.")
12  print("Actually that's not too heavy.")
13  print(f"He's got {my_eyes} eyes and {my_hair} hair.")
14  print(f"His teeth are usually {my_teeth} depending on the coffee.")
15
16  # this line is tricky, try to get it exactly right
17 total = my_age + my_height + my_weight
18  print(f"If I add {my_age}, {my_height}, and {my_weight} I get {total}.")
```

## 你会看到

练习 5 会话

```py
1.  `$ python3.6 ex5.py`2.  `Let's talk about Zed A. Shaw. He's 74 inches tall.`3.  `He's 180 pounds heavy.`4.  `Actually that's not too heavy.`5.  `He's got Blue eyes and Brown hair.`6.  `His teeth are usually White depending on the coffee.`7.  `If I add 35, 74, and 180 I get 289.`
```

## 附加练习

*   修改所有的变量，把前面的 `my_` 删掉。要更改所有的变量名，而不只是有 `=` 的部分。
*   试着写一些变量，把英尺（inches）和英镑（pounds）换算成厘米（ centimeters）和千克（kilograms），别自己直接把自己的数据进去，用 python 的数学运算来换算。

## 常见问题

**我能创建一个这样的变量吗：1 = 'Zed Shaw'？**不能，`1` 不是一个有效的变量名。变量名需要以字母开头，比如 `a1` 就可以，但 `1` 不行。

**我如何给浮点数四舍五入取整数？**你可以用 `round()` 函数，比如：`round(1.7333)`。

**为什么我还是不理解这些代码？**试着把这些数字换成你自己的。虽然有点奇怪，但是与你自己相关能够让这些代码看起来更接地气。而且，你还刚开始学习，肯定会有不理解的地方。继续努力，再做一些练习你就会慢慢理解的。