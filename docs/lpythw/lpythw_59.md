# 附录 A：命令行教程

# 附录 A：命令行教程

*   简介
*   安装和准备
*   路径, 文件夹, 名录 (pwd)
*   如果你迷路了
*   创建一个路径 (mkdir)
*   改变当前路径 (cd)
*   列出当前路径 (ls)
*   删除路径 (rmdir)
*   目录切换(pushd, popd)
*   生成一个空文件(Touch, New-Item)
*   复制文件 (cp)
*   移动文件 (mv)
*   查看文件 (less, MORE)
*   输出文件 (cat)
*   删除文件 (rm)
*   退出命令行 (exit)
*   下一步

# 附录 A-简介

# 附录 A-简介

### 简介：使用 shell 命令行

这个附录是使用命令行的快速教程。作为快速教程，这部分内容不会像我其他的书一样详细。它仅仅是为了让你能够像一个真正的程序员一样使用的电脑。当你完成这个附录的学习，你将学会大部分 shell 用户每天使用的命令，你将明白基本的目录以及一些其他的概念。

对于附录内容，我给你的唯一意见是：

```py
闭上嘴，练习输入每一个命令。 
```

很抱歉这么说，但是这就是你必须要做的。如果你对命令行有非理性的恐惧心理， 征服它的唯一办法就是闭嘴，并与之斗争。

你并不是要毁掉你的电脑。 You are not going to be thrown into some jail at the bottom of Microsoft's Redmond campus. 你的朋友不会因为你变成一个书呆子而嘲笑你。所以，忽略你对命令行所有的愚蠢而奇怪的心理吧。

为什么这么说？因为如果你想学习编程的话，你必须先学习命令行的使用。编程是用编程语言来控制你计算机的高级方式。而命令行则是编程语言的婴儿小弟弟。学习命令行是在教你控制计算机语言。 Once you get past that, you can then move on to writing code and feeling like you actually own the hunk of metal you just bought.当你通过了命令行的学习，你就可以继续编码，那种感觉就像你拥有了大块金属？？？

### 如何使用本附录

使用这个附录最好的办法是做到以下几点：

> *   给自己准备一个纸质笔记本和一支笔。
> *   从附录的开头开始，按照书中的要求完成每一项练习。
> *   当你读到一些你不明白的东西时，把他们记在笔记本上。留一点空间，这样你以后可以把答案写上。
> *   完成一个练习之后，退回去检查你在笔记本上记下的问题。尝试通过互联网或者你熟悉编程的朋友来获取答案。你也可以发邮件到 `help@learncodethehardway.org` 寻求帮助。

坚持做每一个练习，并写下你任何一个疑问，然后再想办法解决你的疑问。当你学完本附录之后，你会发现，你掌握的命令行知识比你想象的多得多。

### 你需要记下的东西

我提前警告你我会让你记住一些东西了。这是让你能掌握某些技能的最快的方式，但是对一些人来说，记忆可能是很痛苦的事情记忆对于学习任何东西都是很重要的技能，所以，你应该恐惧它。

这里是你如何记住东西的方法：

> *   告诉自己，你能记住它。不要试图寻找窍门或简单的方法，只要坐在那开始记忆就好。
> *   在索引卡片上写下你要记住的东西.把你要学的内容分成两部分，一半写在卡片的正面，一半写在背面。
> *   每天拿出 15-30 分钟时间，用做好的卡片训练自己，尝试回忆每一张卡片的内容。把任何你没有正确说出答案的卡片放到一边，针对这些卡片进行训练，直到你觉得厌烦，然后再尝试回忆所有的卡片，看你是否有所进步。
> *   睡觉之前，对你弄错了的卡在练习 5 分钟。

还有其他的方法，比如你可以把你要学习的内容写在一张纸上，然后将它贴在你浴室的墙上，当你洗漱的时候，你就可以不看着墙上的纸练习记忆这些内容，当你遇到问题的时候可以看一眼，刷新你的记忆。

如果你坚持每天都这样做，你应该能记住最多的事。 我想告诉你，练习记忆大约要一个星期到一个月。如果你这样做了，几乎所有的一切都变得更加容易和直观，这就是记忆的目的。 这并不是教你什么抽象的概念，而是一些根深蒂固的基础知识，你不需要思考它们就能脱口而出的知识。如果你记住了这些基础知识，它们就不会再是影响你学习更高级内容的拦路虎了。

# 附录 A-练习 1：安装

# 附录 A-练习 1：安装

本附录中，你需要完成 3 件事：

> *   用你的终端做一些事情 (command line, Terminal, PowerShell).
> *   了解你做过的事情.
> *   自己多练习.

在第一个练习中，你将学会如何打开你的终端并使用其工作，这样你才能完成本附录后面部分的学习。

### 做到这些

让你的终端保持工作状态，这样你就可以快速访问它，并了解它的工作原理。

### Mac OSX

在 Mac OSX 系统上，你应该

> *   按住 `command` 键，并敲空格键。
> *   屏幕顶部会弹出一个蓝色的“搜索框”。
> *   输入“terminal”。
> *   点击终端应用程序，这个程序的图标看起来有点像一个黑盒子。
> *   终端就打开了。
> *   现在你可以在你的 dock 中看到你终端的那个图表，选中它右键选择选项-->保留，这样你的终端就会一直保留在 dock 中了。

