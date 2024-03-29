# 执行 normal!

# 执行 normal!

既然已经学了`execute`和`normal!`，我们就可以深入探讨一个 Vimscript 惯用法。 执行下面的命令：

```
:::vim
:execute "normal! gg/foo\<cr>dd" 
```

这将移动到文件的开头，查找`foo`的首次出现的地方，并删掉那一行。

之前我们尝试过用`normal!`来执行一个搜索命令却无法输入必须的回车来开始进行搜索。 结合`execute`和`normal!`将解决这个问题。

`execute`允许你创建命令，因而你能够使用 Vim 普通的转义字符串来生成你需要的"打不出"的字符。 尝试下面的命令：

```
:::vim
:execute "normal! mqA;\<esc>`q" 
```

这个命令做了什么？让我们掰开来讲：

*   `:execute "normal! ..."`：执行命令序列，一如它们是在 normal 模式下输入的，忽略所有映射， 并替换转义字符串。
*   `mq`：保存当前位置到标记"q"。
*   `A`：移动到当前行的末尾并在最后一个字符后进入 insert 模式。
*   `;`：我们现在位于 insert 模式，所以仅仅是写入了一个";"。
*   `\<esc>`：这是一个表示 Esc 键的转义字符串序列，把我们带离 insert 模式。
*   ``q`：回到标记"q"所在的位置。

看上去有点绕，不过它真的很有用：它在当前行的末尾补上一个分号并保持光标不动。 在写 Javascript，C 或其他以分号作为语句分隔符的语言时，一旦忘记加上分号，这样的映射将助你一臂之力。

## 练习

重读`:help expr-quote`(你之前应该看过)来提醒你怎么用`execute`通过转义字符串传递特殊字符给`normal!`。

在翻开下一章之前，放下本书休息一下。吃一个三明治或喝一杯咖啡(译注：或者茶！)， 喂一下你的宠物——如果你有的话。