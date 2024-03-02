# 第四十章 远程分支

## 40.1 目的

学习有关本地与远程分支的内容。

让我们看看在克隆的仓库中可用的分支。

```
$ git branch
```

```
$ git branch
* master
```

只有 master 分支被列出来了。greet 分支在哪儿？`git branch` 命令默认只会列出本地分支。

## 40.2 列出远程分支

试试执行以下命令来看全部分支：

```
$ git branch -a
```

```
$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/greet
  remotes/origin/master
```

Git 具有原始仓库的全部提交，但在远程仓库中的分支不会作为本地分支。如果我们想要 greet 分支，我们需要自行创建它。一会儿我们将看看如何做到。