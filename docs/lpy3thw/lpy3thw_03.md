# 前言

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.3.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.3.learn-py3.md)

这本简单的小书是为了让你开始编程。虽然书名说是“笨办法”，但其实不然。所谓“笨办法”只是本书教授的方法，也就是按照我的要求重复做一系列的练习来构建你的技能。这种方法对于零基础想要掌握基本编程技能的人来说非常有效，它几乎被用于所有的学习，从武术、音乐，到基础数学和阅读技巧。

这本书指导你通过练习和记忆逐渐建立起 Python 的使用技巧，然后用在更复杂的问题上。学完本书，你将会拥有开始学习更复杂编程所需的工具。我很喜欢告诉别人，我的书可以让你拥有“编程黑带”，也就是你已经掌握要开始学习编程的最基本的知识。

如果你肯努力，肯花时间来建立起这些技巧，你将可以正式学习编程。

## 第四版更新

《笨办法学 Python》第四版用了 Python 3.6。Python 3.6 升级了字符串格式系统，相比于之前的 4 或者 4 更好用，虽然对于初学者来说，学习 Python 3.6 会有很多问题，一个很明显的问题就是它的报错信息非常少，但是我将会帮助你理解从而解决这些问题。

同时，我也根据我过去五年来教授 Python 的经验，更新了视频课程。过去的视频只是简单地让你看着我做练习，而第四版加入了打乱再重新修复的练习，这个技巧叫做“调试”（debuging），它将会叫你如何修复你遇到的问题以及 Python 是如何运行你创建的程序。这个新方法的目标就是建立一种关于 Python 如何运行代码的思维模式，从而能够更容易看出来哪里出了问题。此外，你还会学到很多有用的调试错误程序的有用技巧。

最后，第四版从头到尾完全支持 Windows 10，以前版本更多地专注于基于 Unix 的系统比如 MacOS 和 Linux。而当我开始写第四版的时候微软已经开始认真对待开源工具和开发者，因为作为一个严肃的 Python 开发平台，真的很难忽略他们。视频教程将着重讲解 Windows 系统下 Python 的使用，当然也会展示 MacOS 和 Linux 系统下的操作。我将会告诉你每个平台的安装教程以及其他相关的技巧。

## 致谢

我想感谢 Angela 在这本书的前两版中对我的帮助，没有她我可能很难完成。她做了第一版的复制编辑工作，并且在我写作的过程中给我提供了极大的支持。

我同样要感谢 Greg Newman 为我设计封面，Brian Shumate 所做的网站设计，以及所有读过这本书并花时间给我反馈和更正意见的读者。

谢谢你们。

## 笨办法更简单

在这本书的帮助下，你将会做所有程序员学习一门编程语言都会做的非常简单的事情：

**1\. 做好每一个练习；**

**2\. 准确敲好每一个程序；**

**3\. 让它运行。**

就是这样。刚开始可能会比较难，但坚持下去。如果你通读了这本书，每晚花个一两小时做做习题，你将能够为自己读下一本编程书打下良好的基础。这本书不会让你一夜之间变成程序员，但是它将会带你走上学习如何编程的道路。

这本书的目的是教会你作为编程新手所需的三种最重要的技能：**读和写、注重细节、发现不同**。

### 一、读和写

如果你连打字都不行，那你学习编程也会成问题。尤其如果你连程序源代码中的那些奇怪字符都打不出来，就别提编程了。没有这些基本技能，你将连最基本的软件工作原理都难以学会。

所以，把代码示例打出来并运行，能够帮助你学习各种符号的名称、更熟练地敲出来、以及读懂编程语言。

### 二、注意细节

区分好程序员和差程序员的一个重要标准，就是对细节的注重程度，事实上，这也是任何行业区分好坏的标准。如果缺乏对工作中每个微小细节的注意，你的工作成果将缺乏重要的元素。拿编程来讲，主意细节将会让你远离各种 bug 和难用的系统。

通过这本书的学习，以及准确打出每一个例子，你将能够训练你的大脑，在做练习的时候更多地关注细节。

### 三、发现不同

程序员长年累月的工作会培养出一个重要技能，那就是对于不同点的区分能力。一个有经验的程序员看到两个仅有细微差别的程序，可以立即指出其中的不同。程序员还造出工具来让这件事更加容易，不过我们不会用到这些工具。你要先用笨办法训练自己，然后再用工具。

在你做这些练习并敲代码的时候，你一定会出错。这是不可避免的，即使有经验的程序员也会偶尔写错。你的任务是把自己写的东西和要求的正确答案对比，把所有的不同点都修正过来。这样做可以让你对程序里的错误、bug 以及其他问题更加敏感。

