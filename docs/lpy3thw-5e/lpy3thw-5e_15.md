## 练习 13：参数、解包、变量

现在我们将快速进入`终端`（又称`PowerShell`）版本的`python`世界。如果你正确完成了[First](https://learncodethehardway.org/first_steps/python/) Steps，你应该已经学会了如何启动终端并运行一个简单的 Python 脚本。在本课程的后面，你将学习如何更广泛地使用终端，但在这个练习中，我们只是做一个小小的测试。

首先，我希望你使用 Jupyter 的新 Python 文件创建一个名为`ex13.py`的文件：

1.  左侧有一个列出你目录中文件的列表。

2.  在那个列表的上方有一个蓝色的`[+]`按钮。

3.  点击那个按钮，滚动到底部，那里应该有一个带有 Python“蓝色和黄色蛇”标志的`Python` `File`按钮。

4.  点击那个按钮打开一个新的面板，你可以在其中输入代码。

5.  立即使用鼠标选择`File > Save Python File`或按住`CTRL`键并按下`s`键（通常显示为`Ctrl-S`，但你不需要按住 Shift 键来输入`S`）。

6.  这将打开一个模态提示，上面写着“重命名文件”。输入“ex13”，它应该保留`.py`，但确保这个输入显示为`ex13.py`。

7.  点击蓝色的`[Rename]`按钮将文件保存在那个目录中。

保存了那个文件之后，你可以将以下代码输入到文件中：

列表 13.1: ex13.py

```py
1   **from** sys **import** argv
2   # read the What You Should See section for how to run this
3   script, first, second, third = argv
4
5   **print(**"The script is called:", script**)**
6   **print(**"Your first variable is:", first**)**
7   **print(**"Your second variable is:", second**)**
8   **print(**"Your third variable is:", third**)**
```

我建议你只输入一两行代码，然后执行以下操作：

1.  再次保存你的文件。按下`CTRL-s`是最简单的方法，但如果你记不住，可以使用菜单。这次它不应该要求你“重命名”文件，而应该直接保存。

2.  你的文件现在保存在你的项目目录中。如果你还记得*[First Steps](https://learncodethehardway.org/first_steps/python/)*部分，你创建了一个目录在`~/Projects/lpythw`，当你运行`jupyter-lab`时，你首先`cd ~/Projects/lpythw`。

3.  现在打开一个新的终端（在 Windows 上是 PowerShell），再次输入`cd ~/Projects/lpythw/`以进入该终端。

4.  最后，输入`python ex13.py first 2nd 3rd`。（在终端中输入时不要加句号。）当你这样做时，你应该看到*绝对什么都没有*！是的，这点*非常重要*。你只输入了一两行代码，所以在你的代码中没有`print`语句。这意味着它不会打印任何内容，但这是好事。如果出现错误，那么停下来弄清楚你做错了什么。你是不是打错了那行代码？你运行了`python ex13.py`吗？那也是错误的。你必须运行`python ex13.py first 2nd 3rd`。（再次强调，不要在终端中加句号。）

#### 如果你迷路了

如果你对自己所在位置感到困惑，可以在 macOS 上使用`open`命令，在 Windows 上使用`start`命令。如果你输入以下内容：

```py
1   open .
```

在 macOS 电脑上，它会打开一个窗口，显示当前终端所在位置的内容。当你输入以下内容时，同样的情况也会发生：

```py
1   start .
```

在 Windows 中在 PowerShell 中。这样做将帮助你将“文件在窗口中的文件夹中”这个概念连接到“文件在终端（PowerShell）中的目录中”。

如果这是你第一次看到这个建议，那么回到*[First Steps](https://learncodethehardway.org/first_steps/python/)*部分，重新查看它，因为你似乎错过了这个重要概念。

### 代码描述

在第`1`行，我们有一个称为“import”的东西。这是你从 Python 功能集中添加功能到你的脚本的方式。Python 不会一次性给你所有功能，而是要求你说出你打算使用的功能。这样可以使你的程序保持简洁，同时也作为其他程序员阅读你代码时的文档。

`argv`是“参数变量”，在编程中是一个非常标准的名称，你会发现它在许多其他语言中被使用。这个变量*保存*你在运行 Python 脚本时传递的参数。在练习中，你将有机会更多地玩弄它，并看看会发生什么。

第 3 行“unpacks” `argv`，这样，它不再保存所有参数，而是被分配给四个你可以使用的变量：`script`、`first`、`second`和`third`。这可能看起来很奇怪，但“unpack”可能是最好的描述它的词。它只是说，“取出`argv`中的任何内容，解包它，并按顺序分配给左边的所有这些变量。”

之后我们就像平常一样打印它们出来。

### 等一下！features 还有另一个名字

我在这里称它们为“features”（你`import`来使你的 Python 程序做更多事情的小东西），但没有人称它们为 features。我只是用这个名字是因为我需要欺骗你学习它们是什么，而不带有行话。在继续之前，你需要学习它们的真实名称：`modules`。

从现在开始，我们将称这些为“features”，我们`import`*modules*。我会说像，“你想要导入`sys`模块。”其他程序员也称它们为“库”，但让我们坚持使用模块。

### 你应该看到的内容

警告！

注意！你一直在没有命令行参数运行 Python 脚本。如果你只输入`python3 ex13.py`，那么你做错了！请仔细看我是如何运行的。每当看到使用 argv 时都适用。

当你输入完所有代码后，它应该像这样最终运行（而且你*必须*传递*三个*命令行参数）：

```py
1   $ python ex13.py first 2nd 3rd
2   The script is called: ex13.py
3   Your first variable is: first
4   Your second variable is: 2nd
5   Your third variable is: 3rd
```

这是你使用不同参数进行几次运行时应该看到的内容：

```py
1   $ python ex13.py stuff things that
2   The script is called: ex13.py
3   Your first variable is: stuff
4   Your second variable is: things
5   Your third variable is: that
```

这里有一个更多的例子，显示它可以是任何东西：

```py
1   $ python ex13.py apple orange grapefruit
2   The script is called: ex13.py
3   Your first variable is: apple
4   Your second variable is: orange
5   Your third variable is: grapefruit
```

你实际上可以用任何三个你想要的东西替换`first`、`2nd`和`3rd`。

如果你没有正确运行它，那么你会得到这样的错误：

命令失败：python ex13.py first 2nd Traceback (most recent call last): File “/Users/zedshaw/Project s/learncodethehardway.com/private/db/modules/learn-python-the-hard-way-5e-section-1/code/ex13.py”，第 3 行，在脚本、第一个、第二个、第三个 = argv ValueError: not enough values to unpack (expected 4, got 3)

当你在运行时没有在命令中放足够的参数时会发生这种情况（在这种情况下只有`first 2nd`）。注意，当我运行它时，我给了它`first 2nd`，这导致它出现了一个关于“需要超过 3 个值来解包”的错误，告诉你没有给足够的参数。

### 学习练习

1.  尝试给你的脚本提供少于三个参数。看看你会得到什么错误？看看你能否解释清楚。

2.  编写一个参数较少的脚本和一个参数较多的脚本。确保给解包的变量起一个好名字。

3.  结合`input`和`argv`编写一个脚本，从用户那里获取更多输入。不要想得太多。只需使用`argv`获取一些内容，然后使用`input`从用户那里获取其他内容。

4.  记住模块给你提供了功能。模块。模块。记住这一点，因为我们以后会用到它。

### 常见学生问题

**当我运行它时，我得到** `ValueError: need more than 1 value to unpack`。记住一个重要的技能是注意细节。如果你看一下*你应该看到的内容*部分，你会看到我是如何在命令行上运行脚本的。你应该完全复制我运行它的方式。那里还有一个巨大的警告解释了你刚刚犯的错误，所以请再次注意。

**`argv`和** `input()` **之间有什么区别？** 区别在于用户需要在哪里提供输入。如果他们在命令行上给你的脚本输入，那么使用`argv`。如果你希望他们在脚本运行时使用键盘输入，那么使用`input()`。

**命令行参数是字符串吗？** 是的，它们作为字符串传入，即使你在命令行上输入了数字。使用`int()`来转换它们，就像使用`int(input())`一样。

**你如何使用命令行？** 你应该已经学会如何快速流利地使用它了，但如果你在这个阶段需要学习，那么请阅读附录 A，“命令行速成课程”。

**我无法将** `argv` **与** `input()` **结合起来**。不要想得太多。只需在脚本末尾加上两行，使用`input()`获取一些内容然后打印出来。从那里开始尝试更多同时使用两者的方法。

**为什么我不能这样做** `input('? ') = x`**？** 因为这是反向的工作方式。按照我的方式去做，它就会起作用。

**为什么你要让我一次只输入一行？** 初学者和专业人士最常犯的错误就是他们输入一大块代码，运行一次，然后因为所有的错误而哭泣。编程语言中的错误令人沮丧，并经常指向源代码中错误的位置。如果你一次只输入几行代码，你会更频繁地运行代码，当出现错误时，你知道这可能是你刚刚输入的那几行代码有问题。当你输入 100 行代码时，你将花费接下来的 5 天来寻找所有的错误，最终放弃。省点麻烦，一次只输入一点点。这就是我和大多数有能力的程序员在现实生活中所做的。
