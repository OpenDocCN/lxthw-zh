# 附录练习 8 来回移动 （pushd, popd）

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.9.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.9.spilt.60.learn-py3.md)

在这个练习中，你将学习如何用 `pushd` 命令保存你当前的位置然后去到一个新的位置，以及如何用 `popd` 命令返回之前保存的位置。

### 55.9.1 跟我做

#### Linux/macOS

练习 8 会话

```py
$ cd temp
$ mkdir i/like/icecream
$ pushd i/like/icecream
~/temp/i/like/icecream ~/temp
$ popd
~/temp
$ pwd
~/temp
$ pushd i/like
11.  ``~/temp/i/like ~/temp``12.  ``$ pwd``13.  ``~/temp/i/like``14.  ``$ pushd icecream``15.  ``~/temp/i/like/icecream ~/temp/i/like ~/temp``16.  ``$ pwd``17.  ``~/temp/i/like/icecream``18.  ``$ popd``19.  ``~/temp/i/like ~/temp``20.  ``$ pwd``21.  ``~/temp/i/like``22.  ``$ popd``23.  ``~/temp``24.  ``$ pushd i/like/icecream``25.  ``~/temp/i/like/icecream ~/temp``26.  ``$ pushd``27.  ``~/temp ~/temp/i/like/icecream``28.  ``$ pwd``29.  ``~/temp``30.  ``$ pushd``31.  ``~/temp/i/like/icecream ~/temp``32.  ``$ pwd``33.  ``~/temp/i/like/icecream``34.  ``$``
```

#### Windows

练习 8 Windows 会话

```py
> cd temp
> mkdir i/like/icecream
Directory: C:\Users\zed\temp\i\like
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/20/2011  11:05 AM     icecream
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

| 警告！ |
| --- |
| 在 Windows 系统下，你一般不用像 Linux 系统那样用 `-p` ，但是我想这应该是最近的更新，如果你用老的 Windows 系统的 Powershell，应该还是需要 `-p` 的，所以每个人的情况可能不太一样，你可以试试看。 |

### 55.9.2 你学到的

你正在通过这些命令进入程序员的世界，这些命令很常用，所以我必须要教给你们。它们能让你暂时地去到别的目录，然后再回来，并在两者之间随意切换。

`pushd` 命令会把你当前的目录“push”到一个列表里，然后它会切换到另外一个目录，就好像在说：“保存我现在的位置，然后去到那儿”。

`popd` 命令则是把你从你之前去到的目录那里拉回来。

最后，在 Unix 下使用 `pushd` 的话，如果你后面不加任何东西，它会在你的当前目录和你之前保存的目录之间来回切换。但是在 Powershell 下这个就不适用了。

### 55.9.3 附加练习

*   用这些命令在你电脑的目录之间来回移动。
*   移除 i/like/icecream 目录，然后自己创建一些，并在它们中间来回切换。
*   跟自己解释 `pushd` 和 `popd` 的输入结果，注意它和堆栈的概念很类似。
*   虽然你已经知道了，但是要记住 `mkdir -p` （在 Linux/MacOS 下）会创建一个完整的路径，即使所有的目录都不存在。这也就是我在本练习开头所做的。
*   记住 Window 也会创建一个完整的路径，并且不需要 `-p` 。