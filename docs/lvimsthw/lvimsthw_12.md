# 更多的 Mappings

# 更多的 Mappings

迄今为止我们已经说了很多 mappings 的内容，但现在我们要再次实践一下。mappings 是 使得 Vim 编辑更为高效的方便快捷途径之一，有必要多加用心。

有个概念在多个例子中出现过，但是我们都没有明确解释，那就是多字符 mappings 的连续性。

运行如下命令：

```
:::vim
:nnoremap jk dd 
```

确保你出于 normal 模式，快速输入`jk`。Vim 会删除当前行。

现在试试先输入`j`，停顿一下。如果你输入`j`后没有快速输入`k`，Vim 就会判定你不想 生效那个映射，而是将`j`按默认操作运行（下移一行）。

这个映射会给光标移动操作带来麻烦，我们先删除它。运行下面的命令：

```
:::vim
:nunmap jk 
```

现在 normal 模式下快速输入`jk`会像往常一样下移一行然后又上移一行。

## 一个更为复杂的 Mapping

你已经见过很多简单的 mappings 了，是时候看看一些复杂的了。运行下面的命令：

```
:::vim
:nnoremap <leader>" viw<esc>a"<esc>hbi"<esc>lel 
```

那是一个有趣的 mappings！你自己可以先试试。进入 normal 模式，移动光标至一个单词， 输入`<leader>"`。Vim 将那个单词用双引号包围！

它是如何工作的呢？我们拆分这个映射并逐个解释：

```
:::text
viw<esc>a"<esc>hbi"<esc>lel 
```

*   `viw`: 高亮选中单词
*   `<esc>`: 退出 visual 模式，此时光标会在单词的最后一个字符上
*   `a`: 移动光标至当前位置之 *后* 并进入 insert 模式
*   `"`: 插入一个`"`
*   `<esc>`: 返回到 normal 模式
*   `h`: 左移一个字符
*   `b`: 移动光标至单词头部
*   `i`: 移动光标至当前位置之 *前* 并进入 insert 模式
*   `"`: 插入一个`"`
*   `<esc>`: 返回到 normal 模式
*   `l`: 右移一个字符，光标置于单词的头部
*   `e`: 移动光标至单词尾部
*   `l`: 右移一个字符，置光标位置在第一个添加的引号上

记住：因为我们使用的是`nnoremap`而不是`nmap`，所以尽管你映射了字符序列中的字符 也不会有影响。Vim 会将其中的字符按默认功能执行。

希望你能看出 Vim mappings 的潜能及随之引发的阅读困难。

## Exercises

像刚才一样创建一个 mapping，用单引号而不是双引号。

试试用`vnoremap`添加一个 mapping，使其能够用引号将你 *高亮选中* 的文本包裹。 你可能会需要``<`和``>`命令，所以先执行`:help `<`看看帮助文档。

将 normal 模式下的`H`映射为移动到当前行的首部。`h`是左移，所以你可以认为`H`是 “加强版”的`h`、

将 normal 模式下的`L`映射为移动到当前行的尾部。`l`是右移，所以你可以认为`L`是 “加强版”的`l`、

读取帮助文档`:help H`和`:help L`看看你覆盖了哪些命令。考虑考虑这会不会影响你。

将这些 mappings 添加到你的`~/.vimrc`文件中，确保用你的“编辑`~/.vimrc`”和“重读`~/.vimrc`” 映射操作~