# 练习 36.设计和调试

# 练习 36.设计和调试

现在你已经学会了`if 语句`，我将给你一些使用`for 循环`和`while 循环`的规则，以免你日后碰到麻烦。我还会教你一些调试的小技巧，以便你能发现自己程序的问题。最后，你将需要设计一个和上节类似的小游戏，不过内容略有更改。

## IF 语句的规则：

> 1.  每一个“if 语句”必须包含一个 else.
> 2.  如果这个`else`永远都不应该被执行到，因为它本身没有任何意义，那你必须在 else 语句后面使用一个叫做`die`的函数，让它打印出错误信息,这和上一节的习题类似，这样你可以找到很多的错误。
> 3.  “if 语句”的嵌套不要超过 2 层，最好尽量保持只有 1 层。
> 4.  将“if 语句”当做段落来对待，其中的每一个`if-elif-else` 组合就跟一个段落的句子一样。在这种组合的最前面和最后面留一个空行以作区分。
> 5.  你的布尔测试应该很简单，如果它们很复杂的话，你需要将它们的运算事先放到一个 变量里，并且为变量取一个好名字。

如果你遵循以上规则，你就会写出比大部分程序员都好的代码来。回到上一节练习，看看我有没有遵循这些规则，如果没有的话，就将其改正过来。

> **Warning:**在日常编程中不要死板的遵守规则。在训练中，你需要通过这些规则的应用来巩固你学到的知识，而在实际编程中这些规则有时其实很蠢。如果你觉得哪个规则很蠢，就别使用它。

## 循环的规则

> 1.  只有在循环永不停止时使用“while 循环”，这意味着你可能永远都用不到。这条只有 Python 中成立，其他的语言另当别论。
> 2.  其他类型的循环都使用“for 循环”，尤其是在循环的对象数量固定或者有限的情况下。

## 调试的小技巧

> 1.  不要使用 “debugger”。`Debugger`所作的相当于对病人的全身扫描。你不会得到某方面的有用信息，而且你会发现它输出的信息大部分没有用，或者只会让你更困惑。
> 2.  最好的调试程序的方法是使用`print`,在各个你想要检查的关键环节将关键变量打印出来，从而检查哪里是否有错。
> 3.  让程序一部分一部分地运行起来。不要等一个很长的脚本写完后才去运行它。写一点，运行一点，修改一点。

## 家庭作业

写一个和上节类似的小游戏。任何题材的游戏都可以。尽量花一周的时间让这个游戏有趣一些，作为附加题，你可以尽量多的使用列表，函数和模块（还记得练习 13 吗？），而且，尽量弄一些新的 Python 代码让你的游戏运行起来。

在你开始编码之前，你应该先画一张地图出来，提前设计出玩家可能遇到的房间、怪物以及陷阱等。

当你画好了梯度，你就可以开始编码了。如果你发现地图有问题的话，修改一下，让代码和地图相匹配。

完成一个软件的最好方式是把它们拆解为像下面这样的小块：

> 1.  在纸上写下你完成这个软件所需要做的所有任务。这就是你的待办事项列表。
> 2.  先找到你列表中最容易的事情。
> 3.  在你的源代码中增加注释，作为你完成这项任务的指南。
> 4.  在这些注释下面，开始编码。
> 5.  然后立即运行你的代码，看它是否正常工作。
> 6.  循环的进行代码编写，测试运行，以及代码修正，直到代码正常运行。
> 7.  在你的列表中划掉刚完成的任务，然后再挑选下一个最容易完成的任务，重复进行以上步骤。

这套程序会帮助你在写代码的时候保持系统的、一致的风格。当你开始工作的时候，更新你的任务清单，增加你要做的，并删除已完成的。