你现在已经打开了你的终端，并将它放在你 dock 中，这样你下次可以快速的打开它。

### Linux

如果你用的是 Linux 系统的话，我假设你知道如何打开你的终端。通过菜单窗口管理器查找叫做 shell 或者 terminal 的应用。

### Windows

在 windows 系统中，我们要使用 PowerShell。人们常用一个名为`cmd.exe`的程序协同工作，但是它并不像 PowerShell 好用。如果你有 Windows7 或以上版本,这样做：

> *   单击开始菜单
> *   在“搜索程序和文件”中输入“ powershell”。
> *   敲回车

如果你没有 Windows 7，你应该考虑升级你的系统。如果你坚持不想升级，你可以尝试从微软的下载中心安装它。网上搜索一下，找到"powershell 下载"。 安装适合你电脑的版本，虽然我没有 Windows XP，但我仍希望 PowerShell 的体验是一样的。

### 你应该学到的

你已经学会如何打开你的终端了，现在你可以继续学习本附录的其余部分了。

> **NOTE:**如果你有一些熟悉 Linux 系统的朋友，当他告诉用一些其他的东西替代 Bash 的时候，忽略他的话。我正在教你使用 bash。就是这样！即使他声称，ZSH 能让你提升 30 个 IQ 值甚至更多，忽视他！你的目标是在当前级别获得足够的能力，所以你用什么 shell 没有什么关系。接下来的警告是远离 IRC 或其他有黑色出没定的地方。他们认为破坏你的电脑很有趣。 命令`rm -rf /` 是一个最经典的你永远也不能使用的命令。躲开他们。如果你需要帮助，确保你是从你信任的地方获得答案，而不是从互联网上随便哪个白痴哪里得到帮助。

### 更多练习

这节练习有一个很大的“更多练习”部分。其他的练习是没有这么复杂的更多练习的， 但是，对于本附录的其余部分，我需要你用的大脑做一些记忆的事情。相信我：这会让以后的事情如丝般柔滑！

### Linux/Mac OSX

给下表中的命令创建索引卡片，把命令名称写在卡片的左侧，把命令的定义或功能写在右侧。当你继续本附录中的其他课程时，也要每天抽出时间练习它们。

pwd: 打印当前工作目录

hostname: 获取我的计算机的网络名称

mkdir: 创建目录

cd: 更改目录

ls: 列出目录下的文件

rmdir: 删除目录

pushd: push directory

popd: pop directory

cp: 复制文件或目录

mv: 移动/重命名文件或目录

less: 按页查看文件

cat: 输出整个文件

xargs: 执行参数

find: 查找文件

grep: 查找文件里面的东西

man: 阅读帮助手册

apropos: find what man page is appropriate

env: 查看计算机环境

echo: 输出一些参数

export: 设置一个新的环境变量

exit: 退出终端

sudo: 危险! 拥有超级用户权限!

### Windows

如果你用的是 windows 系统，你要熟记以下命令：

pwd: 打印当前工作目录

hostname: 获取我的计算机的网络名称

mkdir: 创建目录

cd: 更改目录

ls: 列出目录下的文件

rmdir: 删除目录

pushd: push directory

popd: pop directory

cp: 复制文件或目录

robocopy: 更强大的复制

mv: 移动/重命名文件或目录

more: 按页查看文件

type: 输出整个文件

forfiles: 对大量文件执行一个操作

dir -r: 查找文件

select-string: 查找文件里面的东西

help: 阅读帮助手册

helpctr: find what man page is appropriate

echo: 输出一些参数

set: 设置一个新的环境变量

exit: 退出终端

runas: 危险! 拥有超级用户权限!

练习、练习、练习! 练习到你看到一个词能马上说出它的功能。然后倒着练习，你看到一个功能，知道用什么命令实现它。

# 附录 A-练习 2：路径, 文件夹, 名录 (pwd)

# 附录 A-练习 2：路径, 文件夹, 名录 (pwd)

在这个练习中，你将学会使用`pwd`命令打印工作目录。

### 做到这些

我要教会你如何阅读这些我告诉你的“会话”。你不必输入我在这里列出的一切，练习输入其中的一部分就好：

> *   你不需要输入 `$` (Unix) 或`&gt;` (Windows). 这只是我向你展示你在我的会话中能看到什么。
> *   你在`$`或`&gt;`之后输入命令，然后敲回车。所以如果我写的是 `$ pwd`你只需要输入`pwd`并敲回车。
> *   紧跟着你可以在另一个`$` 或 `&gt;`符号后面看到结果输出。这些内容是输出，你应该看到了相同的输出

让我们使用一个简单的命令，你可以得到这样的窍门：

### Linux/OSX

```py
$ pwd
/Users/zedshaw
$ 
```

### Windows

```py
PS C:\Users\zed> pwd

Path
----
C:\Users\zed

PS C:\Users\zed> 
```

> **NOTE:**在本附录中，我需要节省空间，这样你可以更专注于命令的细节。为了达到这个目的，我会删除提示信息的第一部分 (上面例子中的`PS C:\Users\zed` 部分) ，并只留下符号`&gt;`部分。这意味着你的提示信息不会长的一模一样，不过不用担心这些。

