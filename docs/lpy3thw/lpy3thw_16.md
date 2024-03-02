# 练习 12 提示用户

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.17.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.17.learn-py3.md)

当你输入 `()` 的时候，一定要确保输入完整，它们是成对出现的。对于 `input` 来说，你还可以给用户放一个提示，让他知道该输入什么。你可以把提示的字符串放在 `()` 里面，就像这样：

```py
y = input("Name?")
```

这个提示告诉用户输入“名字”，然后把结果放到变量 y 里面。通过这种方式你就可以问用户问题然后得到他输入的答案。

这意味着我们可以重新写我们之前的练习，就用 `input` 来做所有的提示。

ex12.py

```py
1 age = input("How old are you? ")
2 height = input("How tall are you? ")
3 weight = input("How much do you weigh? ")
4
5  print(f"So, you're {age} old, {height} tall and {weight} heavy.")
```

练习 12 会话

```py
1.  `$ python3.6 ex12.py`2.  `How old are you?  38`3.  `How tall are you?  6'2"`4.  `How much do you weigh? 180lbs`5.  `So, you're 38 old,  6'2" tall and 180lbs heavy.`
```

## 附加练习

*   在 Terminal 里输入 `pydoc input` ，看看它会说什么。如果你用的是 Windows， 输入 `python3.6 -m pydoc input` 。
*   输入 `q` ，退出 `pydoc` 。
*   到网上查查 `pydoc` 命令的作用。
*   用 `pydoc` 读一读关于 `open`，`file`，`os`，和 `sys` 的内容；浏览一遍即可，把有意思的东西记下来。

## 常见问题

**为什么我每次运行 `pydoc` 都会收到错误信息：`SyntaxError: invalid syntax`？** 要么你没在命令行运行 `pydoc`，要么你先运行了 python3.6，先退出 python3.6 再运行 `pydoc` 。

**为什么我的 `pydoc` 没有像你的一样暂停？** 有时候如果帮助文件很短，一屏足以放下的话，`pydoc` 就只会把它打印出来。

**当我运行 `pydoc` 的时候我会收到 `more is not recognized as an internal` 。** 一些 Windows 版本没有这个命令，你可以跳过这个小题，需要它的时候在网上搜搜 Python documentation 即可。

**为什么我不能用 `print("How old are you?", input()) ？`**你能，只不过 `input()` 的结果不会被保存到一个变量里，它会以一种奇怪的方式运行。你可以试试，然后试着打印你输入的东西，看看你能不能搞明白为什么它无法运行。