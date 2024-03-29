# 基本折叠

# 基本折叠

如果从未在 Vim 里使用过代码折叠，你不知道你都错过了什么。 阅读`:help usr_28`并花费时间在日常工作中使用它。 一旦到了铭记于指的程度，你就可以继续本章了。

## 折叠类型

Vim 支持六种不同的决定如何折叠你的文本的折叠类型。

### Manual

你手动创建折叠并且折叠将被 Vim 储存在内存中。 当你关闭 Vim 时，它们也将一并烟消云散，而下次你编辑文件时将不得不重新创建。

在你把它跟一些自定义的创建折叠的映射结合起来时，这种方式会很方便。 在本书中，我们不会这么做，但当你想这么做的时候，它会帮上忙。

### Marker

Vim 基于特定的字符组合折叠你的代码。

这些字符通常放置于注释中(比如`// {{{`)， 不过在有些语言里，你可以使用该语言自己的语法代替，比如 javascript 的`{`和`}`。

纯粹为了你的编辑器，用注释割裂你的代码看上去有点丑，但好处是你可以定制特定的折叠。 如果你想以特定的方式组织一个大文件，这个类型将是非常棒的选择。

### Diff

在 diff 文件时使用该特定的折叠类型。我们不会讨论它，因为 Vim 会自动使用它。

### Expr

这让你可以用自定义的 Vimscript 来决定折叠的位置。它是最为强大的方式，不过也需要最繁重的工作。 下一章我们将讲到它。

### Indent

Vim 使用你的代码的缩进来折叠。同样缩进等级的代码折叠到一块，空行则被折叠到周围的行一起去。

这是最便捷的方式，因为你的代码已经缩进过了；你仅仅需要启动它。 这将是我们用来折叠 Potion 代码的第一种方式。

## Potion 折叠

让我们再一次看一下 Potion 实例代码：

```
:::text
factorial = (n):
    total = 1
    n to 1 (i):
        total *= i.
    total.

10 times (i):
    i string print
    '! is: ' print
    factorial (i) string print
    "\n" print. 
```

函数体和循环体已经缩进好了。这意味着我们可以不怎么费力就能实现一些基本的缩进。

在我们开始之前，在`total *= i`上添加一个注释，这样我们就有一个供测试的多行内部块。 你将在做练习的时候学到为什么我们需要这么做，但暂时先信任我。现在文件看上去就像这样：

```
:::text
factorial = (n):
    total = 1
    n to 1 (i):
        # Multiply the running total.
        total *= i.
    total.

10 times (i):
    i string print
    '! is: ' print
    factorial (i) string print
    "\n" print. 
```

在你的 Potion 插件的版本库下创建一个`ftplugin`文件夹，然后在里面创建一个`potion`文件夹。 最后，在*`potion`文件夹*里面创建一个`folding.vim`文件。

不要忘了每次 Vim 设置一个 buffer 的`filetype`为`potion`时，它都会执行这个文件中的代码。 (因为它位于一个叫`potion`的文件夹)

将所有的折叠相关的代码放在同一个文件显然是一个好主意，它能帮我们维护我们的插件的繁多的功能。

在这个文件中加入下面一行：

```
:::vim
setlocal foldmethod=indent 
```

关闭 Vim，重新打开`factoria.pn`。用`zR`，`zM`和`za`尝试折叠功能。

一行 Vimscript 代码就能带来一些有用的折叠！这真是太酷了！

你可能注意到`factorial`函数的内循环里面的那几行不能折叠，尽管它们缩进了。 为什么会这样？

事实上，在使用`indent`折叠时，Vim 默认忽略以`#`字符开头的行。 这在编辑 C 文件时很有用(这时`#`表示一个预编译指令)，但在编辑其他文件时不怎么有意义。

让我们在`ftplugin/potion/folding.vim`中添加多一行来修复问题：

```
:::vim
setlocal foldmethod=indent
setlocal foldignore= 
```

关闭并重新打开`factorial.pn`，现在内部块可以正常地折叠了。

## 练习

阅读`:help foldmethod`.

阅读`:help fold-manual`.

阅读`:help fold-marker`和`:help foldmarker`.

阅读`:help fold-indent`.

阅读`:help fdl`和`:help foldlevelstart`.

阅读`:help foldminlines`.

阅读`:help foldignore`.