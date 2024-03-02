## 练习 8：手动格式化字符串

现在我们将看到如何对字符串进行更复杂的格式化。这段代码看起来复杂，但如果你在每一行上面做好注释，并将每个部分分解开来，你就会理解它。

代码清单 8.1: ex8.py

```py
 1   formatter = "{} {} {} {}"
 2
 3   **print(**formatter.**format(**1, 2, 3, 4**))**
 4   **print(**formatter.**format(**"one", "two", "three", "four"**))**
 5   **print(**formatter.**format(**True, False, False, True**))**
 6   **print(**formatter.**format(**formatter, formatter, formatter, formatter**))**
 7   **print(**formatter.**format(**
 8       "Try your",
 9       "Own text here",
10       "Maybe a poem",
11       "Or a song about fear"
12   **))**
```

### 你应该看到的内容

```py
1   1 2 3 4
2   one two three four
3   True False False True
4   {} {} {} {} {} {} {} {} {} {} {} {} {} {} {} {}
5   Try your Own text here Maybe a poem Or a song about fear
```

在这个练习中，我使用了一个叫做“函数”的东西，将 `formatter` 变量转换为其他字符串。

当你看到我写 `formatter.format(...)` 时，我是在告诉 Python 执行以下操作：

1.  取出第 1 行定义的 `formatter` 字符串。

2.  调用它的 `format` 函数，类似于告诉它执行一个名为 `format` 的命令行命令。

3.  传递给 `format` 四个参数，这些参数与 `formatter` 变量中的四个 `{}` 匹配。这就像向命令行命令 `format` 传递参数一样。

4.  在 `formatter` 上调用 `format` 的结果是一个新字符串，其中的 `{}` 被这四个变量替换。这就是 `print` 现在打印出来的内容。

这对于第八个练习来说有点多，所以我希望你把它当作一个脑筋急转弯。如果你不是*真的*理解发生了什么，也没关系，因为本书的其余部分会慢慢澄清这一点。此时，请尝试研究一下这个，并看看发生了什么，然后继续下一个练习。

### 学习任务

重复 练习 7 中的学习任务。

### 常见学生问题

**为什么我必须在“one”周围加引号，但不需要在** `True` **或** `False` **周围加引号？** Python 将 `True` 和 `False` 视为代表真和假概念的关键字。如果你在它们周围加上引号，那么它们就会变成字符串，无法正常工作。你将在后面学到更多关于它们如何工作的知识。

**我可以使用 IDLE 运行吗？** 不可以，如果你知道的话，应该使用 Jupyter 或命令行。学习编程是必不可少的，如果你想学习编程，这是一个很好的起点。Jupyter 比 IDLE 是一个更优秀的工具。
