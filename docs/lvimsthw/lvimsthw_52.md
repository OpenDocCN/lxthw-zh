# 高级折叠

# 高级折叠

在上一章里我们用 Vim 的`indent`折叠方式，在 Potion 文件中增加了一些快捷而肮脏的折叠。

打开`factorial.pn`并用`zM`关闭所有的折叠。文件现在看起来就像这样：

```
:::text
factorial = (n):
+--  5 lines: total = 1

10 times (i):
+--  4 lines: i string print 
```

展开第一个折叠，它看上去会是这样：

```
:::text
factorial = (n):
    total = 1
    n to 1 (i):
+---  2 lines: # Multiply the running total.
    total.

10 times (i):
+--  4 lines: i string print 
```

这真不错，但我个人喜欢依照内容来折叠每个块的第一行。 在本章中我们将写下一些自定义的折叠代码，并在最后实现这样的效果：

```
:::text
factorial = (n):
    total = 1
+---  3 lines: n to 1 (i):
    total.

+--  5 lines: 10 times (i): 
```

这将更为紧凑，而且(对我来说)更容易阅读。 如果你更喜欢`indent`也不是不行，不过最好学习本章来对 Vim 中实现折叠的代码的更深入的了解。

## 折叠原理

为了写好自定义的折叠，我们需要了解 Vim 对待("thinks")折叠的方式。简明扼要地讲解下规则：

*   文件中的每行代码都有一个"foldlevel"。它不是为零就是一个正整数。
*   foldlevel 为零的行*不会*被折叠。
*   有同等级的相邻行会被折叠到一起。
*   如果一个等级 X 的折叠被关闭了，任何在里面的、foldlevel 不小于 X 的行都会一起被折叠，直到有一行的等级小于 X。

通过一个例子，我们可以加深理解。打开一个 Vim 窗口然后粘贴下面的文本进去。

```
:::text
a
    b
    c
        d
        e
    f
g 
```

执行下面的命令来设置`indent`折叠：

```
:::vim
:setlocal foldmethod=indent 
```

花上一分钟玩一下折叠，观察它是怎么工作的。

现在执行下面的命令来看看第一行的 foldlevel:

```
:::vim
:echom foldlevel(1) 
```

Vim 显示`0`。现在看看第二行的：

```
:::vim
:echom foldlevel(2) 
```

Vim 显示`1`。试一下第三行：

```
:::vim
:echom foldlevel(3) 
```

Vim 再次显示`1`。这意味着第 2,3 行都属于一个 level1 的折叠。

这是每一行的 foldlevel:

```
:::text
a           0
    b       1
    c       1
        d   2
        e   2
    f       1
g           0 
```

重读这一部分开头的几条规则。打开或关闭每个折叠，观察 foldlevel，并确保你理解了为什么会这样折叠。

一旦你已经自信地认为你理解了每行的 foldlevel 是怎么影响折叠结构的，继续看下一部分。

## 首先：做一个规划

在我们埋头敲键盘之前，先为我们的折叠功能规划出几条大概的规则。

首先，同等缩进的行应该要折叠到一块。我们也希望*上*一行也一并折叠，达到这样的效果：

```
:::text
hello = (name):
    'Hello, ' print
    name print. 
```

将折叠成这样：

```
:::text
+--  3 lines: hello = (name): 
```

空行应该算入*下*一行，因此折叠底部的空行不会包括进去。这意味着类似这样的内容：

```
:::text
hello = (name):
    'Hello, ' print
    name print.

hello('Steve') 
```

将折叠成这样：

```
:::text
+--  3 lines: hello = ():

hello('Steve') 
```

而*不是*这样：

```
:::text
+--  4 lines: hello = ():
hello('Steve') 
```

这当然是属于个人偏好的问题，但现在我们就这么定了。

## 开始

现在开始写我们的自定义折叠代码吧。 打开 Vim，分出两个分割，一个是`ftplugin/potion/folding.vim`，另一个是示例代码`factorial.pn`。

在上一章我们关闭并重新打开 Vim 来使得`folding.vim`生效，但其实还有更简单的方法。

