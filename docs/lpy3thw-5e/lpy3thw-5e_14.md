## 练习 12. 更简单的提示方式

当你输入`input()`时，你实际上输入了`(`和`)`字符，这些是`括号`字符。对于`input`，你也可以输入一个提示，让人知道该输入什么。在`()`内放入你想要的提示字符串，看起来像这样：

```py
y = **input**("Name? ")
```

这提示用户输入“姓名？”，并将结果放入变量`y`中。这就是你向某人提问并得到答案的方式。

这意味着我们可以完全重写我们之前的练习，只需使用`input`来进行所有提示。

列表 12.1: ex12.py

```py
1   age = **input(**"How old are you? "**)**
2   height = **input(**"How tall are you? "**)**
3   weight = **input(**"How much do you weigh? "**)**
4
5   **print(**f"So, you're {age} old, {height} tall and {weight} heavy."**)**
```

### 你应该看到什么

```py
1   How old are you? 38
2   How tall are you? 6'2"
3   How much do you weigh? 180lbs
4   So, you're 38 old, 6'2" tall and 180lbs heavy.
```

### 学习练习

1\. 在你的 Jupyter 单元格中右键点击任何`print`，然后选择`显示上下文帮助`。这将为`print`提供快速文档。

2\. 如果你这样做，面板上会显示“点击函数查看文档。”，那么你需要用`SHIFT-ENTER`运行代码，然后再次点击`print`函数。

3\. 接下来，去[Google](https://google.com)搜索`python print site:python.org`以获取 Python `print`函数的官方文档。

### 常见学生问题

**为什么上下文帮助会消失？** 我不确定，但我怀疑它无法在你编辑代码时找到你想要文档的函数。运行代码，然后突然它就会起作用。你也可以点击你工作的任何其他单元格中的任何其他函数。

**这些文档是从哪里来的？** 这些是添加到代码本身的文档注释，这就是为什么它可能与在线文档不同的原因。养成在可能的情况下同时学习两者的习惯。
