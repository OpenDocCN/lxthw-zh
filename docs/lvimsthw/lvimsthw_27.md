# 函数参数

# 函数参数

毫无疑问，Vimscript 函数可以接受参数。执行下面的命令：

```
:::vim
:function DisplayName(name)
:  echom "Hello!  My name is:"
:  echom a:name
:endfunction 
```

执行下面的函数：

```
:::vim
:call DisplayName("Your Name") 
```

Vim 将显示两行：`Hello! My name is:` 和 `Your Name`。

注意我们传递给`echom`命令的参数前面的`a:`。这表示一个变量的作用域，在前几章(译注：第二十章)我们曾讲过。

让我们试一下不带作用域前缀会怎么样。执行下面的命令：

```
:::vim
:function UnscopedDisplayName(name)
:  echom "Hello!  My name is:"
:  echom name
:endfunction
:call UnscopedDisplayName("Your Name") 
```

这次 Vim 抱怨说它找不到变量`name`。

在写需要参数的 Vimscript 函数的时候，你*总需要*给参数加上前缀`a:`，来告诉 Vim 去参数作用域查找。

## 可变参数

Vimscript 函数可以设计为接受不定数目的参数，就像 Javascript 和 Python 中的一样。执行下面命令：

```
:::vim
:function Varg(...)
:  echom a:0
:  echom a:1
:  echo a:000
:endfunction

:call Varg("a", "b") 
```

这个函数向我们展示了许多东西，让我们来逐一审视。

函数定义中的`...`说明这个函数可以接受任意数目的参数。就像 Python 函数中的`*args`

函数中的第一行为输出消息`a:0`，结果显示`2`。当你在 Vim 中定义了一个接受可变参数的函数， `a:0`将被设置为你额外给的参数数量(译注：注意是额外的参数数量)。 刚才我们传递了两个参数给`Varg`，所以 Vim 显示`2`。(译注：2 - 0 ==# 2)

第二行为输出`a:1`，结果显示`a`。你可以使用`a:1`,`a:2`等等来引用你的函数接受的每一个额外参数。 如果我们用的是`a:2`，Vim 就会显示"b"

第三行有些费解。当一个函数可以接受可变参数，`a:000`将被设置为一个包括所有传递过来的额外参数的列表(list)。 我们还没有讲过列表，所以不要太纠结于此。你不能对列表使用`echom`，因而在这里用`echo`代替。

你也可以将可变参数和普通参数一起用。执行下面的命令：

```
:::vim
:function Varg2(foo, ...)
:  echom a:foo
:  echom a:0
:  echom a:1
:  echo a:000
:endfunction

:call Varg2("a", "b", "c") 
```

我们可以看到 Vim 将`"a"`作为具名参数(named argument)`a:foo`的值，将余下的塞进可变参数列表中。

## 赋值

试试执行下面的命令：

```
:::vim
:function Assign(foo)
:  let a:foo = "Nope"
:  echom a:foo
:endfunction

:call Assign("test") 
```

Vim 将抛出一个错误，因为你不能对参数变量重新赋值。现在执行下面的命令：

```
:::vim
:function AssignGood(foo)
:  let foo_tmp = a:foo
:  let foo_tmp = "Yep"
:  echom foo_tmp
:endfunction

:call AssignGood("test") 
```

这次就可以了，Vim 显示`Yep`。

## 练习

阅读`:help function-argument`的前两段。

阅读`:help local-variables`。