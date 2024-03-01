# Abbreviations

# Abbreviations

Vim 有个称为"abbreviations"的特性，与映射有点类似，但是它用于 insert、replace 和 command 模式。这个特性灵活且强大，不过本节只会谈及最常用的用法。

本书只会讲述 insert 模式下的 abbreviations。运行如下命令：

```
:::vim
:iabbrev adn and 
```

进入 insert 模式并输入：

```
:::text
One adn two. 
```

在输入`adn`之后输入空格键，Vim 会将其替换为`and`。

诸如这样的输入纠错是 abbreviations 的一个很实用的用法。运行命令：

```
:::vim
:iabbrev waht what
:iabbrev tehn then 
```

再次进入 insert 模式并输入：

```
:::text
Well, I don't know waht we should do tehn. 
```

注意 *两个* abbreviations 的替换时机，第二个没有输入空格却也替换了。

## Keyword Characters

紧跟一个 abbreviation 输入"non-keyword character"后 Vim 会替换那个 abbreviation。 "non-keyword character"指那些不在`iskeyword`选项中的字符。运行命令：

```
:::vim
:set iskeyword? 
```

你将看到类似于`iskeyword=@,48-57,_,192-255`的结果。这个格式很复杂，但本质上 "keyword characters"包含一下几种：

*   下划线字符 (`_`).
*   所有字母字符，包括大小写。
*   ASCII 值在 48 到 57 之间的字符（数字 0-9）。
*   ASCII 值在 192 到 255 之间的字符（一些特殊 ASCII 字符）。

如果你想阅读这个选项格式的 *完整* 描述，你可以运行命令`:help isfname`，另外 阅读之前最好准备点吃的。

你只要记住输入非字母、数字、下划线的字符就会引发 abbreviations 替换。

## 更多关于 abbreviations

Abbreviations 不仅仅只能纠错笔误。我们可以加几个日常编辑中常用的 abbreviations。 运行如下命令：

```
:::vim
:iabbrev @@    steve@stevelosh.com
:iabbrev ccopy Copyright 2013 Steve Losh, all rights reserved. 
```

随意更换我的名字和邮箱地址为你的，然后试试这两个 abbreviations 吧~

这些 abbreviations 将你常用的一长串字符压缩至几个字符，省的每次都要那么麻烦。

Why Not Use Mappings?

## 为什么不用 Mappings?

不错，abbreviations 和 mappings 很像，但是他们的定位不同。看个例子：

运行命令：

```
:::vim
:inoremap ssig -- <cr>Steve Losh<cr>steve@stevelosh.com 
```

这个 *mapping* 用于快速插入你的签名。进入 insert 模式并输入`ssig`试试看。

看起来一切正常，但是还有个问题。进入 insert 模式并输入如下文字：

```
:::text
Larry Lessig wrote the book "Remix". 
```

注意到 Vim 将 Larry 名字中的`ssig`也替换了！mappings 不管被映射字符串的前后字符是什么-- 它只在文本中查找指定的字符串并替换他们。

运行下面的命令删除上面的 mappings 并用一个 abbreviation 替换它：

```
:::vim
:iunmap ssig
:iabbrev ssig -- <cr>Steve Losh<cr>steve@stevelosh.com 
```

再次试试这个 abbreviation。

这次 Vim 会注意`ssig`的前后字符，只会在需要的时候替换它。

## Exercises

在你的`~/.vimrc`文件中为经常拼写错误的单词增加 abbreviations 配置。一定要使用 上一章中你创建的 mappings 来重新打开读取`~/.vimrc`文件。

为你的邮箱地址、博客网址、签名添加 abbreviations 配置。

为你经常输入的文本添加 abbreviations 配置。