# 检测文件类型

# 检测文件类型

让我们创建一个 Potion 文件作为插件的测试样本。

```
:::text
factorial = (n):
    total = 1
    n to 1 (i):
        total *= i.
    total.

10 times (i):
    i string print
    '! is: ' print
    factorial (i) string print
    "\n" print. 
```

这个代码创建了一个简单的阶乘函数并调用它 10 次，逐次输出结果。继续前进并用`potion factorial.pn`执行它。 输出结果应该像这样：

```
:::text
0! is: 0
1! is: 1
2! is: 2
3! is: 6
4! is: 24
5! is: 120
6! is: 720
7! is: 5040
8! is: 40320
9! is: 362880 
```

如果你得不到这个输出，或者你得到一个错误，停下来并排查问题所在。 这个代码应该会正常工作的。

这跟学习 Vimscript 没有关系，不过它能让你成为更好的程序猿。

## 检测 Potion 文件

用 Vim 打开`factorial.pn`并执行下面命令：

```
:::vim
:set filetype? 
```

Vim 将显示`filetype=`，因为它还不认识`.pn`文件。让我们解决这个问题。

在你的插件的 repo 中创建`ftdetect/potion.vim`。在它里面加入下面几行：

```
:::vim
au BufNewFile,BufRead *.pn set filetype=potion 
```

这创建了一个单行自动命令：一个设置`.pn`文件的 filetype 为`potion`的命令。很简明吧。

注意我们*没有*像之前经常做的那样使用一个自动命令组。 Vim 自动替你把`ftdetect/*.vim`文件包装成自动命令组，所以你不需要操心。

关闭`factorial.pn`并重新打开它。现在再执行前面的命令：

```
:::vim
:set filetype? 
```

这次 Vim 显示`filetype=potion`。当 Vim 启动时，它加载`~/.vim/bundle/potion/ftdetect/potion.vim`里的自动命令组， 而当它打开`factorial.pn`时，自动命令起效，设置`filetype`为`potion`。

既然已经让 Vim 识别了 Potion 文件，我们可以继续前进来做些有用的东西了。

## 练习

阅读`:help ft`。不要担心你看不懂里面的内容。

阅读`:help setfiletype`。

修改 Potion 插件中的`ftdetect/potion.vim`。 用`setfiletype`代替`set filetype`。