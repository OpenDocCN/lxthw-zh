# 设置选项

# 设置选项

Vim 拥有很多选项可以设置以改变其展现方式。

主要有两种选项：布尔选项（值为"on"或"off"）和键值选项。

## 布尔选项

执行如下命令：

```
:::vim
:set number 
```

如果之前屏幕左侧没有显示行号，那么现在你就会看见行号。执行命令：

```
:::vim
:set nonumber 
```

行号应该消失。`number`是一个布尔选项：可以 off、可以 on。通过`:set number`命令打开、 `:set nonumber`命令关闭。

所有的布尔选项都是这种配置方法。`:set <name>`打开选项、`:set no<name>`关闭选项。

## 切换布尔选项

你可以"切换"布尔选项的值，即从开启切为关闭或从关闭切为开启。执行命令：

```
:::vim
:set number! 
```

行号会再次显示出来。再次执行命令：

```
:::vim
:set number! 
```

行号应该会再次消失。添加一个`!`（感叹号）至布尔选项后面就会切换对于选项的值。

## 查看选项当前值

你可以使用一个`?`符号向 Vim 获取一个选项的当前值。执行如下命令并查看每个命令的 返回结果：

```
:::vim
:set number
:set number?
:set nonumber
:set number? 
```

注意第一次`:set number?`命令返回的是`number`而第二次返回的是`nonumber`。

## 键值选项

有些选项并不只有 off 或 on 两种状态，它们需要一个值。执行如下命令，查看返回结果：

```
:::vim
:set number
:set numberwidth=10
:set numberwidth=4
:set numberwidth? 
```

`numberwidth`选项改变行号的列宽。你可以通过`:set <name>=<value>`命令改变 非布尔选项的选项值，并使用`:set <name>?`命令查看选项的当前值。

来看看一些常用选项的值：

```
:::vim
:set wrap?
:set shiftround?
:set matchtime? 
```

## 一次性设置多个选项

最后，你可以在一个`:set`命令中设置多个选项的值。试试如下命令：

```
:::vim
:set numberwidth=2
:set nonumber
:set number numberwidth=6 
```

注意最后一个命令是如何一次性设置两个选项值的。

## 练习

阅读`:help 'number'`（注意有单引号）帮助文档。

阅读`:help relativenumber`帮助文档。

阅读`:help numberwidth`帮助文档。

阅读`:help wrap`帮助文档。

阅读`:help shiftround`帮助文档。

阅读`:help matchtime`帮助文档。

按你自己的喜好在你的`~/.vimrc`文件中添加几个设置选项。