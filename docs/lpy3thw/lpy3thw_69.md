# 附录练习 9 创建空文件 (Touch, New-Item)

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.10.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.10.spilt.60.learn-py3.md)

在这个练习中你将学习如何使用 `touch` （MacOS）或者 `new-item` （Windows） 命令来创建空文件。

### 55.10.1 跟我做

#### Linux/macOS

练习 9 会话

```py
$ cd temp
$ touch iamcool.txt
$ ls iamcool.txt
$
```

#### Windows

练习 9 Windows 会话

```py
> cd temp
>  New-Item iamcool.txt -type file
> ls
6.  ```Directory: C:\Users\zed\temp
Mode  LastWriteTime  Length  Name
----  -------------  ------  -----
a---  12/17/2011  9:03 AM      iamcool.txt
>
```

### 55.10.2 你学到的

你学习了如何创建空文件。在 Unix 系统下用 `touch` ，在 Windows 系统下用 `New-Item` 。

### 55.10.3 附加练习

*   Unix：创建一个目录，切换到该目录下，然后在它里面创建一个文件，然后再切换到该目录的上一次，用 `rmdir` 命令移除该目录。你会收到报错，试着理解一下为什么。
*   Windows：做同样的事情，但是你不会收到报错，你会收到一个提示符问你是否真的要移除这个目录。``