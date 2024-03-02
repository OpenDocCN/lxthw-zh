# 附录练习 12 浏览文件 （less, MORE）

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.13.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.13.spilt.60.learn-py3.md)

做这个练习需要用到目前为止已经学过的一些命令。你还需要一个能创建文本文档（.txt）的文本编辑器，以下是你要做的：

*   打开你的文本编辑器，在新文件中输入一些东西。在 macOS 下，你可以用 TextWrangler，在 Windows 系统下你可以用 Notepad++，在 Linux 下可以用 Gedit。其他任何文本编辑器也都可以。
*   把这个文件保存到桌面，然后命名为 test.txt。
*   在 Shell 中用你学到的命令把这个文件复制到当前的工作目录—— temp 目录下。

做完这些，再完成下面的练习。

### 55.13.1 跟我做

#### Linux/macOS

练习 12 会话

```py
$ less test.txt [displays file here]
$
```

就是这些，输入 `q` 即可退出 `less` 浏览模式。

#### Windows

练习 12 Windows 会话

```py
> more test.txt [displays file here]
>
```

| 警告！ |
| --- |
| 在前面的练习结果中，我用了 `[displays file here]` 来指代程序的输出结果，因为有些输出结果比较复杂。你要知道你的输出结果不是这个。 |

### 55.13.2 你学到的

这只是查看文件内容的一种方法。它很有用，因为当文件有很多行的时候，它可以翻页。在附加练习部分你会做更多的操作。

### 55.13.3 附加练习

*   再次打开你的文本文件，通过复制粘贴的方法把内容扩充到 50-100 行。
*   再把它复制到 temp 目录下。
*   现在再做一遍练习，这一遍可以翻页，Unix 系统可以用 空格键和 `w` 来上下翻页，Windows 系统直接用空格键即可。
*   再看看你创建的其他一些空文件。
*   `cp` 命令会覆盖一些已经存在的文件，所以要复制的时候要小心。