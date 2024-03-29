# 路径

# 路径

Vim 是一个文本编辑器，而文本编辑器(经常)处理文本文件。文本文件储存在文件系统中， 而我们使用路径来描述文件。Vimscript 有一些内置的方法会在你需要处理路径时帮上大忙。

## 绝对路径

有时外部脚本也需要获取特定文件的绝对路径名。执行下面的命令：

```
:::vim
:echom expand('%')
:echom expand('%:p')
:echom fnamemodify('foo.txt', ':p') 
```

第一个命令显示我们正在编辑的文件的相对路径。`%`表示"当前文件"。 Vim 也支持其他一些字符串作为`expand()`的参数。

第二个命令显示当前文件的完整的绝对路径名。字符串中的`:p`告诉 Vim 你需要绝对路径。 这里也有许多别的修饰符可以用到。

第三个命令显示了当前文件夹下的文件`foo.txt`的绝对路径，无论文件是否存在。(译注：试一下看看文件不存在的情况？) `fnamemodify()`是一个比`expand()`灵活多了的 Vim 函数， 你可以指定任意文件名作为`fnamemodify()`的参数，而不仅仅是`expand()`所需要的那种特殊字符串。

## 列出文件

你可能想要得到一个特定文件夹下的文件列表。执行下面的命令：

```
:::vim
:echo globpath('.', '*') 
```

Vim 将输出当前目录下所有的文件和文件夹。`globpath()`函数返回一个字符串， 其中每一项都用换行符隔开。为了得到一个列表，你需要自己去`split()`。执行这个命令：

```
:::vim
:echo split(globpath('.', '*'), '\n') 
```

这次 Vim 显示一个包括各个文件路径的 Vimscript 列表。 如果你的文件名里包括了换行符，那就只能由你自己想办法了。

`globpath()`的通配符(wildcards)的工作方式就像你所想的一样。执行下面的命令：

```
:::vim
:echo split(globpath('.', '*.txt'), '\n') 
```

Vim 显示一个当前文件夹下的所有`.txt`文件组成的列表。

你可以用`**`递归地列出文件。执行这个命令：

```
:::vim
:echo split(globpath('.', '**'), '\n') 
```

Vim 将列出当前文件夹下的所有文件及文件夹。

`globpath()`*非常地*强大。在你完成本章练习后，你将学到更多内容。

## 练习

阅读`:help expand()`.

阅读`:help fnamemodify()`.

阅读`:help filename-modifiers`.

阅读`:help simplify()`.

阅读`:help resolve()`.

阅读`:help globpath()`.

阅读`:help wildcards`.