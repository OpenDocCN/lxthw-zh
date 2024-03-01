# 练习 13.参数, 解包, 变量

# 练习 13.参数, 解包, 变量

在这节练习中，我们将学到另外一种将变量传递给脚本的方法(脚本就是你写的 `.py` 程序)。你已经知道，如果要运行 `ex13.py`，只要在命令行运行 `python ex13.py` 就可以了。这句命令中的 `ex13.py` 部分就是所谓的“参数(argument)”，我们现在要做的就是写一个可以接收参数的脚本。

将下面的程序写下来，后面你会看到详细的解释：

```py
from sys import argv

script, first, second, third = argv

print "The script is called:", script
print "Your first variable is:", first
print "Your second variable is:", second
print "Your third variable is:", third 
```

第一行代码中，我们用到一个`import`语句，这是将 Python 的功能模块加入你自己脚本的方法。Python 不会一下子将它所有的功能提供给你，而是让你需要什么就调用什么。这样可以让你的程序更加精简，而后面的程序员看到你的代码的时候，这些“import”语句可以作为提示，让他们明白你的代码用到了哪些功能。

`argv`就是所谓的“参数变量(argument variable)”，它是一个非常标准的编程术语。在其他的编程语言里你也可以看到它。这个变量包含了你传递给 Python 的参数。通过后面的练习你将对它有更多的了解。

代码的第 3 行将 `argv`进行“解包(unpack)”，与其将所有参数放到同一个变量下面，我们将每个参数赋予一个变量名： script, first, second, 以及 third。这也许看上去有些奇怪,不过”解包”可能是最好的描述方式了。它的含义很简单：“把 argv 中的东西解包，将所有的参数依次赋予左边的变量名”。

接下来，就是正常的打印输出了。

## 等一下! 功能还有另外一个名字

前面我们使用`import`让你的程序实现更多的功能，把`import`称为“功能”。我希望你可以在没接触到正式术语的时候就弄懂它的功能。在继续下去之前, 你需要知道它们的真正名称：模块(modules)。

从现在开始我们将把这些我们导入(import)进来的功能称作模块。你将看到类似这样的说法：“你需要把 sys 模块 import 进来。”也有人将它们称作“库(libraries)”，不过我们还是叫它们模块吧。

## 你看到的结果

像下面的示例一样将你的脚本运行起来（你必须在命令行里传递 3 个参数）：

```py
$ python ex13.py first 2nd 3rd
The script is called: ex13.py
Your first variable is: first
Your second variable is: 2nd
Your third variable is: 3rd 
```

如果你每次输入的参数不一样，那你看到的输出结果也会略有不同：

```py
$ python ex13.py stuff things that
The script is called: ex13.py
Your first variable is: stuff
Your second variable is: things
Your third variable is: that
$
$ python ex13.py apple orange grapefruit
The script is called: ex13.py
Your first variable is: apple
Your second variable is: orange
Your third variable is: grapefruit 
```

你可以将`first`, `2nd`, 和 `3rd` 替换成任意你喜欢的 3 个参数

如果你没有运行对，你可能会看到的错误信息：

```py
$ python ex13.py first 2nd
Traceback (most recent call last):
  File "ex13.py", line 3, in <module>
    script, first, second, third = argv
ValueError: need more than 3 values to unpack 
```

## 附加题

> 1.  给你的脚本三个以下的参数。看看会得到什么错误信息。试着解释一下。
> 2.  再写两个脚本，其中一个接受更少的参数，另一个接受更多的参数，在参数解包时给它们取一些有意义的变量名。
> 3.  将 `raw_input` 和 `argv` 一起使用，让你的脚本从用户手上得到更多的输入。
> 4.  记住“模块(modules)”为你提供额外功能。多读几遍把这个词记住，因为我们后面还会用到它。

## 常见问题

### Q:当我运行脚本的时候，有个报错: `need more than 1 value to unpack`.

> 一定记住，关注细节是学习编程的三要素之一。如果你仔细看了我是如何在命令行运行脚本的，你也能把你的脚本正确的运行起来。

### Q:`argv` 和 `raw_input()`有什么区别?

> 它们的不同之处在于要求用户输入的位置不同。如果你想让用户在命令行输入你的参数，你应该使用`argv`.，如果你希望用户在脚本执行的过程中输入参数，那就就要用到`raw_input()`。

### Q:命令行输入的参数是字符串吗?

> 是的，如果你需要输入数字，可以使用`int()`把他们转化成整数，可以参考 `int(raw_input())`.

### Q:如何使用命令行?

> 通过这节练习，你其实已经快速的学会如何使用命令行了，如果在此阶段你想深入学习的话，你可以阅读这本书的附录 A--命令行速成教程。

### Q: 我不知道怎样把`argv` 和 `raw_input()`结合起来使用.

> 不要想太多. 用`raw_input()`修改脚本后面的两行代码，然后打印输出就行。然后试试用更多的方式来同时使用这两种方法修改脚本。

### Q:为什么我不能这么写`raw_input('? ') = x`?

> 因为这种写法正好是将它正常运行方法的逆序，按照我的写法修改，就能正常运行了。