### 四、要问，不要盯着看

你只要写代码，就会出现 bug。Bug 意味着你写的代码有瑕疵、有错误、或者有问题。Bug 来源于一个传说，从前有一只飞蛾飞进了第一台计算机，造成了故障。修复它就需要“debugging”。在软件世界里，有着不计其数的 bug。

就像第一只飞蛾，你的 bugs 将会藏在你代码的某处，你必须找到它们。你不能只是坐在电脑前盯着屏幕上的代码，希望答案能自己跳出来。这样做不会有额外的信息，你需要额外的信息来解决问题，所以你得起来寻找这只飞蛾。

怎么寻找呢？你需要审问你的代码，问它现在是怎么回事儿，或者从另一个不同的视角去看待这个问题。在这本书里，我将会频繁地告诉你“别盯着看，要问”。我将会向你演示如何让你的代码告诉你正在发生的一切，并且如何找到可能的解决方案。我还会教你一些从不同角度看代码的方法，让你能够获取更多信息和洞见。

### 五、不要复制粘贴

你必须手动将每个练习打出来。复制粘贴会让这些练习变得毫无意义。这些习题的目的是训练你的双手和大脑思维，让你有能力读代码、写代码、观察代码。如果你复制粘贴，那你就是在欺骗自己，这些练习的效果也将大打折扣。

### 六、一个关于坚持练习的忠告

在你通过这本书学习编程时，我正在学习弹吉他。我每天至少练习 2 个小时，至少花一个小时练习音阶、和声、和弦，剩下的时间用来学习音乐理论和歌曲演奏以及训练听力等。有时我一天会花 8 个小时来练习，因为我觉得这是一件有趣的事情。对我来说，重复性练习是学好一样东西最自然而然的方法。并且我深知，要掌握一件事情，只有每天坚持练习。虽然有时候，我整个人状态很差（甚至经常这样），或者觉得实在太难。没关系，坚持尝试，到最后你会发现它越来越简单，并且开始越来越有趣。

在我写《笨办法学 Python》和《笨办法学 Ruby》的过程中，我发现了绘画的乐趣。我在自己 39 岁的时候爱上了这门视觉艺术，并且像学习吉他、音乐和编程一样每天花时间学习画画。我收集了相关的教材，并且按照书中所说，每天坚持画，同时专注于享受这种学习过程的乐趣。我完全不是一个艺术家，甚至差得很远，但我现在至少可以说我会画画了。我学习画画的方法就跟我在这本书里教你的一样。如果你把整个问题分解为一个个小练习和课程，并且每天做，你就可以学会几乎所有的东西。如果你专注于细微的进步，并且享受学习过程，你将会从中获益，无论你最后擅长到何种程度。

当你通过这本书学习编程的时候，要记住任何值得做的事情一开始都是困难的。也许你是一个害怕失败的人，一碰到困难就想放弃；也许你是一个缺乏自律的人，一碰到“无聊”的事情就不想上手；也许因为有人夸你“天赋异禀”而让你自视甚高，不愿意做这些看上去很笨拙的事情，怕有负你”神童”的称号；也许你太过激进，把自己跟有 20 多年经验的编程老手相比，让自己失去了信心。

无论是什么原因让你想要放弃，你一定要坚持下去。如果你碰到做不出来的课后练习，或者碰到一节看不懂的练习，你可以暂时跳过去，过一阵子回来再看。只要坚持下去，你总会弄懂的，因为编程的过程中总是会出现这样的问题。

一开始你可能什么都看不懂。这会让你感觉很不舒服，就像学习人类的自然语言一样。你会发现很难记住一些单词和特殊符号的用法，而且会经常感到很困惑。但是突然有一天，你一下子变得豁然开朗，以前不明白的东西忽然就明白了。如果你坚持练习下去，坚持去上下求索，你最终会学会这些东西。你可能不会成为一位编程大师，但你至少会明白程序是怎么运行的。

如果你放弃的话，你将永远达不到那种“豁然开朗”的时刻。你会在第一次碰到不明白的东西时（一开始就是所有东西）就选择放弃。如果你坚持尝试，坚持练习下去，坚持去弄懂习题的话，你最终一定会明白其中的内容。

如果你通读了这本书，却还是不知道怎么编程，那也没关系，至少你试过了。你可以说你已经尽过力但成效不佳，但至少你试过了。这也是一件值得你骄傲的事情。