# 段移动原理

# 段移动原理

如果你未曾用过 Vim 的段移动命令 (`[[`, `]]`, `[]` and `][`)，现在花上几秒读读它们的帮助文档。 也顺便读读`:help section`。

还是不懂？这不是什么问题，我第一次读这些的时候也是这样。 在写代码之前，我们先岔开来学习这些移动是怎么工作的，然后在下一章我们将使得我们的 Potion 插件支持它们。

## Nroff 文件

四个"段移动"命令正如其字面上的含义，可以用来在文件的"段"之间移动。

这些命令默认为[nroff 文件][]而设计。 Nroff 类似于 LaTex 或 Markdown -- 它是用来写标记文本的(最终会生成 UNIX man 页面)。

Nroff 文件使用一组"macro"来定义"段头"。 比如，这里有个来自于`awk`man 页面的例子：

```
:::nroff
.SH NAME                                                     ***
awk \- pattern-directed scanning and processing language
.SH SYNOPSIS                                                 ***
.B awk
[
.BI \-F
.I fs
]
[
.BI \-v
.I var=value
]
[
.I 'prog'
|
.BI \-f
.I progfile
]
[
.I file ...
]
.SH DESCRIPTION                                              ***
.I Awk
scans each input
.I file
for lines that match ... 
```

以`.SH`开头的行就是段头。我用`***`把它们标记出来。 四个段移动命令将在段头行之间移动你的光标。

Vim 以`.`和 nroff 的段头符开始的任何行当做一个段头，*即使你编辑的不是 nroff 文件*！

你可以改变`sections`设置来改变段头符，但 Vim 依旧需要在行开头有一个点，而且段头符必须是成对的字符， 所以这样改对 Potion 文件不会有足够的灵活性。

## 括号

段移动命令*也*查看另一样东西：一个打开或关闭的大括号(`{`或`}`)作为行的第一个字符。

`[[`和`]]`查看开括号，而`[]`和`][`查看闭括号。

这额外的"行为"使得你可以在 C 风格语言的段之间轻松移动。 然而，这些规则也依旧没有顾及你正在编辑的文件类型！

加入下面内容到一个缓冲区里：

```
:::text
Test           A B
Test

.SH Hello      A B

Test

{              A
Test
}                B

Test

.H World       A B

Test
Test           A B 
```

现在执行`:set filetype=basic`来告诉 Vim 这是一个 BASIC 文件，并尝试段移动命令。

`[[`和`]]`命令将在标记为`A`的行之间移动，而`[]`和`][`将在标记为`B`的行之间移动。

这告诉我们，Vim 总是用同样的两条规则来处理段移动，即使没有一条是起作用的(比如在 BASIC 中的情况)！

## 练习

再次阅读`:help section`，现在你应该可以理解段移动了。

也顺便读读`:help sections`吧。