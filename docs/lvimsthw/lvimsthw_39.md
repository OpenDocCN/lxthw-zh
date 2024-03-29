# 循环

# 循环

你可能会惊讶地发现，作为一本关于编程语言的书，在前 35 章里我们压根就没有提到循环！ Vimscript 提供了非常多的方式操作文本(比如，`normal!`)， 因此循环并不像在其他大多数语言中的那么必要。

即使如此，总有一天你会需要用到它的，所以现在让我们探讨 Vim 支持的两种主要的循环。

## For 循环

第一种循环是`for`循环。如果你习惯了 Java,C 或 Javascript 中的`for`循环，它看上去有点古怪。 但是你会发现这种写法十分地优雅。执行下面的命令：

```
:::vim
:let c = 0

:for i in [1, 2, 3, 4]
:  let c += i
:endfor

:echom c 
```

Vim 显示`10`，就是把列表中的每一个元素的加起来的结果。Vimscript 的`for`循环遍历整个列表 (或我们待会会提到的字典)。

Vimscript 中不存在 C 风格的`for (int i = 0; i < foo; i++)`。这一开始可能难以适应， 但一旦习惯你就不会再怀念 C 风格的 for 循环了。

## While 循环

Vim 也支持经典的`while`循环。执行下面命令：

```
:::vim
:let c = 1
:let total = 0

:while c <= 4
:  let total += c
:  let c += 1
:endwhile

:echom total 
```

Vim 再次显示`10`。几乎每一个程序猿都熟悉这个循环，所以我们不会浪费时间讲解。 你将会很少用到它。铭记它以备不时之需。

## 练习

阅读`:help for`.

阅读`:help while`.