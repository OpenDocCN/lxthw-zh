# 练习 46.项目骨架

# 练习 46.项目骨架

这里你将学会如何建立一个项目“骨架”目录。这个骨架目录具备让项目跑起来的所有基本内容。它里边会包含你的项目文件布局、自动化测试代码，模组，以及安装脚本。当你建立一个新项目的时候，只要把这个目录复制过去，改改目录的名字，再编辑里边的文件就行了。

## 安装 Python 软件包的

你需要使用 pip 预先安装一些软件包，不过问题就来了。我的本意是让这本书越清晰越干净越好，不过安装软件的方法是在是太多了，如果我要一步一步写下来，那 10 页都写不完，而且告诉你吧，我本来就是个懒人。

所以我不会提供详细的安装步骤了，我只会告诉你需要安装哪些东西，然后让你自己搞定。即使我给了你所需软件详尽的安装说明，你还是不得不与之奋斗。计算机更新换代非常频繁，你在安装过程中遇到问题的时候，可以在网上搜索解决方案。

你需要安装下面的软件包：

> 1.  pip – [`pypi.python.org/pypi/pip`](http://pypi.python.org/pypi/pip)
> 2.  distribute – [`pypi.python.org/pypi/distribute`](http://pypi.python.org/pypi/distribute)
> 3.  nose – [`pypi.python.org/pypi/nose/`](http://pypi.python.org/pypi/nose/)
> 4.  virtualenv – [`pypi.python.org/pypi/virtualenv`](http://pypi.python.org/pypi/virtualenv)

不要只是手动下载并且安装这些软件包，你应该看一下别人的建议，尤其看看针对你的操作系统别人是怎样建议你安装和使用的。同样的软件包在不一样的操作系统上面的安装方式是不一样的，不一样版本的 Linux 和 OSX 会有不同，而 Windows 更是不同。

我要预先警告你，这个过程会是相当无趣。在业内我们将这种事情叫做 “yak shaving(剃牦牛)”。它指的是在你做一件有意义的事情之前的一些准备工作，而这些准备工作又是及其无聊冗繁的。你要做一个很酷的 Python 项目，但是创建骨架目录需要你安装一些软件包，而安装软件包之前你还要安装软件包安装工具(package installer)，而要安装这个工具你还得先学会如何在你的操作系统下安装软件，真是烦不胜烦呀。

无论如何，还是克服困难把。你就把它当做进入编程俱乐部的一个考验。每个程序员都会经历这条道路，在每一段“酷”的背后总会有一段“烦”的。

> **NOTE:**有时候 python 的安装程序不会把`C:\Python27\Script`加入到系统的`PATH`中，如果你遇到了这个问题，就参照练习 0 自己把这个目录加上：`[Environment]::SetEnvironmentVariable("Path", "$env:Path;C:\Python27\Scripts", "User")`

## 创建骨架内容

首先使用下述命令创建你的骨架目录：

```py
$ mkdir projects
$ cd projects/
$ mkdir skeleton
$ cd skeleton
$ mkdir bin NAME tests docs 
```

我使用了一个叫`projects`的目录，用来存放我自己的各个项目。然后我在里边建立了一个叫做`skeleton`的文件夹，这就是我们新项目的基础目录。其中叫做`NAME`的文件夹是你的项目的主文件夹，你可以将它任意取名。

接下来我们要配置一些初始文件：

```py
$ touch NAME/__init__.py
$ touch tests/__init__.py 
```

在 windows 上，你可以这样配置初始文件：

```py
$ new-item -type file NAME/__init__.py
$ new-item -type file tests/__init__.py 
```

以上命令为你创建了空的模组目录，以供你后面为其添加代码。然后我们需要建立一个`setup.py`文件，这个文件在安装项目的时候我们会用到它：

```py
try:
    from setuptools import setup
except ImportError:
    from distutils.core import setup

config = {
    'description': 'My Project',
    'author': 'My Name',
    'url': 'URL to get it at.',
    'download_url': 'Where to download it.',
    'author_email': 'My email.',
    'version': '0.1',
    'install_requires': ['nose'],
    'packages': ['NAME'],
    'scripts': [],
    'name': 'projectname'
}

setup(**config) 
```

编辑这个文件，把自己的联系方式写进去，然后放到那里就行了。

最后你需要一个简单的测试专用的骨架文件叫`tests/NAME_tests.py`：

```py
from nose.tools import *
import NAME

def setup():
    print "SETUP!"

def teardown():
    print "TEAR DOWN!"

def test_basic():
    print "I RAN!" 
```

## 最终的目录结构

当你完成一切设置,你的目录应该看起来像我在这里:

```py
skeleton/
     NAME/
         __init__.py
     bin/
     docs/
     setup.py
     tests/
         NAME_tests.py
         __init__.py 
```

从现在开始，你应该在这个目录下运行命令。如果你不能执行`ls -R`命令并看到相似的目录结构，说明你在一个错误的目录下。比如，人们经常会到`tests/`目录下尝试执行文件，那肯定是无法运行的。要运行你应用的测试用例，你也应该在目录`tests/`的上一层目录执行，加入你这样执行：

```py
$ cd tests/   # WRONG! WRONG! WRONG!
$ nosetests

----------------------------------------------------------------------
Ran 0 tests in 0.000s

OK 
```

那结果肯定是错误的，你应当在`tests/`目录的上一层目录执行，所以为了修正你的错误，你应该这样做：

```py
$ cd ..   # get out of tests/
$ ls      # CORRECT! you are now in the right spot
NAME                bin             docs            setup.py        tests
$ nosetests
.
----------------------------------------------------------------------
Ran 1 test in 0.004s

OK 
```

一定要记住这一点，因为人们经常犯这个错误。

## 测试你的配置

安装了所有上面的软件包以后，你就可以做下面的事情了：

```py
$ nosetests
.
----------------------------------------------------------------------
Ran 1 test in 0.007s

OK 
```

下一节练习中我会告诉你`nosetests`的功能，不过如果你没有看到上面的画面，那就说明你哪里出错了。确认一下你的`NAME`和`tests`目录下存在 `__init__.py`， 并且你没有把 `tests/NAME_tests.py` 命名错。

## 使用这个项目骨架

剃牦牛的事情已经做的差不多了，以后每次你要新建一个项目时，只要做下面的事情就可以了：

> 1.  拷贝这份骨架目录，把名字改成你新项目的名字。
> 2.  再将`NAME`模组更名为你需要的名字，它可以是你项目的名字，当然别的名字也行。
> 3.  编辑`setup.py`让它包含你新项目的相关信息。
> 4.  重命名`tests/NAME_tests.py`，让它的名字匹配到你模组的名字。
> 5.  使用`nosetests`检查有无错误。
> 6.  开始写代码吧。

## 小测验

本节没有附加题，不过有一些小测验需要你完成

> 1.  找文档阅读，学会使用你前面安装了的软件包。
> 2.  阅读关于`setup.py`的文档，看它里边可以做多少配置。Python 的安装器并不是一个好软件，所以使用起来也非常奇怪。
> 3.  创建一个项目，在模组目录里写一些代码，并让这个模组可以运行。
> 4.  在 `bin` 目录下放一个可以运行的脚本，找材料学习一下怎样创建可以在系统下运行的 Python 脚本。
> 5.  在你的 `setup.py`中加入`bin`这个目录，这样你安装时就可以连它安装进去。
> 6.  使用`setup.py`安装你的模组，并确定安装的模组可以正常使用，最后使用`pip`将其卸载。

## 常见问题

### Q: 这些说明在 windows 上也是一样的吗？

> 是的，不过也取决于你 windows 系统的版本，你可能需要在配置上下点功夫它才能正常运行，坚持研究并尝试，直到你能在 windows 上正常的运行这个骨架，或者你可以找一些有 python+windows 开发经验的人帮忙。

### Q: 我好像不能在 windows 上运行`nosetests`

> 有时候 python 的安装程序不会把`C:\Python27\Script`加入到系统的`PATH`中，如果你遇到了这个问题，就参照练习 0 自己把这个目录加上：`[Environment]::SetEnvironmentVariable("Path", "$env:Path;C:\Python27\Scripts", "User")`

### Q: 我应该在我的配置文件`setup.py`中放些什么？

> 确认你阅读了 distutils 的文档`http://docs.python.org/distutils/setupscript.html`。

### Q:我好像不能加载`NAME`模块，而且还有个"ImportError"报错

> 确认你创建了`NAME/__init__.py`这个文件，如果你用的 windows 系统，确认你没有把这文件命名为`NAME/__init__.py.txt`，很多程序员都犯过这个错。

### Q: 我们为什么需要一个`bin/`文件夹

> 这只是一个用来存放在命令行执行的脚本的地方，不是用来存在模块的。

### Q: 你有一个真实的项目举例吗？

> 有很多 python 写的项目都可以作为实例，你可以看看我创建的这个简单的项目`https://gitorious.org/python-modargs`.

### Q: 我的`nosetests`运行时只显示正在运行一个测试，这是正确的吗？

> 是的，我的也是这么显示的。