# 函数

# 函数

一如大多数编程语言，Vimscript 支持函数。让我们看看如何创建函数，然后再讨论它们的古怪之处。

执行下面的命令：

```
:::vim
:function meow() 
```

你可能会认为这将定义函数`meow`。不幸的是，情况不是这样的，我们已经掉进了 Vimscript 其中的一个坑。

**没有作用域限制的 Vimscript 函数必须以一个大写字母开头！**

即使你*真的*给函数限定了作用域(我们待会会谈到)，你最好也用一个大写字母开头。 大多数 Vimscript 程序猿都是这么做的，所以不要破例。

ok，是时候认真地定义一个函数了。执行下面的命令：

```
:::vim
:function Meow()
:  echom "Meow!"
:endfunction 
```

这次 Vim 愉快地定义了一个函数。让我们试试运行它：

```
:::vim
:call Meow() 
```

不出所料，Vim 显示`Meow!`

让我们试试令它返回一个值。执行下面的命令：

```
:::vim
:function GetMeow()
:  return "Meow String!"
:endfunction 
```

现在执行这个命令试试：

```
:::vim
:echom GetMeow() 
```

Vim 将调用这个函数并把结果传递给`echom`，显示`Meow String!`。

## 调用函数

我们已经看到，Vimscript 里调用函数有两种不同的方法。

当你想直接调用一个函数时，使用`call`命令。执行下面命令：

```
:::vim
:call Meow()
:call GetMeow() 
```

第一个函数输出`Meow!`，然而第二个却没有任何输出。当你使用`call`时，返回值会被丢弃， 所以这种方法仅在函数具有副作用时才有用。

第二种方法是在表达式里调用函数。这次不需要使用`call`，你只需引用函数的名字。 执行下面的命令：

```
:::vim
:echom GetMeow() 
```

正如我们见过的，这会调用`GetMeow`并把返回值传递给`echom`。

## 隐式返回

执行下面的命令：

```
:::vim
:echom Meow() 
```

这将会显示两行：`Meow!`和`0`。第一个显然来自于`Meow`内部的`echom`。第二个则告诉我们， 如果一个 Vimscript 函数不返回一个值，它隐式返回`0`。看我们可以利用这一点做什么。执行下面命令：

```
:::vim
:function TextwidthIsTooWide()
:  if &l:textwidth ># 80
:    return 1
:  endif
:endfunction 
```

这个函数涉及到我们之前学到的许多重要概念：

*   `if`语句
*   将选项作为变量
*   访问特定作用域里的选项变量
*   大小写敏感的比较

如果你对以上内容感到陌生，最好翻到前几章温习一遍。

现在我们已经定义了一个函数，该函数告诉我们当前缓冲区的`textwidth`会不会设得‘太过宽’。 (因为 80 字符的限制适用于除了 HTML 之外的任何代码文件)

现在让我们使用它。执行下面的命令：

```
:::vim
:set textwidth=80
:if TextwidthIsTooWide()
:  echom "WARNING: Wide text!"
:endif 
```

在这里我们做了什么？

*   一开始我们设置全局的`textwidth`为`80`。
*   接着我们运行一个 if 语句判断`TextwidthIsTooWide()`是否为真。
*   由于不满足条件，`if`语句体(译注：包括函数内的和函数外的)不会被执行。

因为我们没有显式返回一个值，Vim 从函数中返回代表'falsy'的`0`。试试改变一下。运行下面的命令：

```
:::vim
:setlocal textwidth=100
:if TextwidthIsTooWide()
:  echom "WARNING: Wide text!"
:endif 
```

这次函数中的`if`执行了它的语句体，返回`1`，并且我们手工输入的`if`语句也执行了*它*的语句体。

## 练习

阅读`:help :call`。目前先忽略关于"范围"的内容。你可以传递多少参数给一个函数？感到惊讶不？

阅读`:help E124`第一自然段并找出你可以用哪些字符来命名函数。可以用下划线吗？点(Dashes)呢？ 重音符号(Accented characters)？Unicode 符号？如果读了文档还是搞不清楚，试一下看看。

阅读`:help return`。这个命令的缩写("short form")是什么？(我说了你千万不要用它) 在你的预期之内吗？如果不是，为什么？