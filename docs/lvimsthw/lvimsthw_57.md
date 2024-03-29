# 文档

# 文档

我们的 Potion 插件有着许多有用的功能，但是无人知晓这一点，除非我们留下了文档！

Vim 自身的文档非常棒。它不仅是详细地，而且也是非常透彻的。 同时，它也启发了许多插件作者写出很好的插件文档，结果是在 Vimscript 社区里营造出强大的文档文化。

## 如何使用文档

当你阅读 Vim 里的`:help`条目时，你显然注意到了有些内容被高亮得跟别的不一样。 让我们看一下这是怎么回事。

打开任何帮助条目(比如`:help help`)并执行`:set filetype?`。Vim 显示`filetype=help`。 现在执行`:set filetype=text`，你将看到高亮消失了。 再次执行`:set filetype=help`，高亮又回来了。

这表明 Vim 帮助文件只是获得了语法高亮的文本文件，一如其他的文件格式！ 这意味着你可以照着写并获得同样的高亮。

在你的插件 repo 中创建名为`doc/potion.txt`文件。 Vim/Pathogen 在索引帮助条目时查找在`doc`文件夹下的文件，所以我们在此写下插件的帮助文档。

用 Vim 打开这个文件并执行`:set filetype=help`，这样你在输入的时候就可以看到语法高亮。

## 帮助的题头

帮助文件的格式是一个取决于个人品味的问题。 尽管这么说，我还是讲讲一种在当前的 Vimscript 社区逐渐被广泛使用的文档格式。

文件的第一行应该包括帮助文件的文件名，接下来是一行对插件功能的描述。 在你的`potion.txt`文件的第一行加上下面的内容：

```
:::text
*potion.txt* functionality for the potion programming language 
```

在帮助文件中用星号括起一个词创建了一个可以用于跳转的"tag"。 执行`:Helptags`来让 Pathogen 重新索引帮助 tags，接着打开一个新的 Vim 窗口并执行`:help potion.txt`。 Vim 将打开你的帮助文档，一如往日打开别人写的。

接下来你应该把你的插件的大名和一个老长老长的描述打上去。 有些作者(包括我)喜欢在这上面花点心思，用一些 ASCII 艺术字点缀一下。 在`potion.txt`文件内加上一个不错的标题节：

```
:::text
*potion.txt* functionality for the potion programming language

                      ___      _   _              ~
                     / _ \___ | |_(_) ___  _ __   ~
                    / /_)/ _ \| __| |/ _ \| '_ \  ~
                   / ___/ (_) | |_| | (_) | | | | ~
                   \/    \___/ \__|_|\___/|_| |_| ~

          Functionality for the Potion programming language.
        Includes syntax highlighting, code folding, and more! 
```

