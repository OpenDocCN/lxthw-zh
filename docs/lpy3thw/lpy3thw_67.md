# 附录练习 7 移除目录 (rmdir)

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.8.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.8.spilt.60.learn-py3.md)

在这个练习中，你将学习如何移除一个空目录。

### 55.8.1 跟我做

#### Linux/macOS

练习 7 会话

```py
$ cd temp
$ ls stuff
$ cd stuff/things/orange/apple/pear/grape/
$ cd ..
$ rmdir grape
$ cd ..
$ rmdir pear
$ cd ..
$ ls apple
$ rmdir apple
$ cd ..
$ ls orange
$ rmdir orange
$ cd ..
$ ls things
$ rmdir things
$ cd ..
$ ls stuff
$ rmdir stuff
$ pwd
~/temp
$
```

| 警告！ |
| --- |
| 如果你在 MacOS 系统下尝试用 `rmdir` 命令， 但是系统拒绝移除这个目录，即使你百分百确定它是空的，事实上的确有个文件在里面，叫做 `.DS_Store` 。遇到这种情况，输入 `rm -rf <dir>` （将 `<dir>` 替换成你要移除的目录名）。 |

#### Windows

练习 7 Windows 会话

```py
> cd temp
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:03 AM      stuff
> cd stuff/things/orange/apple/pear/grape/
> cd ..
> rmdir grape
> cd ..
> rmdir pear
> cd ..
> rmdir apple
> cd ..
> rmdir orange
> cd ..
> ls
Directory: C:\Users\zed\temp\stuff
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:14 AM      things
> rmdir things
> cd ..
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/17/2011  9:14 AM      stuff
> rmdir stuff
> pwd
Path
----
C:\Users\zed\temp
> cd ..
>
```

### 55.8.2 你学到的

我现在开始把这些目录混在一起用了，所以你一定要专心，确保自己都输对了。如果你犯错了，只能说明你不专心。如果你发现自己犯了很多错，休息一下，或者干脆今天就不学了，明天再继续。

在这个例子中，你学会了如何移除一个目录，非常简单。你只需要去到它的上层目录，然后输入 `rmdir <dir>` ，用你要移除的目录名替换掉 `<dir>` 即可。

### 55.8.3 附加练习

*   创建 20 个目录，然后移除它们。
*   创建一个 10 层路径的目录，然后一次移除一个，就像我之前做的那样。
*   如果你试着移除一个有内容的目录，你会收到报错。我会在后面的练习中教你如何移除它们。``