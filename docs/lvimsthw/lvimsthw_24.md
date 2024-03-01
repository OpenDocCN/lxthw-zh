# 条件语句

# 条件语句

每种编程语言都有产生分支流程的方法，在 Vimscript 中，这是用`if`语句实现的。 `if`语句是 Vimscript 中产生分支的基本方法。这里没有类似 Ruby 中的`unless`语句， 所以代码中所有的判断都需要用`if`实现。

在谈论 Vim 的`if`语句之前，我们需要花费额外的时间讲讲语法，这样可以在同一页里讲完它。

## 多行语句

有时你在一行里写不下所需的 Vimscript。在讲到自动命令组时，我们已经遇到过这样的例子了。 这里是我们之前写过的代码：

```
:::vim
:augroup testgroup
:    autocmd BufWrite * :echom "Baz"
:augroup END 
```

在理想的情况下，你可以分开成三行来写。但在手工执行命令的时候，这样写就太冗长了。 其实，你可以用管道符(`|`)来隔开每一行。执行下面的命令：

```
:::vim
:echom "foo" | echom "bar" 
```

Vim 会把它当作两个独立的命令。如果你看不到两行输出，执行`:messages`查看消息日志。

在本书的剩余部分，当你想手工执行一个命令，却对输入新行和冒号感到心烦时，试试用管道隔开， 在一行里写完。

## If 的基本用法

现在让我们回到正题上来，执行下面的命令：

```
:::vim
:if 1
:    echom "ONE"
:endif 
```

Vim 将显示`ONE`，因为整数`1`是"truthy"。现在执行下面命令：

```
:::vim
:if 0
:    echom "ZERO"
:endif 
```

Vim 将*不*显示`ZERO`，因为整数`0`是"falsy"。让我们看看对字符串是怎么处理的。执行下面命令：

```
:::vim
:if "something"
:    echom "INDEED"
:endif 
```

结果可能让你吃惊。Vim*不会*把非空字符串当作"truthy"，所以什么也没有显示。

让我们打破沙锅问到底。执行下面的命令：

```
:::vim
:if "9024"
:    echom "WHAT?!"
:endif 
```

这次 Vim*会*显示了！为什么会这样？

为了搞懂发生了什么，执行下面三个命令：

```
:::vim
:echom "hello" + 10
:echom "10hello" + 10
:echom "hello10" + 10 
```

第一个命令使得 Vim 输出`10`，第二个命令输出`20`，第三个则又一次输出`10`！

在探究了所有的命令后，对于 Vimscript 我们可以得出结论：

*   如有必要，Vim 将强制转换变量(和字面量)的类型。在解析`10 + "20foo"`时，Vim 将把 `"20foo"`转换成一个整数(`20`)然后加到`10`上去。
*   以一个数字开头的字符串会被强制转换成数字，否则会转换成`0`
*   在所有的强制转换完成*后*，当`if`的判断条件等于非零整数时，Vim 会执行`if`语句体。

## Else 和 Elseif

Vim，像 Python 一样，支持"else"和"else if"分句。执行下面的命令：

```
:::vim
:if 0
:    echom "if"
:elseif "nope!"
:    echom "elseif"
:else
:    echom "finally!"
:endif 
```

Vim 输出`finally!`，因为前面的判断条件都等于 0，而 0 代表 falsy。

## 练习

来一杯啤酒，安抚自己因 Vim 中的字符串强制转换而受伤的心。