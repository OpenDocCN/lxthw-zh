# 自动加载

# 自动加载

我们已经为我们的 Potion 插件写了大量的功能，覆盖了本书所要讲的内容。 在结束之前，我们将讲到一些非常重要的方法，可以给我们的插件锦上添花。

第一项是使用自动加载让我们的插件更有效率。

## 如何自动加载

目前，当用户加载我们的插件时(比如打开了一个 Potion 文件)，所有的功能都会被加载。 我们的插件还很小，所以这大概不是什么大问题，但对于较大的插件，加载全部代码将会导致可被察觉的卡顿。

Vim 使用称为"自动加载(autoload)"来解决这个问题。自动加载让你直到需要时才加载某一部分代码。 会有一些性能上的损失，但如果用户不总是需要你的插件的每一行代码，自动加载将带来速度上的飞跃。

示范一下它是怎么工作的。看看下面的命令：

```
:::vim
:call somefile#Hello() 
```

当你执行这个命令，Vim 的行为与平常的函数调用有些许不同。

如果这个函数已经加载了，Vim 简单地像平常一样调用它。

否则 Vim 将在你的`~/.vim`(或`～/.vim/bundles/对应的插件/autoload`)下查找一个叫做`autoload/somefile.vim`的文件。

如果文件存在，Vim 将加载/source 文件。接着 Vim 就会像平常一样调用它。

在这个文件内，函数应该这样定义：

```
:::vim
function somefile#Hello()
    " ...
endfunction 
```

你可以在函数名中使用多个`#`来表示子目录。举个例子：

```
:::vim
:call myplugin#somefile#Hello() 
```

这将在`autoload/myplugin/somefile.vim`查找自动加载文件。 里面的函数需要使用自动加载的绝对路径进行定义：

```
:::vim
function myplugin#somefile#Hello()
    " ...
endfunction 
```

## 实验一下

为了更好地理解自动加载，让我们实验一下。 创建一个`~/.vim/autoload/example.vim`文件并加入下面的内容：

```
:::vim
echom "Loading..."

function! example#Hello()
    echom "Hello, world!"
endfunction

echom "Done loading." 
```

保存文件并执行`:call example#Hello()`。Vim 将输出下面内容：

```
:::text
Loading...
Done loading.
Hello, world! 
```

这个小演示证明了几件事：

1.  Vim 的确是在半途加载了`example.vim`文件。当我们打开 Vim 的时候它并不存在，所以不可能是在启动时加载的。
2.  当 Vim 找到它需要自动加载的文件后，它在调用对应函数之前就加载了整个文件。

**先不要关闭 Vim**，修改函数的定义成这样：

```
:::vim
echom "Loading..."

function! example#Hello()
    echom "Hello AGAIN, world!"
endfunction

echom "Done loading." 
```

保存文件并**不要关闭 Vim**，执行`:call example#Hello()`。Vim 将简单地输出：

```
:::text
Hello, world! 
```

Vim 已经有了`example#Hello`的一个定义，所以它不再需要重新加载文件，这意味着：

1.  函数以外的代码将不再执行。
2.  它不会反映函数本身的变化。

现在执行`:call example#BadFunction()`。你将再一次看到加载信息，伴随着一个函数不存在的错误。 但现在尝试再次执行`:call example#Hello()`。这次你将看到更新后的信息！

目前为止你应该清晰地了解到 Vim 会怎么处理一个自动加载类型的函数调用吧：

1.  它首先是否已经存在同名的函数了。如果是，就调用它。
2.  否则，查找名字对应的文件，并 source 它。
3.  然后试图调用那个函数。如果成功，太棒了。如果失败，就输出一个错误。

如果你还是没有完成弄懂，回到前面重新过一遍演示，注意观察每条规则生效的地方。

## 自动加载什么

自动加载不是没有缺陷的。 设置了自动加载后，会有一些(小的)运行开销，更别说你不得不在你的代码里容忍丑陋的函数名了。

正因为如此，如果你不是写一个用户会在*每次*打开 Vim 对话时都用到的插件，最好尽量把功能代码都挪到 autoload 文件中去。 这将减少你的插件在用户启动 Vim 时的影响，尤其是在人们安装了越来越多的插件的今天。