不要忘记每当设置一个缓冲区的`filetype`为`potion`的时候，在`ftplugin/potion/`下的所有文件都会被执行。 这意味着仅需在`factorial.pn`的分割下执行`:set ft=potion`，Vim 将重新加载折叠代码！

这比每次都关闭并重新打开文件要快多了。 唯一需要铭记的是，你得*保存*`folding.vim`到硬盘上，否则未保存的改变不会起作用。

## Expr 折叠

为了获取折叠上的无限自由，我们将使用 Vim 的`expr`折叠。

我们可以继续并从`folding.vim`移除`foldignore`，因为它只在使用`indent`的时候生效。 我们也打算让 Vim 使用`expr`折叠，所以把`folding.vim`改成这样：

```
:::vim
setlocal foldmethod=expr
setlocal foldexpr=GetPotionFold(v:lnum)

function! GetPotionFold(lnum)
    return '0'
endfunction 
```

第一行只是告诉 Vim 使用`expr`折叠。

第二行定义了 Vim 用来计算每一行的 foldlevel 的表达式。 当 Vim 执行某个表达式，它会设置`v:lnum`为它需要的对应行的行号。 我们的表达式将把这个数字作为自定义函数的参数。

最后我们定义一个对任意行均返回`0`的占位(dummy)函数。 注意它返回的是一个字符串而不是一个整数。等会我们就知道为什么这么做。

继续并重新加载折叠代码(保存`folding.vim`并对`factorial.pn`执行`:set ft=potion`)。 我们的函数对任意行均返回`0`,所以 Vim 将不会进行任何折叠。

## 空行

让我们先解决空行的特殊情况。修改`GetPotionFold`函数成这样：

```
:::vim
function! GetPotionFold(lnum)
    if getline(a:lnum) =~? '\v^\s*$'
        return '-1'
    endif

    return '0'
endfunction 
```

我们增加了一个`if`语句来处理空行。它是怎么起效的？

首先，我们使用`getline(a:lnum)`来以字符串形式获取当前行的内容。

我们把结果跟正则表达式`\v^\s*$`比较。记得`\v`表示"very magic"(我的意思是，正常的)模式。 这个正则表达式将匹配"行的开头，任何空白字符，行的结尾"。

比较是用大小写不敏感比较符`=~?`完成的。 技术上我们不用担心大小写，毕竟我们只匹配空白，但是我偏好在比较字符串时使用更清晰的方式。 如果你喜欢，可以使用`=～`代替。

如果需要唤起 Vim 中的正则表达式的回忆，你应该回头重读"基本正则表达式"和"Grep Operator"这两部分。

如果当前行包括一些非空白字符，它将不会匹配，我们将如前返回`0`。

如果当前行*匹配*正则表达式(i.e. 比如它是空的或者只有空格)，就返回字符串`'-1'`。

之前我说过一行的 foldlevel 可以为 0 或者正整数，所以这会发生什么？

## 特殊折叠

你自定义的表达式可以直接返回一个 foldlevel，或者返回一个"特殊字符串"来告诉 Vim 如何折叠这一行。

`'-1'`正是其中一种特殊字符串。它告知 Vim，这一行的 foldlevel 为"undefined"。 Vim 将把它理解为"该行的 foldlevel 等于其上一行或下一行的较小的那个 foldlevel"。

这不是我们计划中的*最终*结果，但我们可以看到，它已经足够接近了，而且必将达到我们的目标。

Vim 可以把 undefined 的行串在一起，所以假设你有三个 undefined 的行和接下来的一个 level1 的行， 它将设置最后一行为 1,接着是倒数第二行为 1,然后是第一行为 1。

在写自定义的折叠代码时，你经常会发现有几种行你可以容易地设置好它们的 foldlevel。 然后你就可以使用`'-1'`(或我们等会会看到的其他特殊 foldlevel)来"瀑布般地"设置好剩余的行的 foldlevel。

如果你重新加载了`factorial.pn`的折叠代码，Vim*依然*不会折叠任何行。 这是因为所有的行的 foldlevel 要不是为 0,就是为"undefined"。 等级为 0 的行将影响 undefined 的行，最终导致所有的行的 foldlevel 都是`0`。

## 缩进等级辅助函数

