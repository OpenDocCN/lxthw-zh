# 新希望：用 Pathogen 配置插件

# 新希望：用 Pathogen 配置插件

Vim 的插件配置方式，在你仅仅添加一个文件来自定义自己的 Vim 体验时很合理， 但当你想要使用别人写的插件时，这种方式会导致一团糟。

在过去，要想使用别人写好的插件，你得下载所有文件并逐一正确地放置它们。 你也可能使用`zip`或`tar`来替你做放置的工作。

在这个过程中有些明显的问题：

*   当你想更新插件的时候怎么办？你可以覆盖旧的文件， 但如果作者删除了某个文件，你怎么知道你要手工删除对应文件？
*   假如有两个插件正好使用了同样的文件名(比如`utils.vim`或别的更大众的名字)呢？ 有时你可以简单地重命名掉它，但如果它位于`autoload/`或别的名字相关的文件夹中呢？ 你改掉文件名，就等于改掉插件。这一点也不好玩。

人们总结出一系列 hacks 来让事情变得简单些，比如 Vimball。 幸运的是，我们不再需要忍受这些肮脏的 hacks。 [Tim Pope](http://tpo.pe/)创造了著名的[Pathogen](http://www.vim.org/scripts/script.php?script_id=2332)插件让管理大量插件变得轻松愉快， 只要插件作者神志清醒地安排好插件结构。(译注：现在推荐[vundle](https://github.com/gmarik/vundle)来代替 Pathogen，前者支持使用 git 下载插件)

让我们了解一下 Pathogen 的工作方式，以及为了让我们的插件更加兼容，我们需要做的事。

## 运行时路径

当 Vim 在特殊的文件夹，比如`syntax/`，中查找文件时，它不仅仅只到单一的地方上查找。 就像 Linux/Unix/BSD 系统上的`PATH`，Vim 设置`runtimepath`以便查找要加载的文件。

在你的桌面创建`colors`文件夹。在这个文件夹中创建一个叫`mycolor.vim`的文件(在本示例中你可以让它空着)。 打开 Vim 并执行这个命令：

```
:::vim
:color mycolor 
```

Vim 将显示一个错误，因为它不懂得去你的桌面查找。现在执行这个命令：

```
:::vim
:set runtimepath=/Users/sjl/Desktop 
```

当然，你得根据你的情况修改路径名。现在再尝试 color 命令：

```
:::vim
:color mycolor 
```

这次 Vim 找到了`mycolor.vim`，所以它将不再报错。由于文件是空的，它事实上什么都没*做*， 但由于它不再报错，我们确信它找到了。

## Pathogen

Pathogen 插件在你加载 Vim 的时候自动地把路径加到你的`runtimepath`中。 所有在`~/.vim/bundle/`下的文件夹将逐个加入到`runtimepath`。(译注：vundle 也是这么做的)

这意味着每个`bundle/`下的文件夹应该包括部分或全部的标准的 Vim 插件文件夹，比如`colors/`和`syntax/`。 现在 Vim 可以从每个文件夹中加载文件，而且每个插件文件都独立于自己的文件夹中。

这么一来更新插件就轻松多了。你只需要整个移除旧的插件文件夹，并迎来新的版本。 如果你通过版本控制来管理`~/.vim`文件夹(你应该这么做)， 你可以使用 Mercurial 的 subrepo 或 Git 的 submodule 功能来直接签出(checkout)每个插件的代码库， 然后用一个简单的`hg pull; hg update`或`git pull origin master`来更新。

## 成为 Pathogen 兼容的

我们计划让我们的用户通过 Pathogen 安装我们写的 Potion 插件。 我们需要做的：在插件的代码库里，放置我们的文件到正确的文件夹中。就是这么简单！

我们插件的代码库展开后看起来就像这样：

```
:::text
potion/
    README
    LICENSE
    doc/
        potion.txt
    ftdetect/
        potion.vim
    ftplugin/
        potion.vim
    syntax/
        potion.vim
    ... etc ... 
```

我们把它放置在 GitHub 或 Bitbucket 上，这样用户就能简单地 clone 它到`bundle/`，一切顺利！

## 练习

如果你还没有安装[vnudle][]，安装它。(译注：原文是安装[Pathogen](http://www.vim.org/scripts/script.php?script_id=2332)，但是没有必要啦)

给你的插件创建 Mercurial 或 Git 代码库，起名叫`potion`。 你可以把它放到你喜欢的地方，并链接到`~/.vim/bundle/potion/`或就把它直接放到`~/.vim/bindle/potion/`。

在代码库中创建`README`和`LICENSE`文件，然后 commit。

Push 到 Bitbucket 或 GitHub。

阅读`:help runtimepath`。