# 练习 14 提示和传递

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.19.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.19.learn-py3.md)

让我们来做一个把 `argv` 和 `input` 结合在一起的练习来问用户一些特别的问题。这些问题会在你学习下一个练习中阅读和写文件的时候用到。在这个练习中我们会用一种不同的方式使用 `input` ，就是让它打印出一个简单的 `>` 提示符。这有点像 Zork 或者 Adventure 这两款游戏。

ex14.py

```py
1  from sys import argv
2
3 script, user_name = argv
4 prompt =  '> '
5
6  print(f"Hi {user_name}, I'm the {script} script.")
7  print("I'd like to ask you a few questions.")
8  print(f"Do you like me {user_name}?")
9 likes = input(prompt)
10
11  print(f"Where do you live {user_name}?")
12 lives = input(prompt)
13
14  print("What kind of computer do you have?")
15 computer = input(prompt)
16
17  print(f"""
18  Alright, so you said {likes} about liking me.
19  You live in {lives}. Not sure where that is.
20  And you have a {computer} computer. Nice.
21  """)
```

我们把用户提示符设置成变量 `prompt` ，然后把它赋给 `input` 而不是一遍遍地输入它们。现在如果我们想把提示符变成别的东西，只要修改一个地方，然后重新运行脚本即可，非常方便。

## 你会看到

当你运行脚本的时候，记住一定要把你的名字赋给这个脚本，让 `argv` 接收到你的名字。

练习 14 会话

```py
1.  `$ python3.6 ex14.py zed`2.  `Hi zed, I'm the ex14.py script.`3.  `I'd like to ask you a few questions.`4.  `Do you like me zed?`5.  `>  Yes`6.  `Where  do you live zed?`7.  `>  San  Francisco`8.  `What kind of computer do you have?`9.  `>  Tandy  1000`11.  ``Alright, so you said Yes about liking me.``12.  ``You live in  San  Francisco.  Not sure where that is.``13.  ``And you have a Tandy  1000 computer.  Nice.``
```

 `## 附加练习

*   查查看 Zork 和 Adventure 游戏是什么，找来玩玩。
*   把 `prompt` 变量改成别的东西。
*   在你的脚本里再加一个参数，就像之前练习中 `first, second = argv` 一样。
*   确定你理解了我是如何在最后一行把 `"""` 多行格式字符（style multiline string）和 `{}` 格式激活器（format activator）结合起来的。

## 常见问题

**我运行脚本的时候收到了 `SyntaxError: invalid syntax` 。**我再说一次，你得在命令行里运行它，而不是在 python 里。如果你输入 `python3.6`，然后再输入 `python3.6 ex14.py Zed` ，就会无法运行，因为你是在 python 里面运行 python。关掉窗口，然后只输入 `python3.6 ex14.py Zed` 。

**你说的“改变提示符”是什么意思？我不太理解。**看到这个变量 `prompt = '>'` 了吗？改变它的值。你知道的，它只是一个字符串，你已经做了 13 个练习来创建它们了，所以好好想想，把它弄明白。

**我收到了报错信息：`ValueError: need more than 1 value to unpack.`** 我前面说过，你需要看看“你会看到”那部分然后复制我的做法。这儿也一样，注意我是如何输入命令行的，以及我为什么有一个命令行参数。

**我如何从 IDLE 来运行这些？**不要用 IDLE。

**我能在 prompt 变量外面用双引号吗？**你完全可以，试试吧。

**你有一台 Tandy computer？**是的，在我很小的时候。

**我运行的时候收到了报错信息：NameError: name 'prompt' is not defined 。** 你要么把 `prompt` 变量拼写错了，要么把那行漏掉了。回过头去，从下到上比较每一行代码。你一旦遇到这种报错，就说明你拼写错误或者忘了创建变量。`