为了处理非空行，我们需要知道它们的缩进等级，所以让我们来创建一个辅助函数替我们计算它。 在`GetPotionFold`之上加上下面的函数：

```
:::vim
function! IndentLevel(lnum)
    return indent(a:lnum) / &shiftwidth
endfunction 
```

重新加载折叠代码。在`factorial.pn`缓冲区执行下面的命令来测试你的函数：

```
:::vim
:echom IndentLevel(1) 
```

Vim 显示`0`,因为第一行没有缩进。现在在第二行试试看：

```
:::vim
:echom IndentLevel(2) 
```

这次 Vim 显示`1`。第二行开头有四个空格，而`shiftwidth`设置为 4,所以 4 除以 4 得 1。

我们用它除以缓冲区的`shiftwidth`来得到缩进等级。

为什么我们使用`&shiftwidth`而不是直接除以 4？ 如果有人偏好使用 2 个空格缩进他们的 Potion 代码，除以 4 将导致不正确的结果。 使用`shiftwidth`可以允许任何缩进的空格数。

## 再来一个辅助函数

下一步的方向尚未明朗。让我们停下来想想为了确定折叠非空行，还需要什么信息。

我们需要知道每一行的缩进等级。我们已经通过`IndentLevel`函数得到了，所以这个条件已经满足了。

我们也需要知道*下一个非空行*的缩进等级，因为我们希望折叠段头行到对应的缩进段中去。

让我们写一个辅助函数来得到给定行的下一个非空行的 foldlevel。在`IndentLevel`上面加入下面的函数：

```
:::vim
function! NextNonBlankLine(lnum)
    let numlines = line('$')
    let current = a:lnum + 1

    while current <= numlines
        if getline(current) =~? '\v\S'
            return current
        endif

        let current += 1
    endwhile

    return -2
endfunction 
```

这个函数有点长，不过很简单。让我们逐个部分分析它。

首先我们用`line('$')`得到文件的总行数。查查文档来了解`line()`。

接着我们设变量`current`为下一行的行号。

然后我们开始一个会遍历文件中每一行的循环。

如果某一行匹配正则表达式`\v\S`，表示匹配"有一个*非*空白字符"，它就是非空行，所以返回它的行号。

如果某一行不匹配，我们就循环到下一行。

如果循环到达文件尾行而没有任何返回，这就说明当前行之后*没有*非空行！ 我们返回`-2`来指明这种情况。`-2`不是一个有效的行号，所以用来简单地表示"抱歉，没有有效的结果"。

我们可以返回`-1`，因为它也是一个无效的行号。 我甚至可以选择`0`,因为 Vim 中的行号从`1`开始！ 所以为何我选择`-2`这个看上去奇怪的选项？

我选择`-2`是因为我们正处理着折叠代码，而`'-1'`(和`'0'`)是特殊的 Vim foldlevel 字符串。

当眼睛正扫过代码时，看到`-1`，脑子里会立刻浮现起"undefined foldlevel"。 这对于`0`也差不多。 我在这里选择`-2`，就是为了突出它*不是*foldlevel，而是表示一个"错误"。

如果你觉得这不可理喻，你可以安心地替换`-2`为`-1`或`0`。 这只是代码风格问题。

## 完成折叠函数

本章已经显得比较冗长了，所以现在把折叠函数包装起来(wrap up)吧。把`GetPotionFold`修改成这样：

```
:::vim
function! GetPotionFold(lnum)
    if getline(a:lnum) =~? '\v^\s*$'
        return '-1'
    endif

    let this_indent = IndentLevel(a:lnum)
    let next_indent = IndentLevel(NextNonBlankLine(a:lnum))

    if next_indent == this_indent
        return this_indent
    elseif next_indent < this_indent
        return this_indent
    elseif next_indent > this_indent
        return '>' . next_indent
    endif
endfunction 
```

这里的新代码真多！让我们分开一步步来看。

### 空行

首先我们检查空行。这里没有改动。

如果不是空行，我们就准备好处理非空行的情况了。

### 获取缩进等级

接下来我们使用两个辅助函数来获取当前行和下一个非空行的折叠等级。

