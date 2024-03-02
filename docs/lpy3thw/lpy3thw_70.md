# 附录练习 10 复制文件 (cp)

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.11.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.11.spilt.60.learn-py3.md)

在这个练习中，你将学习如何用 `cp` 命令把一个文件从一个地址复制到另一个地址。

### 55.11.1 跟我做

#### Linux/macOS

练习 10 会话

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
awesome.txt iamcool.txt neat.txt thefourthfile.txt
$ mkdir something
$ cp awesome.txt something/
$ ls
awesome.txt iamcool.txt neat.txt something thefourthfile.txt
$ ls something/ awesome.txt
$ cp -r something newplace
$ ls newplace/ awesome.txt
$
```

#### Windows

练习 10 Windows 会话

```py
> cd temp
> cp iamcool.txt neat.txt
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
-a---  12/22/2011  4:49 PM 0 iamcool.txt
-a---  12/22/2011  4:49 PM 0 neat.txt
> cp neat.txt awesome.txt
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
-a---  12/22/2011  4:49 PM 0 awesome.txt
-a---  12/22/2011  4:49 PM 0 iamcool.txt
-a---  12/22/2011  4:49 PM 0 neat.txt
> cp awesome.txt thefourthfile.txt
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
-a---  12/22/2011  4:49 PM 0 awesome.txt
-a---  12/22/2011  4:49 PM 0 iamcool.txt
-a---  12/22/2011  4:49 PM 0 neat.txt
-a---  12/22/2011  4:49 PM 0 thefourthfile.txt
> mkdir something
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/22/2011  4:52 PM      something
> cp awesome.txt something/
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/22/2011  4:52 PM      something
-a---  12/22/2011  4:49 PM 0 awesome.txt
-a---  12/22/2011  4:49 PM 0 iamcool.txt
-a---  12/22/2011  4:49 PM 0 neat.txt
-a---  12/22/2011  4:49 PM 0 thefourthfile.txt
> ls something
Directory: C:\Users\zed\temp\something
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
-a---  12/22/2011  4:49 PM 0 awesome.txt
> cp -recurse something newplace
> ls newplace
Directory: C:\Users\zed\temp\newplace
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
-a---  12/22/2011  4:49 PM 0 awesome.txt
>
```

### 55.11.2 你学到的

现在你会复制文件了，它很简单。在这个练习中，我还创建了一个新目录，并且把一个文件复制到了那个新目录中。

我要告诉你一个关于程序员和系统管理员的秘密。他们很懒，我也很懒，我的朋友同样很懒。这也正是为什么我们要用计算机。我们热衷于让计算机为我们做无聊的事情。这个练习到目前为止你已经输入了很多重复的命令来学习它们，但是实际情况不是这样的，通常如果你发现自己在做一些无聊和重复的事情，就已经有一个程序员在想办法如何让这件事情变得简单，你只是不知道而已。

关于程序员的另一件事情就是，他们可能没你想的那么聪明。如果你觉得他们输入的东西有多么高深莫测，那你就错了。在你做练习的时候，你可以先试着先想想这些命令的名字和含义，然后再输入。一般你会想到一个名字或者一些缩写。如果你还是想象不出来，就回过头复习一下或者在网上搜一搜。

### 5.11.3 附加练习

*   用 `cp -r` 命令复制更多包含文件的目录。
*   把一个文件复制到你的 home 目录或者桌面。
*   在图形用户界面找到这些文件，然后用文本编辑器打开它们。
*   注意我有时候会放一个 `/` 在目录结尾，这样是为了确保这是一个目录，如果不是的话，我会收到报错。