记住从现在开始，在提示部分我只会留下`&gt;`。

对于 Unix 的提示，我也做了相同处理，但 Unix 的提示于 windows 不同，大多数习惯用`$`。

### 你应该学到的

你的提示信息与我的不同。你的提示信息可能在`$`之前有你的名字或者你电脑的名字。在 Windows 系统上，应该也是不同的。关键是你看到的模式：

> *   有一个提示。
> *   你可以在这里输入命令，这节中的例子是输入`pwd`。
> *   可以打印输出一些内容。
> *   重复以上内容。

你已经学到了`pwd`是做什么的，它的意识是“打印当前工作目录”。什么是一个目录？就是一个文件夹。文件夹和目录是一回事，它们可以互换使用。 当你在你的计算机上以图形方式打开文件浏览器查找文件的时候，你可以浏览你的整个文件夹。这些文件夹与我们所说的目录就是完全相同的东西。

### 更多练习

> *   输入 210 遍`pwd`，每次都要说 "打印当前工作目录"。
> *   写下这个命令输出给你的路径。使用你的图形文件浏览器找到它。
> *   还不够，你要再输入 20 遍，每一遍都要大声的朗读出来。

# 附录 A-练习 3：如果你迷路了

# 附录 A-练习 3：如果你迷路了

当你经历了这些说明，你可能会迷失自己。你可能不知道你在哪里或者再哪一个文件，而且也不知道该如何继续。为了解决这个问题，我要叫你一个命令，这个命令可以防止你在文件目录中迷失方向。

当你迷路的时候，最可能的原因是你执行了某些命令，但你不知道当前你在哪个目录下。此时，你应该输入命令 `pwd` 来打印当前目录。这个命令告诉你你在哪里。

接下来要做的事情就是你需要一种方式回到你的 home 目录。输入 `cd ~` 你将会回到你的 home 目录

也就是说，当你迷路的时候，你可以输入:

```py
pwd
cd ~ 
```

第一个命令`pwd` 告诉你你现在在哪来。第二个命令 `cd ~` 带你回到你的 home 目录。

### 做到这些

现在，找到你在哪来，然后通过使用 `pwd` 和 `cd ~`命令回到你的 home 目录。 这能保证你总是在正确的地方。

### 你应该学到的

如果你不知道你现在位于什么位置，你应该知道怎样回到 home 目录。

# 附录 A-练习 4：创建一个路径 (mkdir)

# 附录 A-练习 4：创建一个路径 (mkdir)

这节练习，你将学习如果使用`mkdir`命令创建一个新的目录（文件夹）。

### 做到这些

记住！ 你要先回到你的 home 目录！在你做这节练习之前，先执行`pwd`和`cd ~`操作。 在你做本附录的所有练习之前，都先回到 home 目录！

### Linux/OSX

```py
$ pwd
$ cd ~
$ mkdir temp
$ mkdir temp/stuff
$ mkdir temp/stuff/things
$ mkdir -p temp/stuff/things/frank/joe/alex/john
$ 
```

### Windows

```py
> pwd
> cd ~
> mkdir temp

    Directory: C:\Users\zed

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:02 AM            temp

> mkdir temp/stuff

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:02 AM            stuff

> mkdir temp/stuff/things

    Directory: C:\Users\zed\temp\stuff

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            things

> mkdir temp/stuff/things/frank/joe/alex/john

    Directory: C:\Users\zed\temp\stuff\things\frank\joe\alex

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            john

> 
```

这是我唯一一次给你列出 `pwd` 和 `cd ~` 命令。 它们预计会在每次练习中使用。随时使用它们。

### 你应该学到的

现在我们已经开始学习输入多个命令。这些都是可以运行`mkdir`的方式。 `mkdir`是做什么的？它能创建目录。你为什么问这个？你应该用你的索引卡片练习记忆这些命令。如果你不知道"`mkdir`创建目录"，那你应该继续使用索引卡练习。

创建一个目录是什么意思？你也可以把目录叫做文件夹。他们是同一种东西。 所有你上面做的事情是创建目录内的目录。这也可以叫做“路径”这是一个跟你说 "第一 temp, 然后 stuff, 接下来 things，这就是我想要的"的方式。这在你的计算机硬盘上就是一系列树形结构的文件夹。

