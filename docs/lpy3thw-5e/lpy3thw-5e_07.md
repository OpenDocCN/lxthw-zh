## 练习 5：更多变量和打印

现在我们将更多地输入变量并将它们打印出来。这次我们将使用一种称为“格式化字符串”的东西。每当你在文本周围加上`"`（双引号）时，你就在制作一个*字符串*。字符串是你如何制作程序可能提供给人类的东西。你打印字符串，将字符串保存到文件中，将字符串发送到 Web 服务器等等。

字符串非常方便，所以在这个练习中，你将学习如何制作包含嵌入变量的字符串。你通过使用特殊的`{}`序列将变量嵌入字符串中，然后将你想要的变量放在`{}`字符中。你还必须以字母`f`开头，表示“格式”，就像`f"Hello {somevar}"`一样。在`"`（双引号）和`{}`字符之前加上这个小`f`告诉 Python 3，“嘿，这个字符串需要格式化。把这些变量放进去。”

和往常一样，即使你不理解也要输入这些内容，并确保完全一样。

列表 5.1：ex5.py

```py
 1   my_name = 'Zed A. Shaw'
 2   my_age = 35 # not a lie
 3   my_height = 74 # inches
 4   my_weight = 180 # lbs
 5   my_eyes = 'Blue'
 6   my_teeth = 'White'
 7   my_hair = 'Brown'
 8
 9   print(f"Let's talk about {my_name}.")
10   print(f"He's {my_height} inches tall.")
11   print(f"He's {my_weight} pounds heavy.")
12   print("Actually that's not too heavy.")
13   print(f"He's got {my_eyes} eyes and {my_hair} hair.")
14   print(f"His teeth are usually {my_teeth} depending on the coffee.")
15
16   # this line is tricky, try to get it exactly right
17   total = my_age + my_height + my_weight
18   print(f"If I add {my_age}, {my_height}, and {my_weight} I get {total}.")
```

### 你应该看到的内容

```py
1   Let's talk about Zed A. Shaw.
2   He's 74 inches tall.
3   He's 180 pounds heavy.
4   Actually that's not too heavy.
5   He's got Blue eyes and Brown hair.
6   His teeth are usually White depending on the coffee.
7   If I add 35, 74, and 180 I get 289.
```

### 学习扩展

1.  将所有变量中的`my_`都去掉。确保你在所有地方都修改了名称，不仅仅是在使用`=`设置它们的地方。

2.  尝试编写一些变量，将英寸和磅转换为厘米和千克。不要只是输入测量值。在 Python 中进行数学计算。

### 常见学生问题

**我可以像这样定义一个变量吗：** `1 = 'Zed Shaw'`**？** 不可以，`1`不是一个有效的变量名。变量名需要以字符开头，所以`a1`是可以的，但`1`是不行的。

**如何将浮点数四舍五入？** 你可以像这样使用`round()`函数：`round(1.7333)`。

**为什么我看不懂这个？** 尝试将脚本中的数字改为你的测量值。这有点奇怪，但谈论自己会让它看起来更真实。而且，你刚刚开始，所以不会太有意义。继续前进，更多的练习会让你更好地理解。
