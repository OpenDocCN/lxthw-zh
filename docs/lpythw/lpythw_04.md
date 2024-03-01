# 练习 0.安装和准备

# 练习 0.安装和准备

这道习题并没有代码内容，它的主要目的是让你在计算机上安装好 Python。你应该尽量照着说明进行操作，例如 Mac OSX 默认已经安装了 Python 2，所以就不要在上面安装 Python 3 或者别的 Python 版本了。

> **Warning:**如果你不知道怎样使用 Windows 下的 PowerShell，或者 OSX 下的 Terminal，或者 Linux 下的“bash”，那你就需要学习了。我有一个免费的快速入门教程放在 [`cli.learncodethehardway.org/`](http://cli.learncodethehardway.org/) 你可以快速学到 PowerShell 和 Terminal 的基本用法。学完后再回来看这本书吧。

## Mac OS X

你需要做下列任务来完成这个练习：

> 1.  用浏览器打开 [`www.barebones.com/products/textwrangler/`](http://www.barebones.com/products/textwrangler/) 下载并安装 `TextWrangler` 文本编辑器。
> 2.  把 `TextWrangler`(也就是你的编辑器) 放到 Dock 中，以方便日后使用。
> 3.  找到你的终端程序。 搜索一下，你就会找到它。
> 4.  同样将你的终端放到 Dock 中
> 5.  运行你的终端程序. 这个程序看上去不怎么地。
> 6.  在 Terminal 程序里边运行`python`。运行的方法是输入程序的名字再敲一下回车
> 7.  键入 quit(), 回车, 就能退出 python.
> 8.  这样你就应该退回到敲`python`前的提示界面了。如果没有的话自己研究一下为什么.
> 9.  学着使用 Terminal 创建一个目录.
> 10.  学着使用 Terminal 进入一个目录.
> 11.  使用你的编辑器在你进入的目录下建立一个文件。你将建立一个文件。使用 “Save” 或者 “Save As...” 选项，然后选择这个目录.
> 12.  使用键盘切换回到 Terminal 窗口，如果不知道怎样使用键盘切换.
> 13.  回到 Terminal，使用`ls`命令看到你新建的文件.

## OS X: 你应该看到的结果

以下是我在自己电脑的 Terminal 中执行上述练习时看到的内容。和你做的结果会有一些不同，但是应该相差不多。

```py
Last login: Sat Apr 24 00:56:54 on ttys001
~ $ python
Python 2.5.1 (r251:54863, Feb  6 2009, 19:02:12)
[GCC 4.0.1 (Apple Inc. build 5465)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> ^D
~ $ mkdir mystuff
~ $ cd mystuff
mystuff $ ls
# ... Use TextWrangler here to edit test.txt....
mystuff $ ls
test.txt
mystuff $ 
```

## Windows

> 1.  浏览器打开[`notepad-plus-plus.org/`](http://notepad-plus-plus.org/) 下载并安装`notepad++` 编辑器，这个操作不需要用管理员权限。
> 2.  确定你可以方便的打开`notepad++`，你可以把它放到桌面或者快速启动栏，两种方式在安装的时候都可以选择。
> 3.  从开始菜单运行`PowerShell`程序。你可以使用开始菜单的搜索功能，输入名称后敲回车即可打开。
> 4.  为它创建一个快捷方式，放到桌面或者快速启动栏中以方便使用。
> 5.  运行你的`PowerShell`（后面我将称呼它为`Terminal`）。
> 6.  在 Terminal 程序里边运行 python。运行的方法是输入程序的名字再敲一下回车。
> 
> ```py
> 1\.  如果你运行 python 发现它不存在(系统找不到 python 云云)。你需要访问 [](http://python.org/download)[`python.org/download`](http://python.org/download) 并且安装 Python。
> 2\.  确认你安装的是 Python 2 而不是 Python 3。
> 3\.  你也可以试试 ActiveState Python，尤其是你没有管理员权限的时候。
> 4\.  如果你安装好了但是 python 还是不能被识别，那你需要在 powershell 下输入并执行以下命令： 
> ```

```py
>     5\. 关闭并重启`powershell`，确认`python`现在可以运行。如果不行的话你可能需要重启电脑。

> 1\. 键入 quit(), 回车, 就能退出 python。
> 1\. 这样你就应该退回到敲`python`前的提示界面了。如果没有的话自己研究一下为什么。
> 1\. 学着使用 Terminal 创建一个目录。
> 1\. 学着使用 Terminal 进入一个目录。
> 1\. 使用你的编辑器在你进入的目录下建立一个文件。你将建立一个文件，使用 “Save” 或者 “Save As...” 选项，然后选择这个目录。
> 1\. 使用键盘切换回到 Terminal 窗口，如果不知道怎样使用键盘切换， 你一样可以上网搜索.
> 1\. 回到 Terminal，使用`ls`命令看到你新建的文件.

从现在开始，当我说到`Terminal` 或者`shell`的时候，我指的是 `PowerShell`. 推荐你也用。

> **Warning:**有时这一步你会漏掉：Windows 下装了 Python 但是没有正确配置路径。 确认你在 powershell 下输入了 
```

~~~你也许需要重启 powershell 或者计算机来让路径设置生效。

## Windows:你应该看到的结果

```py
> python
ActivePython 2.6.5.12 (ActiveState Software Inc.) based on
Python 2.6.5 (r265:79063, Mar 20 2010, 14:22:52) [MSC v.1500 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> quit()
> mkdir mystuff
> cd mystuff
... Here you would use Notepad++ to make test.txt in mystuff ...
>
> dir
 Volume in drive C is
 Volume Serial Number is 085C-7E02

 Directory of C:\Documents and Settings\you\mystuff

04.05.2010  23:32    <DIR>          .
04.05.2010  23:32    <DIR>          ..
04.05.2010  23:32                 6 test.txt
               1 File(s)              6 bytes
               2 Dir(s)  14 804 623 360 bytes free 
```

如果你看到跟我的信息的不同，这仍然是正确的，但是也应该是相似的。

## Linux

Linux 系统可谓五花八门，安装软件的方式也各有不同。我们假设作为 Linux 用户的你已经知道如何安装软件包了，以下是给你的操作说明:

> 1.  使用 Linux 的包管理器下载并安装`gedit`.
> 2.  把 gedit (也就是你的编辑器)放到窗口管理器显见的位置，以方便日后使用。
> 
> ```py
> 1\.  运行 `gedit`，我们要先改掉一些愚蠢的默认设定。
> 2\.  从 `gedit menu` 中打开 `Preferences`，选择 `Editor` 页面。
> 3\.  将 `Tab width:` 改为 4。
> 4\.  选择 (确认有勾选到该选项) `Insert spaces instead of tabs`。
> 5\.  然后打开 “Automatic indentation” 选项。
> 6\.  转到 `View` 页面，打开 “Display line numbers” 选项。 
> ```
> 
> 1.  找到`Terminal`程序。它的名字可能是`GNOME Terminal``Konsole`、 或者`xterm`。
> 
> 1.  把 Terminal 也放到 Dock 里面。
> 2.  运行 Terminal 程序，
> 3.  在 Terminal 程序里边运行 python。运行的方法是输入程序的名字再敲一下回车.
> 
> ```py
> a. 如果你运行 python 发现它不存在的话，你需要安装它，而且要确认你安装的是 Python 2 而非 Python 3。 
> ```
> 
> 1.  键入 quit(), 回车, 就能退出 python.
> 
> 1.  这样你就应该退回到敲`python`前的提示界面了。如果没有的话自己研究一下为什么。
> 2.  学着使用 Terminal 创建一个目录.
> 3.  学着使用 Terminal 进入一个目录.
> 4.  使用你的编辑器在你进入的目录下建立一个文件。你将建立一个文件，使用 “Save” 或者 “Save As...” 选项，然后选择这个目录。
> 5.  使用键盘切换回到 Terminal 窗口，如果不知道怎样使用键盘切换， 你一样可以上网搜索.
> 6.  回到 Terminal，使用`ls`命令看到你新建的文件.

## Linux:应该看到的结果

```py
$ python
Python 2.6.5 (r265:79063, Apr  1 2010, 05:28:39)
[GCC 4.4.3 20100316 (prerelease)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
$ mkdir mystuff
$ cd mystuff
# ... Use gedit here to edit test.txt ...
$ ls
test.txt
$ 
```

如果你看到跟我的信息的不同，这仍然是正确的，但是也应该是相似的。

## 可以在网上找的东西

这本书最重要的一部分是学习在网络上研究编程的课题。如果我告诉你“在网上搜索这个问题的答案”，你要做的就是使用一个搜索引擎去找到答案。我让你自己搜索而不是直接告诉你答案的原因是因为我希望当你读完我的书之后，你能成为一个独立的学习者。如果你能在晚上找到自己需要的答案，你就离不需要我更近了一步，这正是我的目标。

多亏了谷歌等搜索引擎你能很容易的找到我告诉你 IDE 任何东西。如果我说“网上搜索 python list functions”，你应该这么样做：

> 1.浏览器打开[`google.com/`](http://google.com/)
> 
> 2.输入: `python list functions`3.阅读网页上列出来的最好的答案.

## 给新手的告诫

你已经完成了这节练习。这个练习对你而言可能会有些难，这要根据你对自己电脑的熟悉程度。如果你觉得有难度的话，你要自己克服困难，多花点时间学习一下。因为如果你不会这些基础操作的话，编程对你来说将会更难学习。

如果有人告诉你让你在书中一些特殊的练习题处停止或者跳过一些习题，你应该忽略他们。任何试图对你隐藏知识，更甚者，让你从他们而不是通过自己的努力获得知识的人，都在试图让你依赖他们而不是自己的技能。不要听他们的，要继续做练习题，这样你才能学习如何自学。

如果有程序员告诉你让你使用 vim 或者 emacs， 那你应该拒绝他们。当你成为 一个更好的程序员的时候，这些编辑器才会适合你使用。你现在需要的只是一个可以编辑文字的编辑器. 我们使用`gedit`,`TextWrangler``Notepad++`(从现在开始我们称呼它文本编辑器)是因为它很简单，而且在不同的系统上面使用起来是一样的,就连专业程序员也会使用这些编辑器，所以对于初学而言它已经足够了。

也许有程序员会告诉你让你安装和学习 Python3。 拒绝他们， 并告诉她们 “等你电脑里的所有 python 代码都支持 Python 3 了，我再试着学学吧。” 这句话足够他们忙活个十来年的了。再重复一次，不要使用 Python 3。Python 3 并未广泛的应用, 如果你学习了 Python2，当你需要 Python3 的时候，就能很容易的学会。如果你学了 Python3，你仍然需要学习 Python 2 来完成一些事情。只要学习 Python2 就好，忽略别人 Python3 才是未来的说法。

总有一天你会听到有程序员建议你使用 Mac OSX 或者 Linux。如果他喜欢字体美观，他会告诉你让你弄台 Mac OSX 计算机，如果他们喜欢操作控制而且留了一部大胡子，他会让你安装 Linux。再次说明，只要有一台手上能用的电脑就可以了。你需要的只有三样东西: 一个本文编辑器、一个命令行终端、还有 python。

最后，这节练习的准备工作的目的是帮助你在以后的练习中顺利地做到下面的这些事情：

> 1.  使用你的编辑器编写练习题，在 linux 上使用 gedit，在 OS X 上使用 TextWrangler，或者在 windows 上使用 Notepad++。
> 2.  运行你编写的习题.
> 3.  修改习题中的错误.
> 4.  重复以上步骤.