> **NOTE:**在本附录中，我在所有路径中使用 `/` (slash) 字符，因为现在他们在所有计算机上都能正常工作。然而， Windows 系统使用者需要知道，你们也可以使用`\` (backslash)。

### 更多练习

> *   "path" 的概念可能会使你迷惑。别担心。我们将用他们做更多的练习，然后你就会理解了。
> *   在 temp 目录下创建 20 个其他的目录，这 20 个目录要在不同的层级上。通过你的图形文件浏览器看看你创建的目录。
> *   试试看创建一个名字中带有空格且被双引号包起来的目录：`mkdir "I Have Fun"`
> *   如果 temp 目录已经存在，那么你将得到一个错误。使用`cd`改变当前工作目录，然后再尝试创建不同目录。在 Windows 中，桌面是一个好地方。

# 附录 A-练习 5：改变当前路径 (cd)

# 附录 A-练习 5：改变当前路径 (cd)

这节练习中，你将学习如何使用 `cd`命令从一个目录切换到另一个。

### 做到这些

我打算再一次给你解释这些会话的内容：

> *   你不需要输入 `$` (Unix) 或 `&gt;` (Windows).
> *   你输入 stuff 然后敲回车。如果我是`$ cd temp` 你只需要输入`cd temp` 然后回车。
> *   输出会在你按下回车键之后展现，跟在另一个`$` 或 `&gt;` 提示符之后.
> *   永远先回到 home 目录! 执行 `pwd` 和 `cd ~`。

### Linux/OSX

```py
$ cd temp
$ pwd
~/temp
$ cd stuff
$ pwd
~/temp/stuff
$ cd things
$ pwd
~/temp/stuff/things
$ cd frank/
$ pwd
~/temp/stuff/things/frank
$ cd joe/
$ pwd
~/temp/stuff/things/frank/joe
$ cd alex/
$ pwd
~/temp/stuff/things/frank/joe/alex
$ cd john/
$ pwd
~/temp/stuff/things/frank/joe/alex/john
$ cd ..
$ cd ..
$ pwd
~/temp/stuff/things/frank/joe
$ cd ..
$ cd ..
$ pwd
~/temp/stuff/things
$ cd ../../..
$ pwd
~/
$ cd temp/stuff/things/frank/joe/alex/john
$ pwd
~/temp/stuff/things/frank/joe/alex/john
$ cd ../../../../../../../
$ pwd
~/
$ 
```

### Windows

```py
> cd temp
> pwd

Path
----
C:\Users\zed\temp

> cd stuff
> pwd

Path
----
C:\Users\zed\temp\stuff

> cd things
> pwd

Path
----
C:\Users\zed\temp\stuff\things

> cd frank
> pwd

Path
----
C:\Users\zed\temp\stuff\things\frank

> cd joe
> pwd

Path
----
C:\Users\zed\temp\stuff\things\frank\joe

> cd alex
> pwd

Path
----
C:\Users\zed\temp\stuff\things\frank\joe\alex

> cd john
> pwd

Path
----
C:\Users\zed\temp\stuff\things\frank\joe\alex\john

> cd ..
> cd ..
> cd ..
> pwd

Path
----
C:\Users\zed\temp\stuff\things\frank

> cd ../..
> pwd

Path
----
C:\Users\zed\temp\stuff

> cd ..
> cd ..
> cd temp/stuff/things/frank/joe/alex/john
> cd ../../../../../../../
> pwd

Path
----
C:\Users\zed

> 
```

### 你应该学到的

上节练习中你已经创建了所有的目录，你现在只需要使用`cd`命令，就能实现在它们之间进行切换。在上面我的会话中，我也使用`pwd`来检查我在哪里，所以一定记得不要输入命令`pwd`所输出的内容。比如，在第 3 行中，你看到`~/temp`，但是它是上面一个 `pwd`命令的输出。所以不要输入这行。

你应该看到我如何使用`..` 来移动到上一层目录的。

### 更多练习

学习在计算机上使用命令行模式(CLI)与图形用户界面(GUI)的一个非常重要的部分弄清楚他们是如何协同工作的。当我刚开始使用电脑时，是没有 GUI 的，我要做的一切都是用 DOS 提示符（命令行）来实现的.后来,当电脑变得足够强大,每个人都可以通过 GUI 操作电脑的时候,GUI 窗口和 CLI 目录文件夹协同使用对我来说是很简单的。

今天的大多数人，并不理解 CLI、路径和目录的概念。实际上，很难教会他们理解这些，唯一的学习方式是给你不断的使用 CLI，直到有一天你点击你在 GUI 中做的东西，而它能出现在 CLI 中。

做到这些的方法是你花一些时间找到你的 GUI 文件浏览器，然后通过你的 CLI 进入文件浏览器。这些是你下一步要做的事情：

> *   使用一个命令进入`joe`目录。
> *   使用一个命令回到`temp`目录，但不能使用上面例子中的命令。
> *   找到使用一个命令回到 "home 目录" 的方法。
> *   进入你的文件目录，然后使用你的 GUI 文件浏览器找到这个目录。
> *   进入你的下载目录，然后使用你的 GUI 文件浏览器找到这个目录。
> *   使用你的 GUI 文件浏览器找到另一个目录，然后使用`cd`进入这个目录。
> *   还记不记得你用引号包围一个名字中有空格的目录？你可以使用任何命令这么做。比如，你有一个目录叫做 `I Have Fun`，那你可以执行: `cd "I Have Fun"`

# 附录 A-练习 6：列出当前路径 (ls)

# 附录 A-练习 6：列出当前路径 (ls)

这节练习中你将学习如何使用`ls`命令列出一个目录下的所有内容。

### 做到这些

开始之前，确认你已经`cd`回到 temp 的上一层目录。.如果你不知道你在哪里，使用`pwd`找到你的位置，然后移动到正确的目录下。

### Linux/OSX

```py
$ cd temp
$ ls
stuff
$ cd stuff
$ ls
things
$ cd things
$ ls
frank
$ cd frank
$ ls
joe
$ cd joe
$ ls
alex
$ cd alex
$ ls
$ cd john
$ ls
$ cd ..
$ ls
john
$ cd ../../../
$ ls
frank
$ cd ../../
$ ls
stuff
$ 
```

### Windows

```py
> cd temp
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            stuff

