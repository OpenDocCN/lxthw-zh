# 练习 27 记忆逻辑

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.32.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.32.learn-py3.md)

今天你将开始学习逻辑（logic）。目前为止你已经完成了很可能让你会在终端读写文件的所有内容，并且还学习了相当多 Python 中的数学计算。

从现在开始，你将开始学习逻辑。你不会学习学院派喜欢教的那套复杂理论，而只是简单的基本逻辑，它们是一些能让真实的程序运行，以及真正的程序员每天都需要的东西。

学习逻辑需要你先做一些记忆工作。我希望你能花一整个星期的时间来做这个练习。不要中途放弃，哪怕你已经烦闷不堪，坚持学下去。这个练习有一个逻辑表，你必须记住它们，这样在做后面的练习时才能更容易一些。

我得告诉你，这个练习一开始不会很有趣，甚至会冗长乏味，但是它会教给你作为程序员所需的一项重要技能。你需要记住这些重要的理念，当你掌握它们的时候，你会发现其中大多理念都非常令人激动。你会苦苦思索，就像 跟章鱼搏斗（wrestling a squid），直到有一天你最终理解它们。所有记忆工作的付出会在之后给你丰厚的回报。

以下是一些让你不至于抓狂的记忆技巧：

一天少记一些内容，给需要强化记忆的部分做上标记；别妄图一坐坐两个小时一下子把这些表全记住，这样不科学，你的大脑只会保留你前 15-30 分钟记的内容。相反，你应该创建一些索引卡，在表中左边列的内容（True or False）写在正面，右边的内容写在背面。然后你可以把它们拿出来，看着 “True or False” 直接说出 “True！”保持练习，直到你能够做到这样。

一旦你能够做到，你就可以开始每天晚上在笔记本上默写 truth table。不要只是复制，试着凭记忆默写。如果你卡住了，快速看一眼来刷新你的记忆。这样做会训练你的大脑记住整张表。

别花超过一个星期时间在这上面，因为随着你往下学习，你会逐步应用这些内容。

## The Truth Terms

在 Python 中我们有下面这些词条（字符和短语）来判断某些东西是 “True” 还是 “False” 。计算机的逻辑就是看这些字符和变量的组合在特定程序和特定点下是不是 True。


+    and 
+    or 
+    not 
+    != （不等于） 
+    == （等于） 
+    >= （大于等于） 
+    <= （小于等于） 
+    True 
+    False

你其实之前已经遇到过这些字符了，但是可能不是 terms。Terms （and, or, not）的运行方式就跟它们的意思一样。

## The Truth Tables

我们现在要用这些字符来帮你记忆 truth tables 的内容。

| **NOT** | **True?** |
| --- | --- |
| not False | True |
| not True | False |

| **OR** | **True?** |
| --- | --- |
| True or False | True |
| True or True | True |
| False or True | True |
| False or False | False |

| **AND** | **True?** |
| --- | --- |
| True and False | False |
| True and True | True |
| False and True | False |
| False and False | False |

| **NOT OR** | **True?** |
| --- | --- |
| not (True or False) | False |
| not (True or True) | False |
| not (False or True) | False |
| not (False or False) | True |

现在照着这些表来写下你自己的卡片，然后花一周的时间记忆它们。记住，这本书里没有失败，只有每天不断的尝试和坚持。

## 常见问题

**我可以只学习布尔代数（boolean algebra）背后的理论而不去记忆这些内容吗？**你当然可以这样做，但是之后你在写代码的时候就得不停地回顾布尔代数的那些规则了。如果你先把这些记住，不仅可以构建你的记忆技巧，还能让你的操作更自然。在这之后，布尔代数的理念就非常简单了。当然了，选择最适合你的方式吧。