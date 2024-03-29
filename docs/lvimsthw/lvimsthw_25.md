# 比较

# 比较

我们已经学习了条件语句，但如果我们不能进行比较，`if`语句并不怎么有用。 当然 Vim 允许我们比较值的大小，只是不会像看上去那么一目了然。

执行下面的命令：

```
:::vim
:if 10 > 1
:    echom "foo"
:endif 
```

显然，Vim 会显示`foo`。现在执行下面的命令：

```
:::vim
:if 10 > 2001
:    echom "bar"
:endif 
```

Vim 什么都不显示，因为`10`不比`2001`大。目前为止，一切正常。运行下面命令：

```
:::vim
:if 10 == 11
:    echom "first"
:elseif 10 == 10
:    echom "second"
:endif 
```

Vim 显示`second`。没什么好惊讶的。让我们试试比较字符串。执行下面命令：

```
:::vim
:if "foo" == "bar"
:    echom "one"
:elseif "foo" == "foo"
:    echom "two"
:endif 
```

Vim 输出`two`。还是没什么好惊讶的，所以我开头说的(译注：Vim 的比较不像看上去那么直白)到底是指什么呢？

## 大小写敏感

执行下面的命令：

```
:::vim
:set noignorecase
:if "foo" == "FOO"
:    echom "vim is case insensitive"
:elseif "foo" == "foo"
:    echom "vim is case sensitive"
:endif 
```

Vim 执行`elseif`分句,所以显然 Vimscript 是大小写敏感的。有道理，但没什么好震惊的。 现在执行下面命令：

```
:::vim
:set ignorecase
:if "foo" == "FOO"
:    echom "no, it couldn't be"
:elseif "foo" == "foo"
:    echom "this must be the one"
:endif 
```

**啊！** 就在这里停下来。是的，你所见属实。

**`==`的行为取决于用户的设置。**

我发誓我没忽悠你。你再试试看看。我没开玩笑，这不是我干的。

## 防御性编程

这意味着什么？意味着在为别人开发插件时，你*不能*信任`==`。 一个不加包装的`==`*不能*出现在你的插件代码里。

这个建议就像是"`nmap` VS `nnoremap`"一样。*永远不要*猜测你的用户的配置。 Vim 既古老，又博大艰深。在写插件时，你*不得不*假定用户们的配置五花八门，千变万化。

所以怎样才能适应这荒谬的现实？好在 Vim 有额外两种比较操作符来处理这个问题。

执行下面的命令：

```
:::vim
:set noignorecase
:if "foo" ==? "FOO"
:    echom "first"
:elseif "foo" ==? "foo"
:    echom "second"
:endif 
```

Vim 显示`first`因为`==?`是"无论你怎么设都大小写*不敏感*"比较操作符。现在执行下面的命令：

```
:::vim
:set ignorecase
:if "foo" ==# "FOO"
:    echom "one"
:elseif "foo" ==# "foo"
:    echom "two"
:endif 
```

Vim 显示`two`因为`==#`是"无论你怎么设都大小写*敏感*"比较操作符。

故事的最后告诉我们一个道理：你应该*总是*用显式的大小写敏感或不敏感比较。 使用常规的形式是*错的*并且它*终究*会出错。打多一下就能拯救你自己于焦头烂额中。

当你比较整数时，这点小不同不会有什么影响。 不过，我还是建议每一次都使用大小写敏感的比较(即使不一定需要这么做)，好过该用的时候*忘记*用了。

在比较整数时使用`==#`或`==?`都可以，而且将来一旦你改成字符串间的比较，它还会正确工作。 如果你真想用`==`比较整数也不是不行，不过要铭记，一旦被改成字符串间的比较,你需要修改比较操作符。

## 练习

尝试`:set ignorecase`和`:set noignorecase`，看看在不同状态下比较的表现。

阅读`:help ignorecase`来看看为什么有的人设置了这个选项。

阅读`:help expr4`看看所有允许的比较操作符。