> cd stuff
> ls

    Directory: C:\Users\zed\temp\stuff

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            things

> cd things
> ls

    Directory: C:\Users\zed\temp\stuff\things

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            frank

> cd frank
> ls

    Directory: C:\Users\zed\temp\stuff\things\frank

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            joe

> cd joe
> ls

    Directory: C:\Users\zed\temp\stuff\things\frank\joe

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            alex

> cd alex
> ls

    Directory: C:\Users\zed\temp\stuff\things\frank\joe\alex

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            john

> cd john
> ls
> cd ..
> ls

    Directory: C:\Users\zed\temp\stuff\things\frank\joe\alex

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            john

> cd ..
> ls

    Directory: C:\Users\zed\temp\stuff\things\frank\joe

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            alex

> cd ../../..
> ls

    Directory: C:\Users\zed\temp\stuff

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            things

> cd ..
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            stuff

> 
```

### 你应该学到的

`ls`能列出你当前目录中的所有内容。你可以看到我用`cd`切换到不同的目录下，然后列出该目录下的所有内容，这样，我就知道我接下来要到哪个目录中去了。

`ls`命令有很多的命令选项，当我们学习`help`命令之后，你将会学习如何得到这些命令选项的帮助信息。

### 更多练习

> *   输入这里的每一个命令！你必须亲手输入这些命令来学习他们。只是读他们并不够。
> *   在 Unix 中, 在`temp`目录下试试命令 `ls -lR`。
> *   在 Windows 中也可以试试 `dir -R`.
> *   使用`cd` 进入到你计算机上的其他目录，然后使用`ls`看看当前目录里有什么。
> *   将你遇到的新问题更新到你的笔记本中。我知道你可能已经有一些问题了，因为我并没有覆盖这些命令的所有点。
> *   记住，如果你迷路了，使用 `ls`和`pwd` 找到你在哪里，然后使用`cd`去到你要去的目录。

# 附录 A-练习 7：删除路径 (rmdir)

# 附录 A-练习 7：删除路径 (rmdir)

这节练习中，你将学习如何删除一个空目录。

### 做到这些

### Linux/OSX

```py
$ cd temp
$ ls
stuff
$ cd stuff/things/frank/joe/alex/john/
$ cd ..
$ rmdir john
$ cd ..
$ rmdir alex
$ cd ..
$ ls
joe
$ rmdir joe
$ cd ..
$ ls
frank
$ rmdir frank
$ cd ..
$ ls
things
$ rmdir things
$ cd ..
$ ls
stuff
$ rmdir stuff
$ pwd
~/temp
$ 
```

> **Warning:**如果你在 Mac OSX 上尝试执行 rmdir 命令，即使你确认这个目录是空的，但是计算机仍拒绝删除该目录，那么实际上应该是有一个名为`.DS_Store`的文件。这种情况下，你可以输入 `rm -rf &lt;dir&gt;` 来执行删除操作(将 `&lt;dir&gt;` 替换为你要删除的目录名)。

### Windows

```py
> cd temp
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:03 AM            stuff

> cd stuff/things/frank/joe/alex/john/
> cd ..
> rmdir john
> cd ..
> rmdir alex
> cd ..
> rmdir joe
> cd ..
> rmdir frank
> cd ..
> ls

    Directory: C:\Users\zed\temp\stuff

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:14 AM            things

> rmdir things
> cd ..
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/17/2011   9:14 AM            stuff

> rmdir stuff
> pwd

Path
----
C:\Users\zed\temp

> cd ..
> 
```

### 你应该学到的

现在我把这些命令混合起来了，所以你需要加倍注意，并确保你输入了正确的命令。每次你犯一个错误，都是因为你没有仔细看。如果你发现自己犯了不少错误，那么休息以下，或者退出练习一天。你总是需要明天再试一次的。

这个例子中，你学习了如何删除一个目录。很简单，你只需要在该目录的上一级目录，输入`rmdir &lt;dir&gt;`, 把`&lt;dir&gt;` 替换成你要删除的目录名。

### 更多练习

> *   创建 20 个以上的目标，再把他们都删除。
> *   创建一个深度为 10 的单一路径的目录，然后每次删除其中的一个。
> *   如果你尝试删除一个不为空的目录，你会得到一个错误。在后面的练习中我会告诉你如何删除这样的目录。

# 附录 A-练习 8：目录切换(pushd, popd)

# 附录 A-练习 8：目录切换(pushd, popd)

这节练习中，你将学习如何使用`pushd`实现保存你的当前位置，并去一个新的位置，然后您将学习如何使用`popd`恢复保存位置。

### 做到这些

### Linux/OSX

```py
$ cd temp
$ mkdir -p i/like/icecream
$ pushd i/like/icecream
~/temp/i/like/icecream ~/temp
$ popd
~/temp
$ pwd
~/temp
$ pushd i/like
~/temp/i/like ~/temp
$ pwd
~/temp/i/like
$ pushd icecream
~/temp/i/like/icecream ~/temp/i/like ~/temp
$ pwd
~/temp/i/like/icecream
$ popd
~/temp/i/like ~/temp
$ pwd
~/temp/i/like
$ popd
~/temp
$ pushd i/like/icecream
~/temp/i/like/icecream ~/temp
$ pushd
~/temp ~/temp/i/like/icecream
$ pwd
~/temp
$ pushd
~/temp/i/like/icecream ~/temp
$ pwd
~/temp/i/like/icecream
$ 
```

### Windows

```py
> cd temp
> mkdir -p i/like/icecream

    Directory: C:\Users\zed\temp\i\like

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/20/2011  11:05 AM            icecream

