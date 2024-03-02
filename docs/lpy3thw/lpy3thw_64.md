# 附录练习 4 创建目录（mkdir）

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.5.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.5.spilt.60.learn-py3.md)

在这个练习中，你将学习如何用 `mkdir` 命令创建新目录。

### 55.5.1 跟我做

记住！在进行这个练习之前，你需要先用 `pwd` 和 `cd ~` 回到 home！在做附录之后的每个练习前，都要先回到 home！

#### Linux/macOS

练习 4 会话

```py
1.  `$ pwd`2.  `$ cd ~`4.  ``$ mkdir temp``5.  ``$ mkdir temp/stuff``6.  ``$ mkdir temp/stuff/things``7.  ``$ mkdir -p temp/stuff/things/orange/apple/pear/grape``8.  ``$``
```

 `#### Windows

练习 4 Windows 会话

```py
1.  `> pwd`2.  `> cd ~`3.  `> mkdir temp`6.  ```Directory: C:\Users\zed```py9.  ````Mode  LastWriteTime  Length  Name```py`10.  ```----  -------------  ------  ----```py11.  ```d----  12/17/2011  9:02 AM      temp```py14.  ````> mkdir temp/stuff```py`17.  ````Directory: C:\Users\zed\temp```py`20.  ````Mode  LastWriteTime  Length  Name```py`21.  ```----  -------------  ------  ----```py22.  ```d----  12/17/2011  9:02 AM      stuff```py25.  ````> mkdir temp/stuff/things```py`28.  ````Directory: C:\Users\zed\temp\stuff```py`30.  ````Mode  LastWriteTime  Length  Name```py`31.  ```----  -------------  ------  ----```py32.  ```d----  12/17/2011  9:03 AM      things```py35.  ````> mkdir temp/stuff/things/orange/apple/pear/grape```py`39.  ````Directory: C:\Users\zed\temp\stuff\things\orange\apple\pear```py`42.  ````Mode  LastWriteTime  Length  Name```py`43.  ```----  -------------  ------  ----```py44.  ```d----  12/17/2011  9:03 AM      grape```py47.  ````>```py`
```

 ```pypwd` 和 `cd ~` 命令我只列这一次，但是记住，做每个练习之前你都要做这个操作。

### 55.5.2 你学到的

现在我们开始输入多行命令了，这些是你使用 `mkdir` 的多种不同方式。`mkdir` 命令是用来做什么的？他是用来创建目录的。如果你问出了这个问题，那么你需要回过头去复习一下命令表了，再好好记记你做的卡片吧。

创建新目录是什么意思？就是新建文件夹。以上练习中你做的事情就是在目录中创建多层目录。这就叫做“路径”（path），它是一种描述“temp 文件夹下的 stuff 文件夹下的 things 文件夹”的方式。它是你想在计算机的文件夹树中放入某些东西时的路径指向，它构成了你计算机的硬盘。

| 警告！ |
| --- |
| 在这个附录中，我将用 `/` 来表示路径，因为它适用于所有的电脑。然而，Windows 用户需要知道，你们也可以用 `\` 。 |

### 55.5.3 附加练习

*   “路径”的概念可能一开始会让你感到困惑。别担心，我们之后会多次用到这个概念，你会慢慢明白的。
*   在 temp 目录中再创建 20 个不同层级的目录。在图形界面的文件查看器中查看这些文件夹。
*   创建一个名称用 `“ ”` 括起来的目录：`mkdir "I Have Fun"`
*   如果临时文件夹已经存在了你的电脑就会报错。用 `cd` 切换到一个你能控制的工作目录下，然后再试。Windows 桌面是一个很好的选择。```