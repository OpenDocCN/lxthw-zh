# 第四章 检查状态

## 4.1 目的

学习如何检查仓库的状态。

## 4.2 检查仓库的状态

使用 `git status` 命令检查仓库的当前状态。

```
$ git status
```

你应该看到：

```
$ git status
# On branch master
nothing to commit (working directory clean)
```

`status` 命令报告没有要提交的内容。这意味着仓库包含工作目录的所有状态。没有待解决的更改要记录。

我们将继续使用 `git status` 命令来监视仓库和工作目录之间的状态。