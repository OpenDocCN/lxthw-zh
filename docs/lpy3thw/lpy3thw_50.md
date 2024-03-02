# 练习 46\. 一个项目骨架

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.51.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.51.learn-py3.md)

这个练习你将学习如何创建一个好的项目“骨架”（skeleton）目录。这个骨架目录具备让项目跑起来的所有基本内容。它里边会包含你的项目文件布局、自动化测试代码、模块，以及安装脚本。当你建立一个新项目的时候，只要把这个目录复制过去，改改目录的名字，再编辑里边的文件就行了。

## macOS/Linux 设置

在开始这个练习之前，你需要用一个叫做 pip3.6（或者 pip）的工具为 Python 安装一些新的模块。python3.6 的安装中已经包含了 `pip3.6` 命令。你可以通过如下命令来验证一下：

```py
$ pip3.6 list
pip (9.0.1)
setuptools (28.8.0)
$
```

如果看到任何弃用警告，可以忽略它。您可能还会看到安装了其他工具，但是基本的应该是 pip 和 setuptools。一旦你验证了这一点，你就可以安装 virtualenv:

```py
$ sudo pip3.6 install virtualenv Password:
Collecting virtualenv
Downloading virtualenv–15.1.0–py2.py3–none–any.whl (1.8MB)  100%  |||||||||||||||||||||||||||||||||  1.8MB  1.1MB/s
Installing collected packages: virtualenv Successfully installed virtualenv–  15.1.0
$
```

这是用于 Linux 或者 macOS 系统的，如果你用的是 Linux/macOS， 你可以运行如下命令来确保你安装了正确的 virtualenv:

```py
$ whereis virtualenv
/Library/Frameworks/Python.framework/Versions/3.6/bin/virtualenv
```

您应该能在 macOS 上看到类似上面的内容，但是 Linux 上可能不一样。在 Linux 上，你可能有一个实际的 `virtualenv3.6` 命令，或者你最好从你的包管理系统（package management system）中为它安装一个包（package）。

一旦安装了 virtualenv，你就可以用它来创建一个“伪” Python 安装，从而更容易管理不同项目的包版本。首先，运行如下命令，我等会儿会解释它的作用：

```py
$ mkdir ~/.venvs
$ virtualenv –system–site –packages ~/.venvs/lpthw
$ .  ~/.venvs/lpthw/bin/activate
(lpthw) $
```

每一行发生的事情如下：

*   你在你的 `HOME ~/` 地址下创建了一个叫做 `.venvs` 的目录，用来存储你的虚拟环境。

*   你运行了 `virtualenv` 然后告诉它要包含 `system site packages` (— system-site-packages)，然后指导它在 `~/.venvs/lpthw` 中创建 `virtualenv`。

*   然后你在 bash 中用 `.` 运算符来获得 `lpthw` 虚拟环境，后面跟着 `~/.venvs/lpthw/bin/activate` 脚本。

*   最后，你的提示变成了包含 `(lpthw)`，这样你就知道了你正在使用虚拟环境。

现在你可以看到东西被安装在哪里：

```py
(lpthw) $ which python
/Users/zedshaw/.venvs/lpthw/bin/python
(lpthw) $ python
Python  3.6.0rc2  (v3.6.0rc2:800a67f7806d,  Dec  16  2016,  14:12:21)
[GCC 4.2.1  (Apple  Inc. build 5666)  (dot 3)] on darwin
Type  "help",  "copyright",  "credits"  or  "license"  for more information.
>>> quit()
(lpthw) $
```

你可以看到运行中的 python 被安装在 `/Users/zedshaw/.venvs/lpthw/bin/python` 目录，而不是原来的地址。这样还免去了要输入 `python3.6` 的麻烦，因为它把二者都安装了：

```py
$ which python3.6
/Users/zedshaw/.venvs/lpthw/bin/python3.6
(lpthw) $
```

你会发现 `virtualenv` 和 `pip` 命令也一样。这个设置的最后一步是安装 `nose`，一个我们要在练习中用到的测试框架。

```py
$ pip install nose
Collecting nose
Downloading nose—1.3.7—py3—none—any.whl (154kB)
100%  |  ¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦  |  163kB  3.2mb/s Installing collected packages: nose
Successfully installed nose —1.3.7
(lpthw) $
```

## Windows 10 设置

Windows 10 的安装会比 Linux 或者 macOS 简单一些，但是前提是你只安装了一个版本的 Python。如果你有两个版本：Python 3.6 和 Python 2.7，那你自己靠自己了，因为搞多重安装太复杂了。如果你一直跟着这本书学的话，你应该只有 Python 3.6，然后你可以这样做。

