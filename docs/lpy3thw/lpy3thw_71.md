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
6.  ```Directory: C:\Users\zed\temp```py9.  ````Mode  LastWriteTime  Length  Name```py`10.  ```----  -------------  ------  ----```py11.  ```d----  12/22/2011  4:52 PM      newplace```py12.  ```d----  12/22/2011  4:52 PM      something```py13.  ```-a---  12/22/2011  4:49 PM 0 iamcool.txt```py16.  ````-a---  12/22/2011  4:49 PM 0 neat.txt```py`17.  ```-a---  12/22/2011  4:49 PM 0 thefourthfile.txt```py18.  ```-a---  12/22/2011  4:49 PM 0 uncool.txt```py21.  ````> mv newplace oldplace```py`22.  ```> ls```py25.  ````Directory: C:\Users\zed\temp```py`28.  ````Mode  LastWriteTime  Length  Name```py`29.  ```----  -------------  ------  ----```py30.  ```d----  12/22/2011  4:52 PM      oldplace```py31.  ```d----  12/22/2011  4:52 PM      something```py32.  ```-a---  12/22/2011  4:49 PM 0 iamcool.txt```py33.  ```-a---  12/22/2011  4:49 PM 0 neat.txt```py34.  ```-a---  12/22/2011  4:49 PM 0 thefourthfile.txt```py35.  ```-a---  12/22/2011  4:49 PM 0 uncool.txt```py38.  ````> mv oldplace newplace```py`39.  ```> ls newplace```py42.  ````Directory: C:\Users\zed\temp\newplace```py`45.  ````Mode  LastWriteTime  Length  Name```py`46.  ```----  -------------  ------  ----```py47.  ```-a---  12/22/2011  4:49 PM 0 awesome.txt```py50.  ````> ls```py` 53.  ````Directory: C:\Users\zed\temp```py`56.  ````Mode  LastWriteTime  Length  Name```py`57.  ```----  -------------  ------  ----```py58.  ```d----  12/22/2011  4:52 PM      newplace```py59.  ```d----  12/22/2011  4:52 PM      something```py60.  ```-a---  12/22/2011  4:49 PM 0 iamcool.txt```py61.  ```-a---  12/22/2011  4:49 PM 0 neat.txt```py62.  ```-a---  12/22/2011  4:49 PM 0 thefourthfile.txt```py63.  ```-a---  12/22/2011  4:49 PM 0 uncool.txt```py67.  ````>```py`
```

 ``### 55.12.2 你学到的

移动文件，或者重命名，很简单：给出原来的名字和新的名字即可。

### 55.12.3 附加练习

*   将 newplace 目录下的一个文件移动到另一个目录下，然后再移动回来。``