> pushd i/like/icecream
> popd
> pwd

Path
----
C:\Users\zed\temp

> pushd i/like
> pwd

Path
----
C:\Users\zed\temp\i\like

> pushd icecream
> pwd

Path
----
C:\Users\zed\temp\i\like\icecream

> popd
> pwd

Path
----
C:\Users\zed\temp\i\like

> popd
> 
```

### 你应该学到的

你使用这些命令进入了程序员的领土，这些命令是如何方便使用，我一定要教会你使用。这些命令让你暂时去到不同的目录，然后再回来，实现两个目录之间的轻松切换。

`pushd`命令把你当前的目录放到一个 list 中，然后切换到另一个目录。就好像说"保存我在哪里，然后去下一个地方"

`popd`命令把你之前存储的目录弹出来，然后带你回到那个目录。

最后， 在 Unix 上，如果你不带任何参数运行`pushd`，将会在当前目录以及你之前最后一次保存的目录之间进行切换。这是来回切换两个目录的方法，但它在 Powershell 中不起作用。

### 更多练习

> *   使用这两个命令在你计算机上的所有目录中来回切换。
> *   删除目录`i/like/icecream`再自己创建几个目录，在你新创建的目录间进行切换。
> *   给自己解释下`pushd` 和 `popd`命令的输出。注意下，它是如何像一个堆栈一样工作的。
> *   你已经知道这些, 但请记住`mkdir -p` 将会创建整个路径，即使其中的目录都不存在。这是我在这节练习中首先要做的事情。

# 附录 A-练习 9：生成一个空文件(Touch, New-Item)

# 附录 A-练习 9：生成一个空文件(Touch, New-Item)

这节练习中，你将学习使用`touch`(Windows 中是`new-item`)命令创建一个空文件。

### 做到这些

### Linux/OSX

```py
$ cd temp
$ touch iamcool.txt
$ ls
iamcool.txt
$ 
```

### Windows

```py
> cd temp
> New-Item iamcool.txt -type file
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        12/17/2011   9:03 AM            iamcool.txt

> 
```

### 你应该学到的

你已经学会了如何创建一个空文件。在 Unix 中使用`touch`命令,它也改变了文件的修改时间。我只用这个命令还创建空文件。在 Windows 上，没有这命令，所以你要学习如何使用`New-Item`命令，这个命令可以创建空文件也可以创建创建一个新目录。

### 更多练习

> *   Unix: 创建一个目录，进入它并在里面创建一个文件。然后回到他的上一级目录，执行 `rmdir`命令，你将会得到一个错误。尝试想一想为什么会有这个错。
> *   Windows: 做同样的事情，但你不会看到这个错误。你将会得到一个提示，询问你是否真的要删除该目录。

# 附录 A-练习 10：复制文件 (cp)

# 附录 A-练习 10：复制文件 (cp)

这节练习中你将使用`cp`命令从一个位置复制一个文件到另一个位置。

### 做到这些

### Linux/OSX

```py
$ cd temp
$ cp iamcool.txt neat.txt
$ ls
iamcool.txt neat.txt
$ cp neat.txt awesome.txt
$ ls
awesome.txt iamcool.txt neat.txt
$ cp awesome.txt thefourthfile.txt
$ ls
awesome.txt  iamcool.txt  neat.txt  thefourthfile.txt
$ mkdir something
$ cp awesome.txt something/
$ ls
awesome.txt iamcool.txt  neat.txt  something  thefourthfile.txt
$ ls something/
awesome.txt
$ cp -r something newplace
$ ls newplace/
awesome.txt
$ 
```

### Windows

```py
> cd temp
> cp iamcool.txt neat.txt
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt

> cp neat.txt awesome.txt
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        12/22/2011   4:49 PM          0 awesome.txt
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt

> cp awesome.txt thefourthfile.txt
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        12/22/2011   4:49 PM          0 awesome.txt
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt
-a---        12/22/2011   4:49 PM          0 thefourthfile.txt

> mkdir something

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/22/2011   4:52 PM            something

> cp awesome.txt something/
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/22/2011   4:52 PM            something
-a---        12/22/2011   4:49 PM          0 awesome.txt
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt
-a---        12/22/2011   4:49 PM          0 thefourthfile.txt

> ls something

    Directory: C:\Users\zed\temp\something

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        12/22/2011   4:49 PM          0 awesome.txt

> cp -recurse something newplace
> ls newplace

    Directory: C:\Users\zed\temp\newplace

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        12/22/2011   4:49 PM          0 awesome.txt

