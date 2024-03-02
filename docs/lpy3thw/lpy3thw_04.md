# 练习 0 配置环境

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.4.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.4.learn-py3.md)

这个练习没有代码。它只是为了让你的计算机准备好运行 Python。你应该严格按照步骤来。**（如果配置过程中遇到问题，可以在公众号“学习癌”后台留言，小编会为你答疑解惑。）**

| 警告！ |
| --- |
| 如果你不知道如何使用 Windows 上的 Powershell，MacOS 上的 Terminal,或者 Linux 上的 bash，你需要在进行下面的学习之前先做一下附录 A 中的练习。 |

## MacOS

做如下任务以完成练习:

*   去 [`www.python.org/downloads/release/python-360/`](https://www.python.org/downloads/release/python-360/) 上下载 “macOS 64-bit/32-bit installer”，像安装其他软件一样安装它。
*   去 [`atom.io/`](https://atom.io/) 下载 Atom 文本编辑器, 然后安装。如果你用不惯 Atom，可以在这个练习的最后选择其他可用的编辑器。
*   把 Atom 放在 Dock 中，以便快速打开。
*   用苹果电脑搜索功能找到你的 Terminal 程序，找不到的话就想想办法，你可以的。
*   把 Terminal 也放在 Dock.
*   运行 Terminal 程序，它看起来不咋滴。
*   在 Terminal 中运行 python3.6。在 Terminal 中运行程序只需要输入程序名然后敲 `Return` 即可。
*   输入 `quit()`, `Enter`, 然后退出 `python3.6`。
*   你应该回到你输入 `python` 之前看到的提示界面，如果不是，弄明白是什么原因。
*   学会如何在 Terminal 中创建目录。
*   学会如何在 Terminal 中切换目录。
*   用你的编辑器在这个目录下创建一个文件，你可以先在编辑器里编辑，然后点击“保存”或者“另存为”，选择你创建的目录文件夹。
*   用键盘快捷键切换回 Terminal 程序。
*   回到 Terminal 后，用 `ls` 列示目录以查看你新建的文件。

### 0.1.1 MacOS: 你应该看到的

这是我在自己苹果电脑 Terminal 终端操作完的会话。你的可能会稍有不同，但大体应该是差不多的。

```py
1.  `$ python3.6`2.  `Python  3.6.0  (default,  Feb  2  2017,  12:48:29)`3.  `[GCC 4.2.1  Compatible  Apple LLVM 7.0.2  (clang -700.1.81)] on darwin`4.  `Type  "help",  "copyright",  "credits"  or  "license"  for more information`5.  `>>>`6.  `~ $ mkdir lpthw`7.  `~ $ cd lpthw`8.  `lpthw $ ls`9.  `# ...   Use your text editor here to edit test.txt....`10.  `lpthw $ ls`11.  `test.txt lpthw $`
```

## Windows

*   用浏览器访问 [`atom.io`](https://atom.io)，下载 Atom 并安装，你可能需要用管理员身份运行。
*   把 Atom 放在桌面或者快速启动栏以便快速访问，这些都可以在安装的时候进行设置。 **注**：如果你的电脑运行很慢，打不开 Atom，你可以在本练习最后选择其他编辑器。
*   在开始菜单搜索 Powershell，回车，运行。
*   在桌面创建 Powershell 快捷键，或者把它添加到快速启动栏以方便打开。
*   运行 Powershell （我之后会称它为 Terminal），它看起来不咋滴。
*   从 [`www.python.org/downloads/release/python-360/`](https://www.python.org/downloads/release/python-360/) 下载 Python 3.6 然后安装。记得勾选“把 Python 3.6 添加到路径”（add Python 3.6 to your path）复选框。
*   在 Powershell （Terminal）中输入 `python` 并回车，以运行 `Python`。 **注**：如果你输入 `Python` 但它没有运行，你需要重新安装 `Python` 并确保在安装过程中勾选了“把 Python 3.6 添加到路径”（add Python 3.6 to your path）复选框。
*   输入 `quit()` 以退出 `Python`。
*   你应该回到你输入 `python` 之前看到的提示界面，如果不是，弄明白是什么原因。
*   学会如何在 Powershell 中创建目录。
*   学会如何在 Powershell 中切换目录。
*   用你的编辑器在这个目录下创建一个文件，你可以先在编辑器里编辑，然后点击“保存”或者“另存为”，选择你创建的目录文件夹。
*   用键盘快捷键切换回 Powershell 程序。
*   回到 Powershell 后，用 `ls` 列示目录以查看你新建的文件。 从现在起，当我说“Terminal”或“Shell”时指的就是 Powershell。当我让你运行 Python 3.6 的时候你只用输入 `python` 即可。

### 1.2.1 Windows: 你应该看到

```py
1.  `> python`2.  `>>> quit()`3.  `> mkdir lpthw`4.  `> cd lpthw`5.  `...  Here you would use your text editor to make test.txt in lpthw`6.  `>`7.  `> dir`8.  `Volume  in drive C is`9.  `Volume  Serial  Number  is  085C—7E02`11.  ``Directory of C:\Documents and  Settings\you\lpthw``13.  ```04.05.2010  23:32  <DIR>  .```py14.  ```04.05.2010  23:32  <DIR>  ..```py 15.  ```04.05.201  0  23:32  6 test.txt```py16.  ```1  File(s)  6 bytes```py17.  ```2  Dir(s)  14  804  623  360 bytes free```py19.  ````>```py`
```

 ``如果你的显示跟我的略有不同也是正确的，但是大体上应该是一样的。

## Linux

Linux 系统五花八门，软件安装方式也各不相同。我假设如果你用的是 Linux，你是知道如何安装软件包的，下面是你的操作步骤：

*   用你的安装包管理器（package manager）安装 Python 3.6，如果无法安装，就从 [`www.python.org/downloads/release/python-`](https://www.python.org/downloads/release/python-) 360/ 上下载并安装。
*   用你的安装包管理器安装 Atom 编辑器。如果 Atom 不好用，你可以选择本练习最后的其他编辑器。
*   把 Atom 放到你的窗口管理（window manager）菜单，以方便快速访问。
*   找到你的 Terminal 程序，它可能叫 GNOME Terminal、Konsole、或者 xterm。
*   把你的 Terminal 也放在 Dock。
*   运行你的 Terminal 程序，它看起来不咋滴。
*   在你的 Terminal 程序中输入 `python3.6` 以运行 Python 3.6。如果无法运行，试试输入 `python`。
*   输入 `quit()` 然后敲 `enter` 退出 Python。
*   你应该回到你输入 `python` 之前看到的提示界面，如果不是，弄明白是什么原因。
*   学会如何在 Terminal 中创建目录。
*   学会如何在 Terminal 中切换目录。
*   用你的编辑器在这个目录下创建一个文件，你可以先在编辑器里编辑，然后点击“保存”或者“另存为”，选择你创建的目录文件夹。
*   用键盘快捷键切换回 Terminal 程序。
*   回到 Terminal 后，用 `ls` 列示目录以查看你新建的文件。

### 0.3.1 Linux: 你应该看到

```py
1.  `$ python`2.  `>>> quit()`3.  `$ mkdir lpthw`4.  `$ cd lpthw`5.  `# ...    Use your text editor here to edit test.txt ...`6.  `$ ls test.txt`7.  `$`
```

如果你的显示跟我的略有不同也是正确的，但是大体上应该是一样的。

## 从网上找答案

这本书中很重要的一部分就是要学会从网上搜索编程相关的东西。我会告诉你“从网上搜索”，你需要做的就是用搜索引擎找到答案。我之所以不直接告诉你答案而是让你自己去找，就是为了让你成为一个独立的学习者，能够自己从网上找到答案而不依赖于书本，这是我的目标。

## 给初学者的忠告

这个练习已经结束了，它的难易程度可能取决于你对你电脑的熟悉程度。如果你觉得很难，试着花时间去学习和克服困难，因为只有攻克了这些最基础的东西，你才能继续学习更多的编程技能。

如果有人告诉你学到这本书的某个练习就可以停下来，或者跳过某些练习，别去相信。任何对你隐瞒知识的人，或者更糟糕——让你从他们那里获得知识而不是通过你自己的努力去获取，都是在让你对他们形成依赖。别听他们的，老老实实地做这些练习，从掌握自我学习的本领。

程序员可能会让你用 MacOS 或者 Linux，因为他们很喜欢苹果电脑的字体和排版设计，或者觉得用 Linux 很酷。别听他们的，用你现在正在用的电脑系统就行，你需要的就是一个编辑器，一个终端，还有 Python。

最后，这个练习的目的就是为了让你准备好这三样东西，以便做后面的练习：

*   用文本编辑器写练习。
*   运行你写的练习。
*   如果出错就试着修复。
*   重复。 其他事情可能会烦扰到你，所以坚持按照以上计划来。

## 其他可选编辑器

文本编辑器对程序员来说非常重要，但是作为初学者，你只需要一个简单的编辑器即可。我推荐 Atom 是因为它是免费的，而且几乎在任何系统上都能运行。但是，Atom 可能不适合你的电脑，所以你也可以选择以下这些编辑器：

| 编辑器名称 | 适用系统 | 网址 |
| --- | --- | --- |
| Visual Studio Code | Windows, MacOS, Linux | [`code.visualstudio.com/`](https://code.visualstudio.com/) |
| Notepad++ | Windows | [`notepad-plus-plus.org/`](https://notepad-plus-plus.org/) |
| gEdit | Linux, MacOS, Windows | [`github.com/GNOME/gedit`](https://github.com/GNOME/gedit) |
| Textmate | MacOS | [`github.com/textmate/textmate`](https://github.com/textmate/textmate) |
| SciTE | Windows, Linux | [`www.scintilla.org/SciTE.html`](http://www.scintilla.org/SciTE.html) |
| jEdit | Linux, MacOS, Windows | [`www.jedit.org/`](http://www.jedit.org/) |

以上这些编辑器是根据好用程度排序的。由于这些项目可能被放弃、死掉、或者不再适用于你的电脑。所以如果你试了一个不行，就试试别的。而且以上排序是基于我自己的电脑，对于你的电脑来说情况可能不太一样。

如果你已经知道如何使用 Vim 或者 Emacs，那就放心用。如果你从来没用过，就不要考虑了。程序员可能会努力说服你用 Vim 或者 Emacs，但那只会让你误入歧途。你的目标是学习 Python，而不是学习 Vim 或者 Emacs。如果你尝试使用 Vim 但却不知道如何退出，就输入 `:q!` 或者 `ZZ`。``