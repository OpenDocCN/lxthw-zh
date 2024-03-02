# 附录练习 6 列示目录 (ls)

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.7.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.7.spilt.60.learn-py3.md)

在这个练习中你将学习如何用 `ls` 命令列示一个目录中的内容。

### 55.7.1 跟我做

在你开始之前，确保你回到 temp 的上一层目录。如果你不知道你在哪儿，用 `pwd` 来查看，然后切换到要求的地方。

#### Linux/macOS

练习 6 会话

```py
$ cd temp
$ ls stuff
$ cd stuff
$ ls things
$ cd things
$ ls orange
$ cd orange
$ ls apple
$ cd apple
$ ls pear
$ cd pear
$ ls
$ cd grape
$ ls
$ cd ..
$ ls grape
$ cd ../../../
$ ls orange
$ cd ../../
$ ls stuff
22.  ``$``
```

#### Windows

练习 6 Windows 会话

```py
> cd temp
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      stuff
> cd stuff
> ls
Directory: C:\Users\zed\temp\stuff
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      things
> cd things
> ls
Directory: C:\Users\zed\temp\stuff\things
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      orange
> cd orange
> ls
Directory: C:\Users\zed\temp\stuff\things\orange
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      apple
> cd apple
> ls
Directory: C:\Users\zed\temp\stuff\things\orange\apple
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      pear
> cd pear
> ls
Directory: C:\Users\zed\temp\stuff\things\orange\apple\pear
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      grape
`> cd grape
> ls
> cd ..
> ls
`Directory: C:\Users\zed\temp\stuff\things\orange\apple\pear
`Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      grape
> cd ..
> ls
Directory: C:\Users\zed\temp\stuff\things\orange\apple
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      pear
> cd ../../..
> ls
Directory: C:\Users\zed\temp\stuff
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      things
> cd ..
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      stuff
>
```

### 55.7.2 你学到的

`ls` 命令列示出了你当前所在目录的内容。你能看到我使用 `cd` 命令在不同目录之间切换，然后列示出它们里面有些什么内容，然后让我决定接下来要去哪个目录。

`ls` 命令有很多选项，我们会在学习 `help` 命令时学习如何获取帮助。

### 55.7.3 附加练习

*   把每一个命令都输一遍，你必须通过输入来学习这些命令，只是读它们是不够的。
*   在 Unix 下，让你在 temp 目录下，试试 `ls -lR` 命令。
*   在 Windows 系统下，用 `dir -R` 做同样的操作。
*   用 `cd` 去到你电脑上的其他目录，然后用 `ls` 看看它们里面有什么。
*   把新的问题添加到你的本子上。我知道你可能会有一些，因为关于这个命令的内容我没有全讲到。
*   记住如果你迷路了，用 `ls` 和 `pwd` 命令查看你在哪儿，然后用 `cd` 命令去到你应该去的地方。