# 附录练习 13 Stream 文件 （cat）

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.14.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.14.spilt.60.learn-py3.md)

在做这个练习之前你需要再多做一些准备工作，以便在练习中使用。用编辑器创建另一个名为 `test2.txt` 的文件，但是这次直接把它保存在 temp 目录下。

### 55.14.1 跟我做

#### Linux/macOS

练习 13 会话

```py
$ less test2.txt [displays file here]
$ cat test2.txt I am a fun guy.
Don't you know why? Because I make poems, that make babies cry.
$ cat test.txt
Hi there this is cool.
$
```

#### Windows

练习 13 Windows 会话

```py
> more test2.txt [displays file here]
3.  ``> cat test2.txt I am a fun guy.``4.  ``Don't you know why? Because I make poems, that make babies cry.``5.  ``> cat test.txt``6.  ``Hi there this is cool.``7.  ``>``
```

### 55.14.2 你学到的

你已经学习了第一个命令，这个命令只是为了让你检查一下那个文件确实在。然后你把这个文件 `cat` 到屏幕，`cat` 命令是把整个文件内容全部呈现到屏幕上，没有翻页或者停止。

### 55.14.3 附加练习

*   再创建几个文件并使用 `cat` 命令。
*   Unix：试试 `cat test.txt test2.txt` ，看看会发生什么。
*   Windows: 试试 `cat test.txt,test2.txt`，看看会发生什么。`