你可能会疑惑万一`NextNonBlankLine`返回错误码`-2`该怎么办。 如果这发生了，`indent(-2)`还会继续工作。对一个不存在的行号执行`indent()`将返回`-1`。 你可以试试`:echom indent(-2)`看看。

`-1`除以任意大于 1 的`shiftwidth`将返回`0`。 这好像有问题，不过它实际上不会有。现在暂时不用纠结于此。

### 同级缩进

既然我们已经得到了当前行和下一非空行的缩进等级，我们可以比较它们并决定如何折叠当前行。

这里又是一个`if`语句：

```
:::vim
if next_indent == this_indent
    return this_indent
elseif next_indent < this_indent
    return this_indent
elseif next_indent > this_indent
    return '>' . next_indent
endif 
```

首先我们检查这两行是否有同样的缩进等级。如果相等，我们就直接把缩进等级当作 foldlevel 返回！

举个例子：

```
:::text
a
b
    c
    d
e 
```

假设我们正处理包含`c`的那一行，它的缩进等级为 1。 下一个非空行("d")的缩进等级也是一样的，所以返回`1`作为 foldlevel。

假设我们正处理"a"，它的缩进等级为 0。这跟下一非空行("b")的等级是一样的，所以返回`0`作为 foldlevel。

在这个简单的示例中，可以分出两个 foldlevel。

```
:::text
a       0
b       ?
    c   1
    d   ?
e       ? 
```

纯粹出于运气，这种情况也处理了在最后一行对特殊的"error"情况。 记得我们说过，如果我们的辅助函数返回`-2`,`next_indent`将会是`0`。

在这个例子中，行"e"的缩进等级为`0`，而`next_indent`也被设为`0`，所以匹配这种情况并返回`0`。 现在 foldlevels 是这样：

```
:::text
a       0
b       ?
    c   1
    d   ?
e       0 
```

### 更低的缩进等级

我们再来看看那个`if`语句：

```
:::vim
if next_indent == this_indent
    return this_indent
elseif next_indent < this_indent
    return this_indent
elseif next_indent > this_indent
    return '>' . next_indent
endif 
```

`if`的第二部分检查下一行的缩进等级是否比当前行*小*。就像是例子中行"d"的情况。

如果符合，将再一次返回当前行的缩进等级。

现在我们的例子看起来像这样：

```
:::text
a       0
b       ?
    c   1
    d   1
e       0 
```

当然，你可以用`||`把两种情况连接起来，但是我偏好分开来写以显得更清晰。 你的想法可能不同。这只是风格问题。

又一次，纯粹出于运气，这种情况处理了其他来自辅助函数的"error"状态。设想我们有一个文件像这样：

```
:::text
a
    b
    c 
```

第一种情况处理行"b"：

```
:::text
a       ?
    b   1
    c   ? 
```

行"c"为最后一行，有着缩进等级 1。由于我们的辅助函数，`next_indent`将设为`0`。 这匹配`if`语句的第二部分，所以 foldlevel 设为当前缩进等级，也即是`1`。

```
:::text
a       ?
    b   1
    c   1 
```

结果如我们所愿，"b"和"c"折叠到一块去了。

### 更高的缩进等级

现在还剩下最后一个`if`语句：

```
:::vim
if next_indent == this_indent
    return this_indent
elseif next_indent < this_indent
    return this_indent
elseif next_indent > this_indent
    return '>' . next_indent
endif 
```

而我们的例子现在是：

```
:::text
a       0
b       ?
    c   1
    d   1
e       0 
```

只剩下行"b"我们还不知道它的 foldlevel，因为：

*   "b"的缩进等级为`0`。
*   "c"的缩进等级为`1`。
*   1 既不等于 0,又不小于 0。

最后一种情况检查下一行的缩进等级是否*大于*当前行。

这种情况下 Vim 的`indent`折叠并不理想，也是为什么我们一开始打算写自定义的折叠代码的原因！

最后的情况表示，当下一行的缩进比当前行多，它将返回一个以`>`开头和*下一行*的缩进等级构成的字符串。 这是什么意思呢？

从折叠表达式中返回的，类似`>1`的字符串表示 Vim 的特殊 foldlevel 中的一种。 它告诉 Vim 当前行需要*展开*一个给定 level 的折叠。

