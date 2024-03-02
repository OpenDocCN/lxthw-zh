# 附录练习 14 移除文件 （rm）

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.15.spilt.60.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.15.spilt.60.learn-py3.md)

在这个练习中你将学习如何用 `rm` 命令移除（删除）一个文件。

### 55.15.1 跟我做

#### Linux

练习 14 会话

```py
1.  `$ cd temp`2.  `$ ls`3.  `uncool.txt iamcool.txt neat.txt something thefourthfile.txt`4.  `$ rm uncool.txt`5.  `$ ls`6.  `iamcool.txt neat.txt something thefourthfile.txt`7.  `$ rm iamcool.txt neat.txt thefourthfile.txt`8.  `$ ls something`9.  `$ cp -r something newplace`10.  `$`11.  `$ rm something/awesome.txt`12.  `$ rmdir something`13.  `$ rm -rf newplace`14.  `$ ls`15.  `$`
```

#### Windows

练习 14 Windows 会话

```py
1.  `> cd temp`2.  `> ls`5.  ```Directory: C:\Users\zed\temp```py8.  ````Mode  LastWriteTime  Length  Name```py`9.  ```----  -------------  ------  ----```py10.  ```d----  12/22/2011  4:52 PM      newplace```py11.  ```d----  12/22/2011  4:52 PM      something```py12.  ```-a---  12/22/2011  4:49 PM 0 iamcool.txt```py13.  ```-a---  12/22/2011  4:49 PM 0 neat.txt```py14.  ```-a---  12/22/2011  4:49 PM 0 thefourthfile.txt```py15.  ```-a---  12/22/2011  4:49 PM 0 uncool.txt```py18.  ````> rm uncool.txt```py`19.  ```> ls```py21.  ````Directory: C:\Users\zed\temp```py`24.  ````Mode  LastWriteTime  Length  Name```py`25.  ```----  -------------  ------  ----```py26.  ```d----  12/22/2011  4:52 PM      newplace```py27.  ```d----  12/22/2011  4:52 PM      something```py28.  ```-a---  12/22/2011  4:49 PM 0 iamcool.txt```py29.  ```-a---  12/22/2011  4:49 PM 0 neat.txt```py30.  ```-a---  12/22/2011  4:49 PM 0 thefourthfile.txt```py33.  ````> rm iamcool.txt```py`34.  ```> rm neat.txt```py35.  ```> rm thefourthfile.txt```py36.  ```> ls```py39.  ````Directory: C:\Users\zed\temp```py`42.  ````Mode  LastWriteTime  Length  Name```py`43.  ```----  -------------  ------  ----```py44.  ```d----  12/22/2011  4:52 PM      newplace```py45.  ```d----  12/22/2011  4:52 PM      something```py48.  ````> cp -r something newplace```py`49.  ```> rm something/awesome.txt```py50.  ```> rmdir something```py51.  ```> rm -r newplace```py52.  ```> ls```py55.  ````>```py`
```

 ``### 55.15.2 你学到的

这个练习我们学习了如何删除文件。还记得之前我让你们用 `rmdir` 命令移除包含内容的目录时失败了吗？是因为你不能用 `rmdir` 移除包含内容的目录。要移除这个目录，首先要删除它里面的文件，这也正是这个练习中所学到的。

### 55.15.3 附加练习

*   删除 temp 目录中目前为止所有的练习文件。
*   当你对文件进行递归删除的时候要千万小心。（**译者注**：递归删除就是你想删一个文件夹,而这个文件夹下还有其它的东西,它就会先把其它的东西删掉,再删这个文件夹）``