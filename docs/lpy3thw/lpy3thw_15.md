# 练习 11 问问题

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.16.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.16.learn-py3.md)

现在可以缓一缓了。前面我们做了大量的打印练习，以让你熟悉这些简单的东西，但是的确，它们很无聊。我们现在要做的是在你的程序里放入数据。这块有点复杂，因为你得学着做两件你可能一下子理解不了的事情。但是相信我，无论如何先试试看。做几个练习之后你就会明白。

大多数软件就是做如下事情：

*   从用户那里获得一些输入。
*   改一改。
*   打印出来一些东西以显示它变成了什么。到现在为止你一直在打印东西，但是你还不知道怎么从用户那里获得 `input`（输入）。你甚至不知道“input”是什么意思。不管怎样，准确无误地输入这些代码，在下一个练习中我们会做更多的操作来解释 `input` 。

ex11.py

```py
1  print("How old are you?",  end=' ')
2 age = input()
3  print("How tall are you?",  end=' ')
4 height = input()
5  print("How much do you weigh?",  end=' ')
6 weight = input()
7
8  print(f"So, you're {age} old, {height} tall and {weight} heavy.")
```

| 警告！ |
| --- |
| 我们在每一个打印行末尾放一个 `end=' '` ，是为了告诉 print 不要另起一行。 |

## 你会看到

练习 11 会话

```py
$ python3.6 ex11.py
How old are you?  38
How tall are you?  6'2"
How much do you weigh? 180lbs
So, you're 38 old,  6'2" tall and 180lbs heavy.
```

## 附加练习

*   上网查查 python 的 `input` 是干嘛的。
*   你能找到它的其他使用方式吗？输入你找到的一些例子。
*   再写一个像这样的格式，来问一些问题。

## 常见问题

**我如何从别人那里获得一些数字来做数学运算？** 这就有点高级了，你可以试试输入 `x = int(input())` ，这样可以从 `input()` 里面获取到字符串形式的数字，再用 `int()` 把它们转化成数值。

**我把我的体重作为 `input` 像这样输入进去：`input("6'2")` ，但是不能正常运行。** 你别把你的体重放在那儿，你得直接在 Terminal 里面输入。首先，回去输入我让你输的代码；然后，运行脚本，当它暂停的时候，用你的键盘输入你的体重。这才是正确的做法。