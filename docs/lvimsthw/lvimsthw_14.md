# 本地缓冲区的选项设置和映射

# 本地缓冲区的选项设置和映射

现在我们先花点时间复习一下我们已经谈论过的三个东西：映射（mappings），缩写（abbreviations）和选项设置（options），这个过程中会讲到一些新的东西。我们将在一个单一的缓冲区中同时设置它们。

这一章所讲到的东西会在下一章中真正的显示它们的作用，目前我们只需先打下基础。

在这一章中你需要在 Vim 中打开两个文件，两个文件是分开的。我先将它们命名为`foo`和`bar`，你可以随便对它们命名。然后为每个文件输入一些文字。

## 映射

选择文件`foo`，然后执行下面的命令：

```
:::vim
:nnoremap          <leader>d dd
:nnoremap <buffer> <leader>x dd 
```

现在保持在文件`foo`下面，确保当前处于常用模式下，然后敲击`<leader>d`。Vim 会删除一行。这个之前讲到过，没什么新鲜的。

仍然保持在文件`foo`下面，敲击`<leader>x`。Vim 也会删除一行。这很正常，因为我们也将`<leader>x`映射到`dd`了。

现在切换到文件`bar`。在常用模式下敲击`<leader>d`。同样的，Vim 会删除当前行，也没有什么新鲜的。

ok，现在来点新鲜的：在文件`bar`下敲击`<leader>x`。

Vim 只删除了一个字符，而不是删除整个行！ 为什么会这样？

第二个`nnoremap`命令中的`<buffer>`告诉 Vim 这个映射只在定义它的那个缓冲区中有效：

当你在`bar`文件下敲击`<leader>x`，Vim 找不到一个跟它匹配的映射，它将会被解析了两个命令：`<leader>`（这个什么都不会干）和 `x`（通常会删除一个字符）。

## 本地 Leader

在这个例子中，`<leader>x`是一个本地缓冲区映射，不过这种定义方式并不合适。如果我们需要设定一个只会用于特定缓冲区的映射，一般会使用`<localleader>`，而不是`<leader>`。

使用两种不同的 leader 按键就像设置了一种命名空间，这会帮助你保证所有不同的映射对你而言更加清晰直接。

但你在编写一个会被其他人用到的插件的时候，这点显得尤其重要。使用`<localleader>`来设置本地映射会防止你的插件覆盖别人用`<leader>`设置的全局映射，因为他们可能已经对他们做设置的全局映射非常之习惯了。

## 设置

在这本书的前面几个章节里，我们谈论了使用`set`来设置选项。有一些选项总是会适用于整个 Vim，但是有些选项可以基于缓冲区进行设置。

切回到文件`foo`，执行下面的命令：

```
:::vim
:setlocal wrap 
```

然后切换到文件`bar`，执行下面的命令：

```
:::vim
:setlocal nowrap 
```

把你的 Vim 窗口调小一些，你会发现有些行在`foo`中会自动换行，而在`bar`中则不会。

让我们来测试下另外一个选项。切换到`foo`执行下面的命令：

```
:::vim
:setlocal number 
```

现在切换到`bar`，然后执行下面的命令：

```
:::vim
:setlocal nonumber 
```

现在在文件`foo`中会出现行号，而在`bar`则没有。

不是所有的选项都可以使用`setlocal`进行设置。如果你想知道某个特定的选项是否可以设置为本地选项，执行`:help`查看它的帮助文档。

对于本地选项如何*真正地*地工作，我说的有些简略。在练习中你会学到更多这方面的细节。

## 遮盖

ok，在开始下一节之前，我们先来看关于本地映射的一个非常有趣的特性。切换到文件`foo`，然后执行下面的命令：

```
:::vim
:nnoremap <buffer> Q x
:nnoremap          Q dd 
```

然后敲击`Q`，看看会发生什么？

当你敲击`Q`，Vim 会执行第一个映射，而不是第二个，因为第一个映射比起第二个要显得*更具体*，这可以看成第二个映射被第一个映射遮盖了。

切换回文件`bar`，然后敲击`Q`，Vim 会使用第二个映射。这是因为在这个缓冲区中第二个映射没有被第一个映射遮盖。

## 练习

阅读`:help local-options`。

阅读`:help setlocal`。

阅读`:help map-local`。