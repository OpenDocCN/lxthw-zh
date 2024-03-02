# 第十一章 别名

## 11.1 目的

学习如何设置别名及简写 Git 命令。

## 11.2 常用别名

`git status`、`git add`、`git commit`、`git checkout` 是非常常用的命令，因此对它们进行缩写十分有用。

添加下列内容到你的 `$HOME` 目录的 `.gitconfig` 文件中：

```
[alias]
  co = checkout
  ci = commit
  st = status
  br = branch
  hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph \
  --date=short
  type = cat-file -t
  dump = cat-file -p
```

我们已经介绍了 `commit` 和 `status` 命令，并且在上个实验中也介绍了 `log` 命令。`checkout` 命令将接下来介绍。

使用这些在 `.gitconfig` 中定义的别名，你可以通过输入 `git co` 来表示 `git checkout`。同时，`git st` 表示 `git status`，而 `git ci` 表示 `git commit`。并且，最好的是 `git hist` 将使你避免很长的 `log` 命令。

去试试新命令吧。

## 11.3 在 `.gitconfig` 文件中定义 hist 别名

在大多数介绍中，我将继续输入完整的命令。唯一的例外是，当我需要看 `git log` 的输出时，我将使用上面定义的 `hist` 别名。如果你想要遵循这里的约定，那么在继续前设置你的 `.gitconfig` 文件。

## 11.4 输入与转存

我们已经添加了几个还没有介绍的命令别名。`git branch` 命令很快将介绍。`git cat-file` 命令对于浏览 Git 很有用，一会儿我们将看看。

## 11.5 Shell 别名（可选）

注意：本节是为那些运行 POSIX 类 Shell 的同学写的。Windows 用户及其他非 POSIX Shell 用户可以跳到下一个实验。

如果你的 Shell 支持别名或简写，那么你可以添加一些别名。下面是我使用的：

文件：.profile

```
alias gs='git status '
alias ga='git add '
alias gb='git branch '
alias gc='git commit'
alias gd='git diff'
alias go='git checkout '
alias gk='gitk --all&'
alias gx='gitx --all'

alias got='git '
alias get='git '
```

`git checkout` 的缩写 `go` 尤其好，它允许我输入：

```
$ go <branch>
```

来检出一个特定的分支。

另外，我也经常通过创建足够多的别名来避免打错 Git 命令。

注意：有些 Shell 别名有点攻击性。实际上，`gs` 将与 Linux GhostScript 程序冲突。最近我开始使用 Go 编程语言，因此必须禁用上面的 `go` 别名。所以使用这些别名要小心。