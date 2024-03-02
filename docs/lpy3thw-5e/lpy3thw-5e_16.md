## 练习 14. 提示和传递

让我们做一个练习，结合使用`argv`和`input`来询问用户特定的事情。你将在下一个练习中需要这个，那里你将学习如何读写文件。在这个练习中，我们将稍微不同地使用`input`，让它打印一个简单的`>`提示。

列表 14.1: ex14.py

```py
 1   **from** sys **import** argv
 2
 3   script, user_name = argv
 4   prompt = '> '
 5
 6   **print(**f"Hi {user_name}, I'm the {script} script."**)**
 7   **print(**"I'd like to ask you a few questions."**)**
 8   **print(**f"Do you like me {user_name}?"**)**
 9   likes = **input**(prompt)
10
11   **print(**f"Where do you live {user_name}?"**)**
12   lives = **input(**prompt**)**
13
14   **print(**"What kind of computer do you have?"**)**
15   computer = **input(**prompt**)**
16
17   **print(**f"""
18   Alright, so you said {likes} about liking me.
19   You live in {lives}. Not sure where that is.
20   And you have a {computer} computer. Nice.
21   """**)**
```

我们创建一个名为`prompt`的变量，设置为我们想要的提示，并将其提供给`input`，而不是一遍又一遍地输入。现在，如果我们想要将提示更改为其他内容，我们只需在这一个地方更改它，然后重新运行脚本。非常方便。

警告！

记住，你必须像在 Exercise 13 中那样做，并使用终端使其工作。这将是一段时间内的最后一次，但重要的是要知道如何从终端运行代码，因为这是运行 Python 代码的一种常见方式。

### 你应该看到的内容

运行此代码时，请记住必须为`argv`参数提供你的名字。

```py
 1   $ python ex14.py zed
 2   Hi zed, I'm the ex14.py script.
 3   I'd like to ask you a few questions.
 4   Do you like me zed?
 5   > Yes
 6   Where do you live zed?
 7   > San Francisco
 8   What kind of computer do you have?
 9   > Tandy 1000
10
11   Alright, so you said Yes about liking me.
12   You live in San Francisco. Not sure where that is.
13   And you have a Tandy 1000 computer. Nice.
```

### 学习练习

1\. 找出 Zork 和 Adventure 是什么游戏。尝试找到一份副本并玩一玩。

2\. 将`prompt`变量完全更改为其他内容。

3\. 添加另一个参数，并在你的脚本中使用它，就像在上一个练习中使用`first, second = ARGV`一样。

4\. 确保你理解我是如何将`"""`样式的多行字符串与`{}`格式激活器结合在一起作为最后一个打印的。

5\. 尝试找到在 Jupyter 中运行此代码的方法。你可能需要用其他东西替换使用`argv`的代码，比如一些变量。

### 常见学生问题

**当我运行这个脚本时，我收到** `SyntaxError: invalid syntax`。再次强调，你必须在命令行上正确运行它，而不是在 Python 内部。如果你输入`python3`然后尝试输入`python3 ex14.py Zed`，它将失败，因为你是在*Python 内部运行 Python*。关闭窗口，然后只需输入`python3 ex14.py Zed`。

**我不明白你所说的改变提示是什么意思**。看看变量`prompt = '> '`。将其更改为其他值。你知道这个；这只是一个字符串，你已经做了 13 个练习来创建它，所以花点时间弄清楚。

**我收到错误** `ValueError: need more than 1 value to unpack`。记得我说过你需要查看*你应该看到的内容*（WYSS）部分并复制我做的吗？你需要在这里做同样的事情，关注我如何输入命令以及为什么要有命令行参数。

**我如何从 IDLE 运行这个？** 不要使用 IDLE。它很糟糕。

**我可以为** `prompt` **变量使用双引号吗？** 完全可以。试试看吧。

**你有一台 Tandy 电脑吗？** 我小时候有过。

**当我运行它时，我收到** `NameError: name 'prompt' is not defined`。你要么拼错了`prompt`变量的名称，要么忘记了那一行。回去逐行比较我的代码和你的代码，从脚本底部到顶部。每当你看到这个错误时，意味着你拼写错了或忘记创建变量。
