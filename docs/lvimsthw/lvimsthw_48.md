# 基本语法高亮

# 基本语法高亮

既然已经移除前进路上的绊脚石，是时候开始为我们的 Potion 插件写下一些有用的代码。 我们将从一些简单的语法高亮开始。

在你的插件的 repo 中创建`syntax/potion.vim`。把下面的代码放到你的文件里：

```
:::vim
if exists("b:current_syntax")
    finish
endif

echom "Our syntax highlighting code will go here."

let b:current_syntax = "potion" 
```

关闭 Vim，然后打开你的`factorial.pn`文件。 你也许或也许不能看到消息，取决于你是否有其他插件在该插件之后输出消息。 如果你执行`:message`，你将会看到这个文件的确已经加载了。

**注意：** 每次我告诉你打开 Potion 文件，我是想要你在一个新的 Vim 窗口或进程里打开，而不是在一个分割或 tab。 打开一个新的 Vim 窗口导致 Vim 为此重新加载你所有的插件，而打开一个分割则不会。

代码文件开头和结尾的那几行是一个惯用法，如果这个缓冲区的语法高亮已经启动了，那就无需重新加载。

## 高亮关键字

在本章的剩下部分，我们将忽略文件开头和结尾的`if`和`let`防御墙。不要移除那几行，只是眼不见为净而已。

用下面的代码替换掉文件中的占位符`echom`：

```
:::vim
syntax keyword potionKeyword to times
highlight link potionKeyword Keyword 
```

关闭`factorial.pn`并重新打开它。`to`和`times`被高亮成你的配色方案中的关键字类型了！

这两行展示了 Vim 中的基本的语法高亮。为了高亮某个语法：

*   你首先要用`syntax keyword`或相关命令(我们待会会提到)，定义一组语法类型。
*   然后你要把这组类型链接到高亮组(highlighting groups)。 一个高亮组是你在配色方案里定义的东西，比如"函数名应该是蓝色的"。

这可以让插件作者决定有意义的语法类型分组，然后链接到通用的高亮组。 这同时也让配色方案创作者决定通用的程序结构，而不需要考虑单独的语言。

除了在我们的玩具程序中用到的，Potion 还有其他的关键字，所以让我们修改 syntax 文件来一并高亮它们。

```
:::vim
syntax keyword potionKeyword loop times to while
syntax keyword potionKeyword if elsif else
syntax keyword potionKeyword class return

highlight link potionKeyword Keyword 
```

首先要说的是：最后一行没有改掉。我们依然告诉 Vim 所有在`potionKeyword`中的内容应该作为`Keyword`高亮。

我们现在新增三行，每行都以`syntax keyword potionKeyword`开头。 这意味着多次执行这个命令不会*重置*语法类型分组 —— 而是扩增它！这使得你可以化整为零地定义分组。

怎样定义分组取决于你：

*   你可以仅仅一行密密麻麻地写满所有的内容。
*   你可以划分成几行，来满足每行 80 列的规则以便于阅读。
*   你可以每一项都独占一行，来使得 diff 的结果更加清晰。
*   你可以跟我在这里做的一样，把相关的项放在同一行。

## 高亮函数

Vim 的另一个高亮组是`Function`。这就来加入一些 Potion 的内置函数到我们的高亮文件。 把你的 syntax 文件修改成这样：

```
:::vim
syntax keyword potionKeyword loop times to while
syntax keyword potionKeyword if elsif else
syntax keyword potionKeyword class return

syntax keyword potionFunction print join string

highlight link potionKeyword Keyword
highlight link potionFunction Function 
```

关闭并重新打开`factorial.pn`，你将看到内置的 Potion 函数现在已经高亮了。

它的工作原理就跟关键字高亮一样。我们定义了新的语法类型分组并链接到不同的高亮组。

## 练习

想一想为什么文件开头的`if exists`和结尾的`let`是有用的。如果你搞不懂，不要担心。 我也曾就这个问题问过 Tim Pope。

浏览`:help syn-keyword`。注意提到`iskeyword`的部分。

阅读`:help iskeyword`.

阅读`:help group-name`来了解一些配色方案作者常用的通用高亮组。