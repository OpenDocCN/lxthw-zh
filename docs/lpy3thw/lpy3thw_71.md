# 附录练习 11 移动文件 （mv）

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.12.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.12.spilt.60.learn-py3.md)

在这个练习中，你将会学习如何使用 `mv` 命令把一个文件从一个地方移动到另一个地方。

### 55.12.1 跟我做

#### Linux/macOS

练习 11 会话

```py
$ cd temp
$ mv awesome.txt uncool.txt
$ ls
newplace uncool.txt
$ mv newplace oldplace
$ ls
oldplace uncool.txt
$ mv oldplace newplace
$ ls
newplace uncool.txt
$
```

#### Windows

练习 11 Windows 会话

```py
> cd temp
> mv awesome.txt uncool.txt
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/22/2011  4:52 PM      newplace
d----  12/22/2011  4:52 PM      something
-a---  12/22/2011  4:49 PM 0 iamcool.txt
-a---  12/22/2011  4:49 PM 0 neat.txt
-a---  12/22/2011  4:49 PM 0 thefourthfile.txt
-a---  12/22/2011  4:49 PM 0 uncool.txt
> mv newplace oldplace
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/22/2011  4:52 PM      oldplace
d----  12/22/2011  4:52 PM      something
-a---  12/22/2011  4:49 PM 0 iamcool.txt
-a---  12/22/2011  4:49 PM 0 neat.txt
-a---  12/22/2011  4:49 PM 0 thefourthfile.txt
-a---  12/22/2011  4:49 PM 0 uncool.txt
> mv oldplace newplace
> ls newplace
Directory: C:\Users\zed\temp\newplace
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
-a---  12/22/2011  4:49 PM 0 awesome.txt
> ls
Directory: C:\Users\zed\temp
`Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/22/2011  4:52 PM      newplace
d----  12/22/2011  4:52 PM      something
-a---  12/22/2011  4:49 PM 0 iamcool.txt
-a---  12/22/2011  4:49 PM 0 neat.txt
-a---  12/22/2011  4:49 PM 0 thefourthfile.txt
-a---  12/22/2011  4:49 PM 0 uncool.txt
>
```

### 55.12.2 你学到的

移动文件，或者重命名，很简单：给出原来的名字和新的名字即可。

### 55.12.3 附加练习

*   将 newplace 目录下的一个文件移动到另一个目录下，然后再移动回来。``