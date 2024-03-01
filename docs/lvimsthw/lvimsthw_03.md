# 预备知识

# 预备知识

阅读本书之前，请确保您的机器已经安装了最新版的 Vim，本书写作时 Vim 的最新版本是 7.3。 新版本的 Vim 会向后兼容，所以本书中的内容在 7.3 之后的版本中应该同样有效。

本书中的内容通用，你可以任意选择 console Vim 或者是 gVim、MacVim 之类的 GUI 作为你的终端。

你最好习惯用 Vim 编辑文件。至少应该知道 Vim 的基本术语，如"buffer"、"window"、 "normal mode"、"insert mode"、"text mode"。

如果你当前不符合上述的条件，建议你阅读命令`vimtutor`的内容、使用 Vim 一两个月，当你 熟练使用 Vim 后再阅读本书。

你需要有一些编程经验。如果没有，建议先阅读《[笨方法学 Python](http://learnpythonthehardway.org/) 》，读完之后再阅读本书。

> **译者注:**原文提到的《笨方法学 Python》是英文的，有问题的读者可以选择阅读 [gastlygem](https://bitbucket.org/gastlygem/lpthw)翻译的中文版《[笨方法学 Python](https://learn-python-the-hard-way-zh_cn-translation.readthedocs.org/en/1.0/intro_zh.html) 》

## 创建 Vimrc 文件

如果你已经清楚`~/.vimrc`的作用并已经有了这个文件，直接跳到下一章继续吧。

`~/.vimrc`文件包含了 Vimscript 代码，每次启动 Vim 时，Vim 都会自动执行其中的代码。

在 Linux 和 Mac OS X 中，这个文件位于你的 home 文件夹，并以`.vimrc`命名。

在 Windows 中，这个文件位于你的 home 文件夹，并以`_vimrc`命名。

在*任意*系统中，在 Vim 中执行`:echo $MYVIMRC`命令可以快速得知这个文件的位置和名称。 文件的路径会在屏幕的底部显示。

如果你的 home 文件夹没有这个文件，请自行创建一个。