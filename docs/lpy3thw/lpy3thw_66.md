# 附录练习 6 列示目录 (ls)

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.7.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.7.spilt.60.learn-py3.md)

在这个练习中你将学习如何用 `ls` 命令列示一个目录中的内容。

### 55.7.1 跟我做

在你开始之前，确保你回到 temp 的上一层目录。如果你不知道你在哪儿，用 `pwd` 来查看，然后切换到要求的地方。

#### Linux/macOS

练习 6 会话

```py
1.  `$ cd temp`2.  `$ ls stuff`3.  `$ cd stuff`4.  `$ ls things`5.  `$ cd things`6.  `$ ls orange`7.  `$ cd orange`8.  `$ ls apple`9.  `$ cd apple`10.  `$ ls pear`11.  `$ cd pear`12.  `$ ls`13.  `$ cd grape`14.  `$ ls`15.  `$ cd ..`16.  `$ ls grape`17.  `$ cd ../../../`18.  `$ ls orange`19.  `$ cd ../../`20.  `$ ls stuff`22.  ``$``
```

 `#### Windows

练习 6 Windows 会话

```py
1.  `> cd temp`2.  `> ls`5.  ```Directory: C:\Users\zed\temp```py8.  ````Mode  LastWriteTime  Length  Name```py`9.  ```----  -------------  ------  ----```py10.  ```d----  12/17/2011  9:03 AM      stuff```py13.  ````> cd stuff```py`14.  ```> ls```py17.  ````Directory: C:\Users\zed\temp\stuff```py`20.  ````Mode  LastWriteTime  Length  Name```py`21.  ```----  -------------  ------  ----```py22.  ```d----  12/17/2011  9:03 AM      things```py25.  ````> cd things```py`26.  ```> ls```py29.  ````Directory: C:\Users\zed\temp\stuff\things```py`32.  ````Mode  LastWriteTime  Length  Name```py`33.  ```----  -------------  ------  ----```py34.  ```d----  12/17/2011  9:03 AM      orange```py37.  ````> cd orange```py`38.  ```> ls```py41.  ````Directory: C:\Users\zed\temp\stuff\things\orange```py`44.  ````Mode  LastWriteTime  Length  Name```py`45.  ```----  -------------  ------  ----```py46.  ```d----  12/17/2011  9:03 AM      apple```py49.  ````> cd apple```py`50.  ```> ls```py53.  ````Directory: C:\Users\zed\temp\stuff\things\orange\apple```py`56.  ````Mode  LastWriteTime  Length  Name```py`57.  ```----  -------------  ------  ----```py58.  ```d----  12/17/2011  9:03 AM      pear```py61.  ````> cd pear```py`62.  ```> ls```py65.  ````Directory: C:\Users\zed\temp\stuff\things\orange\apple\pear```py`68.  ````Mode  LastWriteTime  Length  Name```py`69.  ```----  -------------  ------  ----```py70.  ```d----  12/17/2011  9:03 AM      grape```py73.  ````> cd grape```py`74.  ```> ls```py75.  ```> cd ..```py76.  ```> ls```py79.  ````Directory: C:\Users\zed\temp\stuff\things\orange\apple\pear```py`82.  ````Mode  LastWriteTime  Length  Name```py`83.  ```----  -------------  ------  ----```py84.  ```d----  12/17/2011  9:03 AM      grape```py87.  ````> cd ..```py`89.  ````> ls```py`92.  ````Directory: C:\Users\zed\temp\stuff\things\orange\apple```py`95.  ````Mode  LastWriteTime  Length  Name```py`96.  ```----  -------------  ------  ----```py97.  ```d----  12/17/2011  9:03 AM      pear```py100.  ````> cd ../../..```py`101.  ```> ls```py104.  ````Directory: C:\Users\zed\temp\stuff```py`107.  ````Mode  LastWriteTime  Length  Name```py`108.  ```----  -------------  ------  ----```py109.  ```d----  12/17/2011  9:03 AM      things```py112.  ````> cd ..```py`113.  ```> ls```py116.  ````Directory: C:\Users\zed\temp```py`119.  ````Mode  LastWriteTime  Length  Name```py`120.  ```----  -------------  ------  ----```py121.  ```d----  12/17/2011  9:03 AM      stuff```py124.  ````>```py`
```

 ``### 55.7.2 你学到的

`ls` 命令列示出了你当前所在目录的内容。你能看到我使用 `cd` 命令在不同目录之间切换，然后列示出它们里面有些什么内容，然后让我决定接下来要去哪个目录。

`ls` 命令有很多选项，我们会在学习 `help` 命令时学习如何获取帮助。

### 55.7.3 附加练习

*   把每一个命令都输一遍，你必须通过输入来学习这些命令，只是读它们是不够的。
*   在 Unix 下，让你在 temp 目录下，试试 `ls -lR` 命令。
*   在 Windows 系统下，用 `dir -R` 做同样的操作。
*   用 `cd` 去到你电脑上的其他目录，然后用 `ls` 看看它们里面有什么。
*   把新的问题添加到你的本子上。我知道你可能会有一些，因为关于这个命令的内容我没有全讲到。
*   记住如果你迷路了，用 `ls` 和 `pwd` 命令查看你在哪儿，然后用 `cd` 命令去到你应该去的地方。```