> 
```

### 你应该学到的

现在你会复制文件了。这是简单的只获取一个文件，并复制到一个新文件。在这个练习中，我也创建了一个新目录，并将文件复制到该目录中。

我要告诉你一个关于程序员和系统管理员的秘密了。他们很懒，我也很懒，我的朋友们也很懒。这就是为什么我们要使用电脑。我们喜欢让电脑为我们做无聊的事情。在目前的练习中，为了使你了解这些命令，你需要重复键入这些枯燥的命令，但通常都不是这样的。通常，如果你发现自己正在做一些无聊或重复的事情，有可能已经有程序员找到更容易做到的方法了。只是你不知道这件事。

关于程序员的另一个秘密是，他们并不像你想象的那样聪明。如果你过多的思考要输入的内容，那你肯呢过就搞错了。相反，想象一下对你来说一个命令的名字是什么。可能是一个名字或者一些类似你认为的缩写。如果你仍然无法搞清楚，那么问问周围的人或者上网找找答案。但愿这不是跟 ROBOCOPY 一样愚蠢的东西。

### 更多练习

> *   使用 `cp -r`命令，复制一个包含文件的目录。
> *   复制一个文件到你的 home 目录或桌面。
> *   在你的 GUI 中找到这些文件，并用文本编辑器打开它们。
> *   请注意，为什么有时候我会在一个目录的结尾用一个`/` (slash) ？这可以确保该文件确实是一个目录，如果没有这个目录，我就会得到一个错误。

# 附录 A-练习 11：移动文件 (mv)

# 附录 A-练习 11：移动文件 (mv)

这节练习中，你将学习使用`mv`命令把文件从一个位置移动另一个位置。

### 做到这些

### Linux/OSX

```py
$ cd temp
$ mv awesome.txt uncool.txt
$ ls
newplace    uncool.txt
$ mv newplace oldplace
$ ls
oldplace    uncool.txt
$ mv oldplace newplace
$ ls
newplace   uncool.txt
$ 
```

### Windows

```py
> cd temp
> mv awesome.txt uncool.txt
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/22/2011   4:52 PM            newplace
d----        12/22/2011   4:52 PM            something
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt
-a---        12/22/2011   4:49 PM          0 thefourthfile.txt
-a---        12/22/2011   4:49 PM          0 uncool.txt

> mv newplace oldplace
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/22/2011   4:52 PM            oldplace
d----        12/22/2011   4:52 PM            something
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt
-a---        12/22/2011   4:49 PM          0 thefourthfile.txt
-a---        12/22/2011   4:49 PM          0 uncool.txt

> mv oldplace newplace
> ls newplace

    Directory: C:\Users\zed\temp\newplace

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        12/22/2011   4:49 PM          0 awesome.txt

> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/22/2011   4:52 PM            newplace
d----        12/22/2011   4:52 PM            something
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt
-a---        12/22/2011   4:49 PM          0 thefourthfile.txt
-a---        12/22/2011   4:49 PM          0 uncool.txt

> 
```

### 你应该学到的

移动文件，或者重命名文件。这很简单： 给出就名字，然后新名字。

### 更多练习

> *   将`newplace`目录中的一个文件移动到另一个目录，在移动回来。

# 附录 A-练习 12：查看文件 (less, MORE)

# 附录 A-练习 12：查看文件 (less, MORE)

为了做这个练习，你要用你已经知道的命令做一些工作。你还需要一个文本编辑器，可以编写纯文本（.txt）文件。这里是你要做的：

> *   打开文本编辑器，并输入一些内容到一个新文件。
> *   保存文件到你的桌面，并将其命名为`test.txt`。
> *   在你的命令行中，使用你已知的命令复制这个文件到`temp`目录下。

当你完成这些准备工作，开始完成这个练习吧。

### 做到这些

### Linux/OSX

```py
$ less test.txt
[displays file here]
$ 
```

就是这样，输入`q`退出`less`命令。

### Windows

```py
> more test.txt
[displays file here]
> 
```

> **NOTE:**上面例子中的输出，我使用 `[displays file here]` 代替程序显示的内容。 我这样做的意思是说"显示你这个程序的输出太复杂了，所以只需要在这里插入你在你电脑上看到的内容，假装我展示给你看了。"你的屏幕实际上不会这样显示。

### 你应该学到的

这是查看文件内容的一种方法。它很有用，因为如果这个文件有很多行，它将按页展现文件的内容，这样每次都只有一屏内容是可见的。在更多练习部分，你会做更多关于这个的练习。

### 更多练习

> *   再次打开你的文件，然后复制粘贴文件的文本内容，使文件有 50-100 行。
> *   将文件复制到你的`temp`目录中。
> *   现在再做一次这个练习。在 Unix 中，你可以使用空格键以及字母键 `w` 来向下或向上查看。方向键也适用。在 Windows 上，只能通过空格键翻页。
> *   看看你创建的空文件。
> *   `cp` 命令将会覆盖已经存在的文件，所以复制文件的时候一定要当心。

# 附录 A-练习 13：输出文件 (cat)

# 附录 A-练习 13：输出文件 (cat)

你要为这节练习做更多的准备工作，你要习惯于在一个程序中创建文件，然后通过命令行访问这个文件。使用上节练习中用过的文本编辑器，新建一个叫做 `test2.txt`的文件，这一次直接将他保存在你的`temp`目录中.

### 做到这些

### Linux/OSX

```py
$ less test2.txt
[displays file here]
$ cat test2.txt
I am a fun guy.
Don't you know why?
Because I make poems,
that make babies cry.
$ cat test.txt
Hi there this is cool.
$ 
```

### Windows

```py
> more test2.txt
[displays file here]
> cat test2.txt
I am a fun guy.
Don't you know why?
Because I make poems,
that make babies cry.
> cat test.txt
Hi there this is cool.
> 
```

请记住，当我说 `[displays file here]`的时候，我只是缩写了命令的真实输出，所以我没有给你展示确切的一切。

### 你应该学到的

你喜欢我的诗吗？你已经知道第一个命令，我只是让你检查你的文件是否存在。然后你使用`cat`输出该文件到屏幕上。这个命令会将整个文件内容不分页不间断的输出到屏幕上。为了证明这一点，我需要你同样使用该命令输出 I `test.txt`，这个文件会输出一大堆文字。

### 更多练习

> *   创建更多的文本文件，并使用`cat`命令输出文件内容。
> *   Unix: 尝试命令`cat test.txt test2.txt` 看看它做了什么。
> *   Windows: 尝试命令 `cat test.txt,test2.txt` 看看它做了什么。

# 附录 A-练习 14：删除文件 (rm)

# 附录 A-练习 14：删除文件 (rm)

这节练习中，你将学会如何使用`rm`命令删除一个文件。

### 做到这些

### Linux

```py
$ cd temp
$ ls
uncool.txt  iamcool.txt  neat.txt  something  thefourthfile.txt
$ rm uncool.txt
$ ls
iamcool.txt  neat.txt  something  thefourthfile.txt
$ rm iamcool.txt neat.txt thefourthfile.txt
$ ls
something
$ cp -r something newplace
$
$ rm something/awesome.txt
$ rmdir something
$ rm -rf newplace
$ ls
$ 
```

### Windows

```py
> cd temp
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/22/2011   4:52 PM            newplace
d----        12/22/2011   4:52 PM            something
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt
-a---        12/22/2011   4:49 PM          0 thefourthfile.txt
-a---        12/22/2011   4:49 PM          0 uncool.txt