在这个简单的例子中，我们可以简单返回表示缩进等级的数字，但我们很快将看到为什么要这么做。

这种情况下"b"将展开 level1 的折叠，使我们的例子变成这样：

```
:::text
a       0
b       >1
    c   1
    d   1
e       0 
```

这就是我们想要的！万岁！

## 复习

如果你一步步做到了这里，你应该为自己感到骄傲。即使像这样的简单折叠代码，也会是令人绞尽脑汁的。

在我们结束之前，让我们重温最初的`factorial.pn`代码，看看我们的折叠表达式是怎么处理每一行的 foldlevel 的。

重新把`factorial.pn`代码列在这里：

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

首先，所有的空行的 foldlevel 都将设为 undefined：

```
:::text
factorial = (n):
    total = 1
    n to 1 (i):
        # Multiply the running total.
        total *= i.
    total.
                                         undefined
10 times (i):
    i string print
    '! is: ' print
    factorial (i) string print
    "\n" print. 
```

所有折叠等级跟下一行的*相等*的行，它们的 foldlevel 等于折叠等级：

```
:::text
factorial = (n):
    total = 1                            1
    n to 1 (i):
        # Multiply the running total.    2
        total *= i.
    total.
                                         undefined
10 times (i):
    i string print                       1
    '! is: ' print                       1
    factorial (i) string print           1
    "\n" print. 
```

在下一行的缩进比当前行*更少*的情况下，也是同样的处理：

```
:::text
factorial = (n):
    total = 1                            1
    n to 1 (i):
        # Multiply the running total.    2
        total *= i.                      2
    total.                               1
                                         undefined
10 times (i):
    i string print                       1
    '! is: ' print                       1
    factorial (i) string print           1
    "\n" print.                          1 
```

最后的情况是下一行的缩进比当前行更多。如果这样，那就设当前行的折叠等级为展开下一行的折叠：

```
:::text
factorial = (n):                         >1
    total = 1                            1
    n to 1 (i):                          >2
        # Multiply the running total.    2
        total *= i.                      2
    total.                               1
                                         undefined
10 times (i):                            >1
    i string print                       1
    '! is: ' print                       1
    factorial (i) string print           1
    "\n" print.                          1 
```

现在我们已经得到了文件中每一行的 foldlevel。剩下的就是由 Vim 来解决未定义(undefined)的行。

不久前我说过 undefined 的行将选择相邻行中较小的那个 foldlevel。

Vim 手册是这么讲的，但不是十分地确切。 如果真是这样的，我们的文件中的空行的 foldlevel 为 1，因为它相邻两行的 foldlevel 都为 1。

事实上，空行的 foldlevel 将被设定成 0！

这就是为什么我们不直接设置`10 times(i):`的 foldlevel 为 1。我们告诉 Vim 该行*展开*一个 level1 的折叠。 Vim 能够意识到这意味着 undefined 的行应该设置成`0`而不是`1`。

这样做背后的理由也许深埋在 Vim 的源码里。 通常 Vim 在处理 undefined 行时，对待特殊的 foldlevel 的行为都是很聪明的，所以你总能如愿以偿。

一旦 Vim 处理完 undefined 行，它会得到一个对每一行的折叠情况的完整描述，看上去像这样：

```
:::text
factorial = (n):                         1
    total = 1                            1
    n to 1 (i):                          2
        # Multiply the running total.    2
        total *= i.                      2
    total.                               1
                                         0
10 times (i):                            1
    i string print                       1
    '! is: ' print                       1
    factorial (i) string print           1
    "\n" print.                          1 
```

这就是了，我们完成啦！重新加载折叠代码，在`factorial.pn`中玩玩我们神奇的折叠功能吧！

## 练习

阅读`:help foldexpr`.

阅读`:help fold-expr`。注意你的表达式可以返回的所有特殊字符串。

阅读`:help getline`。

阅读`:help indent()`。

阅读`:help line()`。

想想为什么我们用`.`连接`>`和我们折叠函数给出的数字。如果我们使用的是`+`会怎样？

我们在全局空间中定义了辅助函数，但这不是好的做法。把它改到脚本本地的命名空间中。

放下本书，出去玩一下，让你的大脑从本章中清醒清醒。