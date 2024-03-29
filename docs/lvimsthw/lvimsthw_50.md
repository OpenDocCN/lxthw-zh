# 更高级的语法高亮

# 更高级的语法高亮

我们甚至可以为 Vim 里面的语法高亮另开一本书了。

我们将在此讲解它最后的重要内容，然后继续讲别的东西。 如果你想要学到更多，去读`:help syntax`并阅读别人写的 syntax 文件。

## 高亮字符串

Potion，一如大多数编程语言，支持诸如`"Hello,world!"`的字符串字面量。 我们应该把这些高亮成字符串。为此我们将使用`syntax region`命令。 在你的 Potion syntax 文件中加入下面内容：

```
:::vim
syntax region potionString start=/\v"/ skip=/\v\\./ end=/\v"/
highlight link potionString String 
```

关闭并重新打开你的`factorial.pn`，你将看到文件结尾的字符串被高亮了！

最后一行应该很熟了。如果你不懂，重读前两章。

第一行用一个"region"添加一个语法类型分组。 区域(Regions)有一个"start"模式和一个"end"模式来指定开头和结束的位置。 这里，一个 Potion 字符串从一个双引号开始，到另一个双引号结束。

`syntax region`的"skip"参数允许我们处理转义字符串，比如 `"She said: \"Vimscript is tricky, but useful\"!"`。

如果不提供`skip`参数，Vim 将在`Vimscript`之前的`"`停止匹配字符串，这不是我们想要的！

简明扼要地说，`syntax region`中的`skip`参数告诉 Vim： "一旦你开始匹配这个区域，我希望你忽略`skip`匹配的内容，即使它会被当作区域结束的标志"。

花上几分钟去想透彻。如果遇到的是`"foo \\" bar"`会怎样？那会是正确的行为吗？ 那*总是*正确的行为吗？放下本书，花上几分钟来认真*想一想*！

## 练习

给单引号字符串加上语法高亮。

阅读`:help syn-region`.

阅读`:help syn-region`将比阅读本章花费更多的时间。给自己倒杯饮料，这是你应得的！