所以有什么是可以安全地自动加载？那些不由你的用户直接调用的部分。 映射和自定义命令不能自动加载(因为它们需要由用户调用)，但别的许多东西都可以。

让我们看看 Potion 插件里有什么可以自动加载的。

## 在 Potion 插件里添加自动加载

我们将从编译和执行功能开始下手。 在前一章的最后，我们的`ftplugin/potion/running.vim`文件大概是这样：

```
:::vim
if !exists("g:potion_command")
    let g:potion_command = "/Users/sjl/src/potion/potion"
endif

function! PotionCompileAndRunFile()
    silent !clear
    execute "!" . g:potion_command . " " . bufname("%")
endfunction

function! PotionShowBytecode()
    " Get the bytecode.
    let bytecode = system(g:potion_command . " -c -V " . bufname("%"))

    " Open a new split and set it up.
    vsplit __Potion_Bytecode__
    normal! ggdG
    setlocal filetype=potionbytecode
    setlocal buftype=nofile

    " Insert the bytecode.
    call append(0, split(bytecode, '\v\n'))
endfunction

nnoremap <buffer> <localleader>r :call PotionCompileAndRunFile()<cr>
nnoremap <buffer> <localleader>b :call PotionShowBytecode()<cr> 
```

这个文件仅仅当 Potion 文件加载时才会调用，所以它通常不会影响 Vim 的启动时间。 但可能会有一些用户就是不想要这些功能，所以如果我们可以自动加载某些部分， 每次打开 Potion 文件时可以省下他们以毫秒记的时间。

是的，这种情况下我们不会节省多少。 但你可以想象到可能有那么一个插件包括了数千行可以通过自动加载来减少每次的加载时间的代码。

让我们开始吧。在你的插件 repo 中创建一个`autoload/potion/running.vim`文件。 然后移动两个函数进去，并修改它们的名字，让它们看上去像：

```
:::vim
echom "Autoloading..."

function! potion#running#PotionCompileAndRunFile()
    silent !clear
    execute "!" . g:potion_command . " " . bufname("%")
endfunction

function! potion#running#PotionShowBytecode()
    " Get the bytecode.
    let bytecode = system(g:potion_command . " -c -V " . bufname("%"))

    " Open a new split and set it up.
    vsplit __Potion_Bytecode__
    normal! ggdG
    setlocal filetype=potionbytecode
    setlocal buftype=nofile

    " Insert the bytecode.
    call append(0, split(bytecode, '\v\n'))
endfunction 
```

注意`potion#running`部分的函数名怎么匹配它们所在的路径。 现在修改`ftplugin/potion/running.vim`文件成这样：

```
:::vim
if !exists("g:potion_command")
    let g:potion_command = "/Users/sjl/src/potion/potion"
endif

nnoremap <buffer> <localleader>r
            \ :call potion#running#PotionCompileAndRunFile()<cr>

nnoremap <buffer> <localleader>b
            \ :call potion#running#PotionShowBytecode()<cr> 
```

保存文件，关闭 Vim，然后打开你的`factorial.pn`文件。尝试这些映射，确保它们依然正常工作。

确保你仅仅在第一次执行其中一个映射的时候才看到诊断信息`Autoloading...`(你可能需要使用`:message`来看到)。 一旦认为自动加载正常工作，你可以移除那些信息。

正如你看到的，我们保留`nnoremap`映射部分不变。 我们不能自动加载它们，不然用户就没办法引发自动加载了！

你将在 Vim 插件中普遍看到：大多数的功能将位于自动加载函数中，仅有`nnoremap`和`command`命令每次都被 Vim 加载。 每次你写一个有用的 Vim 插件时，不要忘了这一点。

## 练习

阅读`:help autoload`

稍微测试一下并弄懂自动加载变量是怎么一回事。

假设你想要强制加载一个 Vim 已经加载的自动加载文件，并不会惊扰到用户。 你会怎么做？你可能想要阅读`:help silent!`(译注：此处应该是`:help :silent`)。不过在现实生活中请不要那么做。