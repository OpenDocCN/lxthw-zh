# 附录练习 14 移除文件 （rm）

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.15.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.15.spilt.60.learn-py3.md)

在这个练习中你将学习如何用 `rm` 命令移除（删除）一个文件。

### 55.15.1 跟我做

#### Linux

练习 14 会话

```py
$ cd temp
$ ls
uncool.txt iamcool.txt neat.txt something thefourthfile.txt
$ rm uncool.txt
$ ls
iamcool.txt neat.txt something thefourthfile.txt
$ rm iamcool.txt neat.txt thefourthfile.txt
$ ls something
$ cp -r something newplace
$
$ rm something/awesome.txt
$ rmdir something
$ rm -rf newplace
$ ls
$
```

#### Windows

练习 14 Windows 会话

```py
> cd temp
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
> rm uncool.txt
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/22/2011  4:52 PM      newplace
d----  12/22/2011  4:52 PM      something
-a---  12/22/2011  4:49 PM 0 iamcool.txt
-a---  12/22/2011  4:49 PM 0 neat.txt
-a---  12/22/2011  4:49 PM 0 thefourthfile.txt
> rm iamcool.txt
> rm neat.txt
> rm thefourthfile.txt
> ls
Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  ----
d----  12/22/2011  4:52 PM      newplace
d----  12/22/2011  4:52 PM      something
> cp -r something newplace
> rm something/awesome.txt
> rmdir something
> rm -r newplace
> ls
>
```

### 55.15.2 你学到的

这个练习我们学习了如何删除文件。还记得之前我让你们用 `rmdir` 命令移除包含内容的目录时失败了吗？是因为你不能用 `rmdir` 移除包含内容的目录。要移除这个目录，首先要删除它里面的文件，这也正是这个练习中所学到的。

### 55.15.3 附加练习

*   删除 temp 目录中目前为止所有的练习文件。
*   当你对文件进行递归删除的时候要千万小心。（**译者注**：递归删除就是你想删一个文件夹,而这个文件夹下还有其它的东西,它就会先把其它的东西删掉,再删这个文件夹）``