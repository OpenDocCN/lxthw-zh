## 练习 9：多行字符串

现在你应该意识到这本书的模式是使用多个练习来教授你新知识。我从你可能不理解的代码开始，然后更多的练习来解释概念。如果你现在不理解某些内容，随着完成更多练习，你以后会理解的。记下你不理解的内容，然后继续。

代码清单 9.1: ex9.py

```py
 1   # Here's some new strange stuff, remember type it exactly.
 2
 3   days = "Mon Tue Wed Thu Fri Sat Sun"
 4   months = "Jan\nFeb\nMar\nApr\nMay\nJun\nJul\nAug"
 5
 6   print("Here are the days: ", days)
 7   print("Here are the months: ", months)
 8
 9   print("""
10   There's something going on here.
11   With the three double-quotes.
12   We'll be able to type as much as we like.
13   Even 4 lines if we want, or 5, or 6.
14   """)
```

### 你应该看到的内容

```py
 1   Here are the days: Mon Tue Wed Thu Fri Sat Sun
 2   Here are the months: Jan
 3   Feb
 4   Mar
 5   Apr
 6   May
 7   Jun
 8   Jul
 9   Aug
10
11   There's something going on here.
12   With the three double-quotes.
13   We'll be able to type as much as we like.
14   Even 4 lines if we want, or 5, or 6.
```

### 学习扩展

重复来自练习 7 的学习扩展。

### 常见学生问题

**为什么我在三个双引号之间放空格时会出错？** 你必须像这样输入`"""`而不是`" " "`, 意思是*每个之间都没有*空格。

**如果我想要在新的一行开始月份怎么办？** 你只需像这样以`\n`开头的字符串：`"\nJan\nFeb\nMar\nApr\nMay\nJun\nJul\nAug"`。

**我的错误总是拼写错误，这是不好的吗？** 大多数编程错误在开始阶段（甚至后来）都是简单的拼写错误、打字错误或者简单事情的顺序错了。