首先，切换到你的 home 目录，然后确保你正在运行正确版本的 Python：

```py
> cd ~
> python
Python  3.6.0  (v3.6.0:41 df79263a11 ,  Dec  23  2016,  08:06:12)  [MSC v.1900  64 bit (AMD64)] on Win32
Type  "help",  "copyright",  "credits"  or  "license"  for more informa
>>> quit()
```

然后运行 `pip` 确保你已经做了基本的安装：

```py
> pip list
pip (9.0.1)
setuptools (28.8.0)
```

你可以安全地忽略任何弃用警告，如果你安装了其他的包也没有关系。接着，安装 `virtualenv` 来为这本书接下来的内容设置一个虚拟环境：

```py
> pip   install virtualenv
Collecting virtualenv
Using cached virtualenv —15.1.0—py2.py3—none—any.whl Installing collected packages : virtualenv
Successfully installed virtualenv —  15.1.0
```

安装好 `virtualenv` 之后，你需要创建一个 `.venvs` 目录，并填入一个虚拟环境：

```py
> mkdir . venvs
> virtualenv —system—site —packages.venvs/lpthw
Using  base prefix
'c:\\users\\zedsh\\appdata\\local\\programs\\python\\python36
New python executable in
C:\Users\zedshaw\.venvs\lpthw\Scripts\python.exe
Installing setuptools, pip, wheel ... done.
```

这两行命令创建了一个 `.venvs` 文件夹来存储不同的虚拟环境，然后还创建了你的第一个虚拟环境 `lpthw`。一个虚拟环境（virtualenv）是一个用来运行软件的虚构的地方，这样你就有了针对每个项目包的不同版本。设置好 `virtualenv` 之后你需要激活它：

```py
>  .\.venvs\lpthw\Scripts\activate
```

这个命令会让 PowerShell 运行 activate 脚本，这个脚本会为你当前的 shell 配置 lpthw 虚拟环境。每次你想用你在这本书里的软件，你都要运行这个命令。你会看到 PowerShell 中的下一行命令提示符前面已经有了一个 `(lpthw)`，这表明了你正在使用的虚拟环境。最后，你只需要安装 nose 来运行随后的测试：

```py
(lpthw)  > pip install nose
Collecting nose
Downloading nose —1.3.7—py3—none—any.whl (154kB)
100%  |  ¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦¦  | i63kB i.2mb/s Installing collected packages: nose
Successfully installed nose—1.3.7
(lpthw)  >
```

你会看到，这样就安装了 nose，不过 pip 会把它安装在你的 `.venvs\lpthw` 虚拟环境中，而不是主系统的目录。这可以让你为每个项目安装相互冲突的 Python 包版本，而不会影响主系统的配置。

## 创建项目骨架目录

首先，用以下这些命令创建你的项目骨架结构：

```py
$ mkdir projects
$ cd projects/
$ mkdir skeleton
$ cd skeleton
$ mkdir bin, NAME, tests, docs
```

**ai 酱注：**这里原文是 `mkdir bin Name tests docs` 无法正常运行，作者本意是创建平行文件夹，所以用 `,` 隔开。

我用一个叫做 projects 的目录来存储所有我正在使用的变量。在这个目录下，我创建了 skeleton 目录，并把我项目的一些基础文件放了进去。这个 NAME 可以被重命名为任何你想给你项目的主模块取的名字。

接着，我们需要设置一些初始化文件，以下是 Linux/macOS 系统上的操作：

```py
$ touch NAME/__init__.py
$ touch tests/__init__.py
```

以下是 Windows PowerShell 上的操作：

```py
$ new-item —type file NAME/__init__.py
$ new-item —type file tests/__init__.py
```

这样就创建了一个空的 Python 模块目录，我们可以把我们的代码放进去。然后我们需要创建一个 `setup.py` 以便在之后需要的时候来安装我们的项目：

**ai 酱注：**该文件创建在当前 skeleton 目录下，可以参考前述创建文件的命令来创建。

setup.py

```py
1  try:
2  from setuptools import setup
3  except  ImportError:
4  from distutils.core import setup
5
6 config =  {
7  'description':  'My Project',
8  'author':  'My Name',
9  'url':  'URL to get it at.',
10  'download_url':  'Where to download it.',
11  'author_email':  'My email.',
12  'version':  '0.1',
13  'install_requires':  ['nose'],
14  'packages':  ['NAME'],
15  'scripts':  [],
16  'name':  'projectname'
17  }
18
19 setup(**config)
```

