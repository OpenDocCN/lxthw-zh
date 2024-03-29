# 高级语法高亮

# 高级语法高亮

目前我们已经为 Potion 文件实现了简单的关键字和函数的语法高亮。

如果没有做上一章的练习，你需要回去完成。我将假设你做了练习。

事实上，你应该回去完成你跳过的*任何*练习。即使你觉得你不需要，为了更好的学习效果， 你都得把它们完成了。请在这一点上相信我。

## 高亮注释

接下来我们需要高亮 Potion 的一个重要组成部分——注释。 问题是，Potion 的注释以`#`开头，而`#`并不在`iskeyword`里。

如果不知道什么是`iskeyword`，你没有认真听讲。回去并*完成那该死的练习*。 在写每一章的内容时，我不会把无意义的粗重活丢给你。你*真的*需要完成它们来跟上本书的进度。

因为`#`不是一个 keyword 字符，我们需要使用正则表达式来匹配它(以及接下来的注释)。 我们将用`syntax match`代替`syntax keyword`。在你的 syntax 文件中加入下面几行：

```
:::vim
syntax match potionComment "\v#.*$"
highlight link potionComment Comment 
```

我不会再唠叨要把它们放到文件的哪里。你已经是个程序猿了：由你自己判断。

关闭并重新打开`factorial.pn`。在文件的某处添加一个注释，你将看到它被当作注释高亮了。

第二行是简单的：它告诉 Vim 高亮`potionComment`语法类型组里的任何东西为`Comment`。

第一行有点新东西。我们使用`syntax match`来告诉 Vim 用*正则表达式*而不是关键词来匹配。

注意正则表达式以`\v`开头，表示使用"very magic"模式。 如果你不太清楚，重读关于基本正则表达式的那一章。(译注：第三十一章)

当前状况下，"very magic"模式不是必须的。 但将来我们可能会改变这个正则表达式，然后苦思冥想为何它不工作了， 所以我建议总是使用"very magic"来保证一致性。

至于正则表达式的功能，非常简单：匹配以`#`开头的注释，包括以此开始到行末的所有字符。

如果你需要重新唤起对正则表达式的记忆，你应该看一下 Zed Shaw 的[Learn Regex the Hard Way](http://regex.learncodethehardway.org/)。

## 高亮运算符

另一个需要正则表达式来高亮的部分是运算符。在你的 syntax 文件中加入下列内容：

```
:::vim
syntax match potionOperator "\v\*"
syntax match potionOperator "\v/"
syntax match potionOperator "\v\+"
syntax match potionOperator "\v-"
syntax match potionOperator "\v\?"
syntax match potionOperator "\v\*\="
syntax match potionOperator "\v/\="
syntax match potionOperator "\v\+\="
syntax match potionOperator "\v-\="

highlight link potionOperator Operator 
```

关闭并重新打开`factorial.pn`。注意到阶乘函数的`*=`现在被高亮了。

你可能首先注意到，我把每个正则表达式独立成一行而不是像对关键字一样分成组。 这是因为`syntax match`*不*支持在一行里放多个组。

你应该也注意到每个正则表达式都以`\v`开头，即使并不是必须的。 在写 Vimscript 时，我希望保持正则表达式的一致性，即使这样做需要多打几个符号。

你可能会奇怪，为什么我不用类似于`"\v-\=?"`的正则表达式来同时匹配`-`*以及*`-=`。 你想要的话也可以这么做。它会正常工作。 我只是坚持认为`-`和`-=`是不同的运算符，所以把它们放到不同行里。

把每个运算符放在单独的匹配中，简化了正则表达式，代价是输入了额外的字符。 我喜欢这么做，但你可能不这么认为。你自己决定吧。

我也没有把`=`定义成一个运算符。我们等会会这么做，但我希望暂时先不这样做，这样就能给你考上一题了。

因为分开了`-`和`-=`的正则表达式，我不得不在定义`-`*之后*定义`-=`！

如果以相反的顺序定义，并在 Potion 文件里使用`-=`，Vim 将匹配`-`(当然，同时也高亮它)， 剩下`=`等待匹配。这意味着在构建`syntax match`组时，每个组"消耗"的文本片段在之后不能被匹配到。

这讲得太笼统了，但我暂时并不打算纠结于细节。 总之，你应该在匹配较小的组之后匹配较大的组，因为在*之后*定义的组优先于在*之前*定义的组。

让我们继续并添加`=`作为运算符。现在请听题：

```
:::vim
syntax match potionOperator "\v\=" 
```

花一点时间想想你应该把它放在 syntax 文件的哪个位置。如果你需要提示，重读前几章。

## 练习

阅读`:help syn-match`.

阅读`:help syn-priority`.

在例子中，我们没有把`:`当作运算符。阅读 Potion 文档并审慎地决定是否把`:`当作一个运算符。 如果你决定这么做，把它加到 syntax 文件中。

同样考虑`.`和`/`。

增加一个高亮数字的语法类型分组`potionNumber`。链接它到高亮组`Number`。 不要忘了 Potion 支持`2`，`0xffaf`，`123.23`，`1e-2`和`1.9956e+2`这几种形式。 记得在处理边际状态的花费的时间和这些边际状态出现的次数之间取得平衡。