# Operator-Pending 映射

# Operator-Pending 映射

这一章我们将来探索 Vim 映射系统中另外一个神奇的部分：“Operator-Pending 映射”。开始之前，我们先解释下这里面的几个词含义。

一个 Operator（操作）就是一个命令，你可以在这个命令的后面输入一个 Movement（移动）命令，然后 Vim 开始对文本执行前面的操作命令，这个操作命令会从你当前所在的位置开始执行，一直到这个移动命令会把你带到的位置结束。

常用到的 Operator 有`d`，`y`和`c`。例如：

```
:::text
按键   操作       移动
----   --------   -------------
dw     删除       到下一个单词
ci(    修改       在括号内
yt,    复制       到逗号 
```

## Movement 映射

Vim 允许你创建任何新的 movements，这些 movements 可以跟所有命令一起工作。执行下面的命令：

```
:::vim
:onoremap p i( 
```

在缓冲区中输入下面的文字：

```
:::text
return person.get_pets(type="cat", fluffy_only=True) 
```

把光标放到单词“cat”上，然后敲击`dp`。结果会发生什么？Vim 会删除括号内的所有文字。你可以把这个新建的 movements 当作“参数”。

`onoremap`命令会告诉 Vim 当它在等待一个要附加在 operator 后面的 movement 的时候，如果这个 movement 是`p`的话，它会把它当作`i(`。所以当我们在运行`dp`的时候，就象是在对 Vim 说“delete parameters”，而 Vim 会把它理解为“在括号内删除”。

我们现在可以立马对所有的 operators 使用这个新建的映射。再次在缓冲区中输入上面的文字（或者直接把之前修改恢复一下）。

```
:::text
return person.get_pets(type="cat", fluffy_only=True) 
```

把光标放到单词“cat”上，然后敲击`cp`。这次又会发生什么？Vim 会删除括号中的所有文字，不过这一次删除之后 Vim 会处于插入模式，这是因为你使用的是“change”，而不是“delete”。

再看一个示例。执行下面的命令：

```
:::vim
:onoremap b /return<cr> 
```

现在把下面的文字输入到缓冲区：

```
:::python
def count(i):
    i += 1
    print i

    return foo 
```

把光标放到第二行的`i`上，然后按下`db`。会发生生么？Vim 把整个函数体中直到`return`上面的内容都删除了，`return`就是上面的映射使用 Vim 的通用查找得到的结果。

当你想搞清楚怎么定义一个新的 operator-pending movement 的时候，你可以从下面几个步骤来思考：

1.  在光标所在的位置开始。
2.  进入可视模式(charwise)。
3.  ... 把映射的按键放到这里 ...
4.  所有你想包含在 movement 中的文字都会被选中。

你所要做的工作就是在第三步中填上合适的按键。

## 改变开始位置

你可能已经从上面所学的东西中意识到一个了问题。如果我们定义的 movements 都是从光标所在的位置开始的话，那么这就会限制我们做一些我们想使用 movement 来做的事情。

但是 Vim 并不会限制你去做你想做的事情，所以对于这个问题肯定有解决办法。执行下面的命令：

```
:::vim
:onoremap in( :<c-u>normal! f(vi(<cr> 
```

这个命令看起来有些复杂，不过我们还是先试试它能干什么。将下面的文字输入缓冲区：

```
:::python
print foo(bar) 
```

把光标放到单词`print`上面，然后敲击`cin(`。Vim 会删除括号内的内容然后进入插入模式，并且光标会停留在括号的中间。

你可以将这个映射理解为“在下一个括号内(inside next parentheses)”。它会对当前行光标所在位置的下一个括号内的文本执行 operator。

我们再创建一个“在上一个括号内(inside last parentheses)”的 movement 进行对照。（在这里使用“前一个(previous)“可能更准确，但这会覆盖“段落(paragraph)”movement）

```
:::vim
:onoremap il( :<c-u>normal! F)vi(<cr> 
```

先试试确保这个命令可以工作。

那么这些映射是怎么工作的呢？首先，`<c-u>`比较特殊，可以先不用管（你只需要相信我这个东西可以让这个映射在任何情况下都能正常工作）。如果我们删除它的话，这个映射会变成这个样子：

```
:::vim
:normal! F)vi(<cr> 
```

`:normal!`会在后面的章节谈到，现在你只需要知道它可以在常用模式下模拟按下按键。例如，运行 `:normal! dddd`会删除两行，就像按下`dddd`。映射后面的`<cr>`是用来执行`:normal!`命令的。

那么现在我们可以认为这个映射的关键是运行下面这些按键组成的命令：

```
:::vim
F)vi( 
```

This is fairly simple: 这个命令很容易理解：

*   `F)`: 向后移动到最近的`)`字符。
*   `vi(`: 进入可视模式选择括号内的所有内容。

这个 movement 结束在在可视模式下选择中我们想操作的文本，然后 Vim 会对选中的文本执行操作，就像通常情况一样。

## 一般规则

下面两条规则可以让你可以很直观的以多种方式创建 operator-pending 映射：

*   如果你的 operator-pending 映射以在可视模式下选中文本结束，Vim 会操作这些文本。
*   否则，Vim 会操作从光标的原始位置到一个新位置之间的文本。

## 练习

为"around next parentheses"和"around last parentheses"创建 operator-pending 映射

为打括号创建类似的 in/around next/last 的 mappings。

阅读`:help omap-info`，看看你可不可以搞清楚`<c-u>`是干啥的。