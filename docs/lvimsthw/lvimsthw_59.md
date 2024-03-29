# 还剩下什么？

# 还剩下什么？

如果已经读到了这里并且完成了所有的例子和练习，你现在对 Vimscript 基础的掌握就很牢固了。 不要担心，还有*许多*东西需要学呢！

如果你求知若渴，这里还有一些东西值得你去探索。

## 配色方案

在本书中我们给 Potion 文件添加了语法高亮。作为硬币的另一面，我们也可以创建配色方案来决定每种语法元素的颜色。

制作 Vim 的配色方案非常简单直白，甚至有点重复。阅读`:help highlgiht`来学习基础知识。 你可能想要看看一些内置的配色方案来看他们怎么组织文件的。

如果你渴望挑战，看看我自己的[灰太狼](https://github.com/sjl/badwolf/blob/master/colors/badwolf.vim)配色方案来了解我是怎么用 Vimscript 来为我简化定义及维护工作的。 注意"palette"字典和`HL`函数，它们动态地生成`highlight`命令。

## Command 命令

许多插件允许用户使用键映射和函数调用来交互，但有一些偏好使用 Ex 命令。 举个例子，[Fugitive](https://github.com/tpope/vim-fugitive)插件创建类似`:Gbrowse`和`:Gdiff`并把调用它们的方式留给用户定制。

像这样的命令是通过`:command`命令创建的。阅读`:help user-commands`来学习怎样给自己制作一个。 你应该已经学会了足够的 Vimscript 知识来帮助自己理解 Vim 文档，并以此来学习新的命令。

## 运行时路径

在本书中，关于 Vim 怎么加载某个文件时，我都是用"使用 Pathogen"应付过去的。 鉴于你已经懂得了许多 Vimscript 知识，你可以阅读`:help runtimepath`并查看[Pathogen 源代码](https://github.com/tpope/vim-pathogen/blob/master/autoload/pathogen.vim) 来找出幕后隐藏的真相。

## Omnicomplete

Vim 提供了许多不同的方法来补全文本(浏览`:help ins-completion`)。 大多数都很简单，但其中最强大的是"omnicomplete"， 它允许你调用一个自定义的 Vimscript 函数来决定你想到的各种补全方式。

当你决定对 omnicomplete 一探究竟，你可以从`:help omnifunc`和`:help coml-omni`开始你的征途。

## 编译器支持

在我们的 Potion 插件中，我们创建了一些编译并执行 Potion 文件的映射。 Vim 提供了更深入的支持来跟编译器交互，包括解析编译器错误并生成一个整洁的列表让你跳转到对应的错误。

如果你对此感兴趣，你可以从通读整篇`:help quickfix.txt`开始深入。 不过，我得提醒你`errorformat`不适合心脏虚弱的人阅读。

## 其他语言

这本书专注于 Vimscript，但 Vim 也提供了其他语言的接口，比如 Python, Ruby, 和 Lua。 这意味着如果不喜欢 Vimscript，你可以使用其他语言拓展 Vim。

当然还是需要了解 Vimscript 来编辑你的`~/.vimrc`，和理解 Vim 提供给其他语言的 API。 但使用一个替代语言可能是从 Vimscript 的局限之处解放出来的好办法，尤其在写大型插件的时候。

如果你想了解更多用特定语言拓展 Vim，查看下列对应的帮助文档：

*   `:help Python`
*   `:help Ruby`
*   `:help Lua`
*   `:help perl-using`
*   `:help MzScheme`

## Vim 文档

作为最后的部分，这里列出了一些 Vim 帮助条目，它们非常有用，有趣，有道理，或者仅仅是好玩(排名不分先后)：

*   `:help various-motions`
*   `:help sign-support`
*   `:help virtualedit`
*   `:help map-alt-keys`
*   `:help error-messages`
*   `:help development`
*   `:help tips`
*   `:help 24.8`
*   `:help 24.9`
*   `:help usr_12.txt`
*   `:help usr_26.txt`
*   `:help usr_32.txt`
*   `:help usr_42.txt`

## 练习

去为你想要的功能写一个 Vim 插件，向全世界分享你的成果！