编辑这个文件，在其中填上你的联系信息，并且保证当你复制该文件的时候它能正常运行。

最后，你需要一个简单的骨架文件来测试，文件名为：`tests/NAME_tests.py` :

NAME_tests.py

```py
1  from nose.tools import  *
2  import NAME
3
4  def setup():
5  print("SETUP!")
6
7  def teardown():
8  print("TEAR DOWN!")
9
10  def test_basic():
11  print("I RAN!")
```

### 46.3.1 最终目录结构

当你完成以上所有设置，你的目录应该像下面这样：

```py
skeleton /
NAME/
__init__.py
bin/
docs/
setup.py
tests/
NAME_tests. py
__init__.py

```

从现在开始，你应该从这个目录中运行你的命令。如果你看不到，可以输入 `ls -R`，如果你没看到同样的结构，那应该是搞错了当前目录。比如，人们通常在 tests/ 下运行文件，这肯定行不通。要运行你的应用的测试，你需要处在 tests/ 目录的上一层，所以如果你这样：

```py
$ cd tests/  # WRONG! WRONG! WRONG!
$ nosetests
-----------------------
Ran  0 tests in  0.000 s OK
```

那就大错特错了，你得在 tests 的上一层目录。要是你犯了这个错误，你可以这样改正：

```py
$ cd ..  # get out of tests/
$ ls # CORRECT! you are now in the right spot
NAME    bin docs    setup.py
$ nosetests
.
-----------------------
Ran  1 test in  0.004s OK
```

记住这一点，因为人们经常犯这样的错误。

## 测试你的 Setup

当你安装好了所有东西之后，你应该可以运行这个：

```py
$ nosetests
.
-----------------------
Ran  1 test in  0.007s OK
```

我会在下个练习中给你解释 nosetests 是做什么的，但是现在，你如果没看到这个，那你可能哪个地方搞错了。确保你把 `**init**.py` 文件放在了你的 NAME 目录和 tests 目录下面，并且确保你把 `tests/NAME_tests.py` 放在了正确的位置。

## 使用这个骨架

现在你已经完成了一连串的动作。任何时候当你想要开始一个新项目，只需要这样做：

*   创建一个骨架目录的副本，以你的新项目名称命名。

*   用你的新项目名重命名 NAME 目录，或者其他你想用的名字，来调用你的根模块。

*   编辑你的 `setup.py` 文件，为你的新项目填入相应的信息。

*   重命名 `tests/NAME_tests.py` 文件，跟你的模块文件保持一致。

*   再次用 nosetests 确保所有文件都能正常运行。

*   开始编写代码。

## 课后测试

这个练习没有附加练习，但是你必须完成一个测试：

*   读一读如何使用你所安装的所有东西。

*   读一读 `setup.py` 文件及其内容。警告：它不是一个写得很好的软件，所以可能会很难用。

*   创建一个项目，并且开始把代码放入模块，然后让这个模块运行起来。

*   在 bin 目录中放一个可以运行的脚本。读一读你如何能让一个 Python 脚本在你的系统中正常运行。

*   在你的 `setup.py` 文件中加上你所创建的 bin 脚本，以使其得到安装。

*   用你的 `setup.py` 来安装你自己的模块，确保它能正常运行，然后使用 pip 来卸载它。

## 常见问题

**这些指导适用于 Windows 吗？** 适用的，不过还取决于你的 Windows 版本。有些版本可能会让你在安装的时候遇到一些麻烦。你可以通过搜索来解决，或者找一个对 Python+Windows 比较有经验的朋友来帮你解决。

**我应该在我的 `setup.py` 配置文件中放些什么呢？** 确保你阅读了该链接中的发布工具（distutils）文档：[`docs.python3.6.org/distutils/setupscript.html`](http://docs.python3.6.org/distutils/setupscript.html).

**我没办法引入 NAME 模块，总是收到报错信息 `ImportError`。** 确保你创建了 `NAME/**init**.py` 文件。如果你用的是 Windows，确保你没有不小心把它命名成了 `NAME/**init**.py.txt`，某些编辑器会有这样的默认设置。

**为什么我们需要一个 `bin/` 文件夹呢？** 这是一个用于存放在命令行运行的脚本的标准地方，它不是一个存放模块的地方。

**我的 `nosetests` 运行结果只显示了一个 test 被运行。这是正确的吗？** 是的，我的输出结果也是这样的。`