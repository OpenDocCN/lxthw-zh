# 附录练习 5 切换目录 (cd)

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.6.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.6.spilt.60.learn-py3.md)

在这个练习中，你将学习如何使用 `cd` 命令从一个目录切换到另一个目录。

### 55.6.1 跟我做

在这部分练习中我会再给你一次指导说明：

*   不用输入 `$` （Unix 系统）或者 `>` （Windows 系统）。
*   你输入 `$` 或者 `>` 后面的内容，然后回车。比如如果我写的是 `$ cd`，你就只用输入 `cd` 然后回车就行。
*   回车之后你会在 `$` 或者 `>` 之后看到你的输出结果。
*   每次练习之前要先用 `pwd` 和 `cd ~` 回到 home，回到你最开始的地方。

#### Linux/macOS

练习 5 会话

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
$ cd orange/
$ pwd
~/temp/stuff/things/orange
$ cd apple/
$ pwd
~/temp/stuff/things/orange/apple
$ cd pear/
$ pwd
~/temp/stuff/things/orange/apple/pear
$ cd grape/
$ pwd
~/temp/stuff/things/orange/apple/pear/grape
$ cd ..
$ cd ..
$ pwd
~/temp/stuff/things/orange/apple
$ cd ..
$ cd ..
$ pwd
~/temp/stuff/things
$ cd ../../..
$ pwd
~/
$ cd temp/stuff/things/orange/apple/pear/grape
$ pwd
~/temp/stuff/things/orange/apple/pear/grape
$ cd ../../../../../../../
$ pwd
~/
$
```

#### Windows

练习 5 Windows 会话

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
> cd orange
> pwd
Path
----
C:\Users\zed\temp\stuff\things\orange
> cd apple
> pwd
Path
----
C:\Users\zed\temp\stuff\things\orange\apple
> cd pear
> pwd
Path
----
C:\Users\zed\temp\stuff\things\orange\apple\pear
> cd grape
> pwd
Path
----
C:\Users\zed\temp\stuff\things\orange\apple\pear\grape
> cd ..
> cd ..
> cd ..
> pwd
Path
----
C:\Users\zed\temp\stuff\things\orange
> cd ../..
> pwd
Path
----
C:\Users\zed\temp\stuff
> cd ..
> cd ..
> cd temp/stuff/things/orange/apple/pear/grape
> cd ../../../../../../../
> pwd
Path
----
C:\Users\zed
>
```

 ``### 55.6.2 你学到的

你已经在上一个练习中创建了以上这些目录，你刚才只是用 `cd` 命令在这些目录之间来回移动，同时在练习中我还用了 `pwd` 命令来看自己当前所处的位置，所以别把 `pwd` 输出的内容当作命令输入进去。例如，在第三行，你看到 `~/temp`，但那只是 `pwd` 命令的输出结果，不要把它作为你要输入的内容。

你还应该看到我如何使用 `..` 命令来沿着路径向上。

### 55.6.3 附加练习

在一个拥有图形用户界面（graphical user interface，GUI） 的电脑上学习命令行界面（command line interface，CLI） 的一个非常重要的事情就是要明白它们是如何一起工作的。我最早开始使用计算机的时候还没有 GUI，我们在 DOS 界面上进行所有的操作。后来，当计算机变成强大的图形界面时，我很容易就能把一些 CLI 的目录和 GUI 上面的目录和 GUI 的窗口和文件夹对应上。

然而如今大多数人对 CLI、路径和目录毫无概念。事实上，也很难教会他们。唯一可能的办法就是持续地去用 CLI，直到有一天你用起 CLI 来会跟 GUI 一样自然流畅。

这就需要你花时间去寻找 GUI 下文件查看器里的目录，然后在 CLI 下切换到这些目录。以下是你接下来要做的：

*   用一个命令切换到 `apple` 目录下。
*   用一个命令切换回 `temp` 目录，但不是续着上一步来做。
*   试试如何用一个命令切换到你的“home 目录”。
*   切换到你的 Document 目录下，然后用 GUI 下的文件查看器找到它。（MacOS 下是 Finder，Windows 下是文件资源管理器，即“我的电脑”或“计算机”）
*   切换到你的 Downloads 目录，然后用你的文件浏览器找到它。
*   用你的文件浏览器找到其他目录，然后在 CLI 下切换到该目录。
*   还记得你给目录名加过引号吗？你也可以在命令中加入引号，比如，如果你有一个目录是 `I Have Fun`，然后你可以输入：`cd "I Have Fun"` 。``