# 第八章 提交更改

## 8.1 目的

学习如何提交更改到仓库。

## 8.2 提交更改

关于暂存谈得差不多了。让我们提交已暂存的内容到仓库。

当你先前使用 `git commit` 命令提交 `hello.rb` 文件的初始版本到仓库时，在命令行中的 `-m` 选项可以包含注释。`commit` 命令将允许你交互式地编辑提交的注释。现在让我们试试看。

如果你从命令行忽略 `-m` 选项，那么 Git 将带你到所选的编辑器中。编辑器按以下列表选择（使用优先级顺序）：

*   `GIT_EDITOR` 环境变量
*   `core.editor` 配置设置
*   `VISUAL` 环境变量
*   `EDITOR` 环境变量

我已将 `EDITOR` 变量设置为 `emacsclient`。

那么，现在提交并检查状态。

```
$ git commit
```

你应当在编辑器中看到下面的内容：

```
|
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   modified:   hello.rb
#
```

在第一行，输入注释：“Using ARGV”。保存文件，并退出编辑器。你应该看到：

```
git commit
Waiting for Emacs...
[master 569aa96] Using ARGV
 1 files changed, 1 insertions(+), 1 deletions(-)
```

“Waiting for Emacs…”来自 `emacsclient` 程序，该程序将文件发送到正在运行的 Emacs，并等候关闭文件。其余的输出是标准的提交信息。

## 8.3 检查状态

最后，让我们再检查下状态。

```
$ git status
```

你应该看到：

```
$ git status
# On branch master
nothing to commit (working directory clean)
```

工作目录是干净的，且准备让你继续。