> rm uncool.txt
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/22/2011   4:52 PM            newplace
d----        12/22/2011   4:52 PM            something
-a---        12/22/2011   4:49 PM          0 iamcool.txt
-a---        12/22/2011   4:49 PM          0 neat.txt
-a---        12/22/2011   4:49 PM          0 thefourthfile.txt

> rm iamcool.txt
> rm neat.txt
> rm thefourthfile.txt
> ls

    Directory: C:\Users\zed\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/22/2011   4:52 PM            newplace
d----        12/22/2011   4:52 PM            something

> cp -r something newplace
> rm something/awesome.txt
> rmdir something
> rm -r newplace
> ls
> 
```

### 你应该学到的

这里我们清理了之前练习中的所有文件。还记得我让你尝试使用`rmdir`删除一个不为空的目录吗？那个操作失败了因为你无法删除包含文件在内的目录。要做到这一点，你需要删除文件，或者递归删除所有的内容。这是你要在本节练习结尾要做的事情。

### 更多练习

> *   清理从开始练习到现在所有`temp`目录下的文件。
> *   在你的笔记本上写下递归删除文件时一定要小心。

# 附录 A-练习 15:退出命令行 (exit)

# 附录 A-练习 15:退出命令行 (exit)

### 做到这些

### Linux/OSX

```py
$ exit 
```

### Windows

```py
> exit 
```

### 你应该学到的

最后一个练习是学会如何退出一个终端命令行。这个非常简单，但是我还是希望你能多做些练习。

### 更多练习

在你最后的练习题中，我会告诉你如何使用帮助系统，使用帮助系统可以查看和研究并学会使用更多的命令行命令。

Unix 中你需要自己研究的命令:

> *   xargs
> *   sudo
> *   chmod
> *   chown

Windows 中你需要自己研究的命令:

> *   forfiles
> *   runas
> *   attrib
> *   icacls

找出这些命令是干什么的，并练习使用它们，然后把他们加入到你的索引卡中。

# 附录 A-下一步

# 附录 A-下一步

### 命令行学习下一步

你已经完成了这本快速教程。此时，你应该能勉强算是一个 shell 用户了。 但是仍然还有一大部分的操作是你所不知道的，我想在最后给你一些需要研究的内容。

### Unix Bash 参考（Unix/Linux 环境）

在 Unix 环境下你所用的 shell 叫做`Bash`。它不是最大的 shell 程序，但是它无所不在，而且又很多的功能，所以，学习 Bash 是一个好的开始。下面是几个学习 Bash 可以参考的链接：

Bash 使用小技巧: `http://cli.learncodethehardway.org/bash_cheat_sheet.pdf`

参考手册: `http://www.gnu.org/software/bash/manual/bashref.html`

### PowerShell 参考（windows 环境）

在 Windows 环境下，通常只有`PowerShell`，下面是一系列对你有用的文档：

用户手册: `http://technet.microsoft.com/en-us/library/ee221100.aspx`

使用技巧: `http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=7097`

PowerShell 大师: `http://powershell.com/cs/blogs/ebook/default.aspx`