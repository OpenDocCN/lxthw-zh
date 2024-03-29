# 函数式编程

# 函数式编程

现在让我们小憩一下，聊一聊一种你可能听过的编程风格：[函数式编程](https://secure.wikimedia.org/wikipedia/en/wiki/Functional_programming)。

如果你用过 Python，Ruby 或 Javascript，*甚或*Lisp，Scheme，Clojure 或 Haskell， 你应该会觉得把函数作为变量类型，用不可变的状态作为数据结构是平常的事。 如果你没用过，你可以放心地跳过这一章了，但我还是鼓励你找机会去试试并拓宽自己的视野。

Vimscript 具有使用函数式风格进行编程的潜力，不过会有点吃力。 我们可以创建一些辅助函数来让这个过程少些痛苦。

继续前进并创建`functional.vim`文件，这样你就不用反复地重新击打每一行代码。 这个文件将会成为这一章的草稿本。

## 不可变的数据结构

不幸的是，Vim 没有类似于 Clojure 内置的 vector 和 map 那样的不可变集合， 不过通过一些辅助函数，我们可以在一定程度上模拟出来。

在你的文件加上下面的函数:

```
:::vim
function! Sorted(l)
    let new_list = deepcopy(a:l)
    call sort(new_list)
    return new_list
endfunction 
```

保存并 source 文件，然后执行`:echo Sorted([3,2,4,1])`来试试看。 Vim 输出`[1,2,3,4]`。

这跟调用内置的`sort()`函数有什么区别呢？关键在于第一行：`let new_list = deepcopy(a:l)`。 Vim 的`sort()`*就地*重排列表，所以我们先创建一个列表的副本，并排序*副本*, 这样原本的列表不会被改变。

这样就避免了副作用，并帮助我们写出更容易推断和测试的代码。让我们加入更多同样风格的辅助函数：

```
:::vim
function! Reversed(l)
    let new_list = deepcopy(a:l)
    call reverse(new_list)
    return new_list
endfunction

function! Append(l, val)
    let new_list = deepcopy(a:l)
    call add(new_list, a:val)
    return new_list
endfunction

function! Assoc(l, i, val)
    let new_list = deepcopy(a:l)
    let new_list[a:i] = a:val
    return new_list
endfunction

function! Pop(l, i)
    let new_list = deepcopy(a:l)
    call remove(new_list, a:i)
    return new_list
endfunction 
```

除了中间的一行和它们接受的参数，每一个函数都是一样的。保存并 source 文件，在一些列表上试试它们。

`Reversed()`接受一个列表并返回一个新的倒置了元素的列表。

`Append()`返回一个在原列表的基础上增加了给定值的新列表。

`Assoc()`("associate"的缩写)返回一个给定索引上的元素被替换成新值的新列表。

`Pop()`返回一个给定索引上的元素被移除的新列表。

## 作为变量的函数

Vimscript 支持使用变量储存函数，但是相关的语法有点愚钝。执行下面的命令：

```
:::vim
:let Myfunc = function("Append")
:echo Myfunc([1, 2], 3) 
```

Vim 意料之中地显示`[1, 2, 3]`。注意我们使用的变量以大写字母开头。 如果一个 Vimscript 变量要引用一个函数，它就要以大写字母开头。

就像其他种类的变量，函数也可以储存在列表里。执行下面命令：

```
:::vim
:let funcs = [function("Append"), function("Pop")]
:echo funcs1 
```

Vim 显示`['a', 'c']`。`funcs`变量*不*需要以大写字母开头，因为它储存的是列表，而不是函数。 列表的内容不会造成任何影响。

## 高阶函数

让我们创建一些用途广泛的高阶函数。如果你需要解释，高阶函数就是接受*别的*函数并使用它们的函数。

我们将从`map`函数开始。在你的文件中添加这个：

```
:::vim
function! Mapped(fn, l)
    let new_list = deepcopy(a:l)
    call map(new_list, string(a:fn) . '(v:val)')
    return new_list
endfunction 
```

保存并 source 文件，执行下面命令试试看：

```
:::vim
:let mylist = [[1, 2], [3, 4]]
:echo Mapped(function("Reversed"), mylist) 
```

Vim 显示`[[2, 1], [4, 3]]`，正好是对列表中的每一个元素应用了`Reversed()`的结果。

`Mapped()`是如何起作用的？我们又一次用`deepcopy()`创建新的列表，修修改改，返回修改后的副本 —— 没什么是新的。有门道的是中间的部分。

`Mapped()`接受两个参数：一个 funcref("储存一个函数的变量"在 Vim 里的说法)和一个列表。 我们使用内置的`map()`函数实现真正的工作。现在就阅读`:help map()`来看它怎么工作的。

现在我们将创建一些通用的高阶函数。把下面的代码加入到你的文件：

```
:::vim
function! Filtered(fn, l)
    let new_list = deepcopy(a:l)
    call filter(new_list, string(a:fn) . '(v:val)')
    return new_list
endfunction 
```

用下面的命令尝试`Filtered()`：

```
:::vim
:let mylist = [[1, 2], [], ['foo'], []]
:echo Filtered(function('len'), mylist) 
```

Vim 显示`[[1, 2], ['foo']]`。

`Filtered()`接受一个谓词函数和一个列表。它返回一个列表的副本， 而这个列表只包括将自身作为谓词函数的输入参数并返回真值的元素。 这里我们使用了内置的`len()`，让它过滤掉所有长度为 0 的元素。

最后我们创建了`Filtered()`的好基友(counterpart)：

```
:::vim
function! Removed(fn, l)
    let new_list = deepcopy(a:l)
    call filter(new_list, '!' . string(a:fn) . '(v:val)')
    return new_list
endfunction 
```

像使用`Filtered()`一样试一下：

```
:::vim
:let mylist = [[1, 2], [], ['foo'], []]
:echo Removed(function('len'), mylist) 
```

Vim 显示`[[], []]`。`Removed()`就像`Filtered()`，不过它只保留谓词函数返回*非*真值的元素。

代码中的唯一不同在于调用命令前面的`'!' .`，它把谓词函数的结果取反。

## 效率

考虑到 Vim 不得不持续地创建新的副本并垃圾回收旧的对象，你可能会认为不停地制造副本是种浪费。

是的，你是对的！Vim 的列表不像 Clojure 的 vector 那样支持结构共享(structural sharing)， 所以这里所有的复制操作是昂贵的。

有时这的确是个问题。如果你需要使用庞大的列表，程序就会因此变慢。 在现实世界，你可能会吃惊地发现你几乎不会注意到其中的差别。

想想看吧：当我正写下本章时，Vim 占用了 80M 内存(而且我可是装了*一堆*插件)。 我的笔记本总共有*8G*内存。有一些列表的副本被创建出来，这会造成可被察觉的不同吗？ 当然这取决于列表的大小，但在大多数情况下答案将会是"No"。

作为比较，我的 Firefox 打开了五个 tab，现在正饕餮着*1.22G*内存。

你将需要自己判断，什么时候这种编程风格会导致不可接受的低效率。

## 练习

阅读`:help sort()`。

阅读`:help reverse()`。

阅读`:help copy()`。

阅读`:help deepcopy()`。

阅读`:help map()`，如果你未曾读过。

阅读`:help function()`。

修改`Assoc()`, `Pop()`, `Mapped()`, `Filtered()`和`Removed()`来支持字典类型。 你可能需要阅读`:help type()`来帮助自己。

实现`Reduced()`。

倒给自己一杯最喜欢的饮料。这一章真激烈(intense)！