我是通过执行`figlet -f ogre "Potion"`命令来得到这些有趣的字符的。 [Figlet](http://www.figlet.org/)是一个好玩的小程序，可以生成 ACSII 艺术字。 每一行结尾的`~`字符保证 Vim 不会尝试高亮或隐藏艺术字中的某些字符。

## 写什么文档

接下来通常是一个内容目录。不过，首先，让我们决定我们想要写的文档内容。

在给一个新插件写文档时，我通常从下面的列表开始：

*   Introduction
*   Usage
*   Mappings
*   Configuration
*   License
*   Bugs
*   Contributing
*   Changelog
*   Credits

如果这是一个大插件，需要一个"大纲"，我将写一个介绍段落来概括它的主要功能。 否则我会跳过它继续下一段。

一个"usage"段落应该解释，大体上用户将怎样*使用*你的插件。如果他们需要通过映射进行交互，告诉他们。 如果映射数目不是很多，你可以简单地在这里列出来，否则你可能需要创建一个单独的"mappings"段落来一一列出。

"configuration"段落应该详尽列出用户可以自定义的变量，以及它们的功能和默认值。

"license"段落应该指出插件代码所用的协议，连同一个指向协议完整文本的 URL。 不要把整份协议放入帮助文件 -- 大多数用户知道这些常用的协议是什么意思，这样做只会徒增混乱。

"bugs"段落应该尽可能短小。列出所有你已知却尚未解决的主要的 bugs，并告知用户如何向你报告他们抓到的新 bug。

如果你希望你的用户可以向项目奉献 bug fixes 和 features，他们需要怎么做。 应该把 pull request 发到 GitHub 呢？还是 Bitbucket?要用 email 寄补丁吗？ 要选择其中的一个还是全都得要？一个"contributing"段落可以清楚地表明你想要接受代码的方式。

一个 changlog 也是值得包含在内的，这样当用户从版本 X 更新到版本 Y 时，他们立即可以看到什么改变了。 此外，我强烈推荐你为你的插件使用一个合理的版本号计划，比如[Semantic Versioning](http://semver.org/)，并一直坚持。 你的用户会感谢你的。

最后，我喜欢加入一个"credits"段落来留下自己的大名，列出影响该插件创作的其他插件，感谢奉献者，等等。

这样我们就有一个成功的开始了。对于许多特殊的插件，你可能觉得需要不这么做，那也没问题。 你仅需追随下面几条规则：

*   透彻明了
*   不要废话
*   带领你的用户漫步于你的插件，从一无所知到了如指掌。

## 内容目录

既然我们已经了解了应该要有的段落，把下面内容加入到`potion.txt`文件中：

```
:::text
====================================================================
CONTENTS                                            *PotionContents*

    1\. Usage ................ |PotionUsage|
    2\. Mappings ............. |PotionMappings|
    3\. License .............. |PotionLicense|
    4\. Bugs ................. |PotionBugs|
    5\. Contributing ......... |PotionContributing|
    6\. Changelog ............ |PotionChangelog|
    7\. Credits .............. |PotionCredits| 
```

有很多事情需要在这里提一下。 首先，`=`字符组成的那行将被高亮。你可以用这些行醒目地隔开你的帮助文档各部分。 你也可以使用`-`隔开子段落，如果想要的话。

`*PotionContents*`将创建另一个 tag，这样用户可以输入`:help PotionContents`来直接跳到内容目录。

用`|`包起每一个词将创建一个跳转到 tag 的链接。 用户可以把他们的光标移到词上并按下`<c-]>`跳转到对应 tag，就像他们输入`:help TheTag`一样。 他们也可以用鼠标点开。

Vim 将隐藏`*`和`|`并高亮其间的内容，所以用户将会看到一个整洁漂亮的目录，以便于跳到感兴趣的地方。

## 段落

你可以像这样创建一个段头：

```
:::text
====================================================================
Section 1: Usage                                       *PotionUsage*

This plugin with automatically provide syntax highlighting for
Potion files (files ending in .pn).

It also... 
```

确保对`*`围起的内容创建了正确的 tags，这样你的目录的链接才能正常工作。

继续并为目录中每一部分创建段头。

## 例子

我可以讲述所有的帮助文件语法和怎样使用它们，但我不喜欢这样。 所以，不如我给你一系列不同类型的 Vim 插件文档作为例子。

对于每个例子，复制文档源代码到一个 Vim 缓冲区并设置它的 filetype 为`help`来观察它的渲染。 如果你想比较每个渲染效果，切回`text`看看。

你也许需要使用你的 Vimscript 技能为当前缓冲区创建一个切换于`help`和`text`的映射。

*   [Clam](https://github.com/sjl/clam.vim/blob/master/doc/clam.txt)，我自己用来写 shell 命令的插件。这是一个很小的范例，满足了我前面讲过的大多数内容。
*   [NERD tree](https://github.com/scrooloose/nerdtree/blob/master/doc/NERD_tree.txt)，Scrooloose 写的一个文件浏览插件。 注意大体结构，还有他如何在详尽解释每一项之前，总结出一个易读的列表。
*   [Surround](https://github.com/tpope/vim-surround/blob/master/doc/surround.txt)，Tim Pope 写的一个处理环绕字符的插件。 注意到它没有目录，以及不同的段头风格和表格列项(table column headers)。 弄懂他是怎么做到的，并想想你是否喜欢这种风格。这是个人风格问题啦。
*   [Splice](https://github.com/sjl/splice.vim/blob/master/doc/splice.txt)，我自己用来解决版本控制中[three-way merge conflict](http://en.wikipedia.org/wiki/Merge_(revision_control)#Three-way_merge)的插件。 注意映射列表的排版方式，以及我怎样使用 ASCII 流派的图片来解释布局。有时候，一图胜千言。

不要忘了，Vim 本身的文档也可以作为一个例子。这会给你许多可供学习的内容。

## 写！

既然你已经看过其他插件如何规划和撰写它们的文档，给你的 Potion 插件填补上文档内容吧。

如果你不熟悉技术文档的写作，这可能会是个挑战。 学习如何去写并不容易，但一如其他技能，它需要的是更多的练习，所以现在开始吧！ 你不必苛求完美，从战争中学习战争即可。

不要惧于写你没有完全弄懂的事情，待会丢掉它重写即可。 经常只要在缓冲区中*信手留下几笔*，将会带动你的头脑进入写作状态。 任何时候你想重起炉灶，旧版本一直会在版本控制中等你。

一个开始的好方法是想象你身边也有一个使用 Vim 的好基友。 他对你的插件很感兴趣却未曾用过，而你的目标是让他熟练掌握。 在你写下插件工作的方式之前，考虑如何向人类进行介绍，可以让你脚踏实地，避免太深入于技术层面。

如果你依旧卡住了，感觉自己无力应对写一个完整插件的文档的挑战，尝试做点简单的。 在你的`~/.vimrc`中找一个映射并给它写下完整的文档。解释它是干什么的，怎么用它，它怎么工作。 比如，这是我的`~/.vimrc`的一个例子：

```
:::vim
" "Uppercase word" mapping.
"
" This mapping allows you to press <c-u> in insert mode to convert the
" current word to uppercase.  It's handy when you're writing names of
" constants and don't want to use Capslock.
"
" To use it you type the name of the constant in lowercase.  While
" your cursor is at the end of the word, press <c-u> to uppercase it,
" and then continue happily on your way:
"
"                            cursor
"                            v
"     max_connections_allowed|
"     <c-u>
"     MAX_CONNECTIONS_ALLOWED|
"                            ^
"                            cursor
"
" It works by exiting out of insert mode, recording the current cursor
" location in the z mark, using gUiw to uppercase inside the current
" word, moving back to the z mark, and entering insert mode again.
"
" Note that this will overwrite the contents of the z mark.  I never
" use it, but if you do you'll probably want to use another mark.
inoremap <C-u> <esc>mzgUiw`za 
```

它比一个完整插件的文档短很多，却是一个练习写作的好练习。 如果你把`~/.vimrc`放到 Bitbucket 或 GitHub，别人也更容易理解。

## 练习

给 Potion 插件每一部分写下文档。

阅读`:help help-writing`来帮助你写帮助文档。

阅读`:help :left`, `:help :right`,和`:help :center`来学习三个有用的命令使得你的 ASCII 艺术字更好看。