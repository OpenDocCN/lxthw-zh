# 第四十三章 合并拉取的更改

## 43.1 目的

学习将拉取的更改合并到当前分支及工作目录。

## 43.2 将拉取的更改合并到本地 master

```
$ git merge origin/master
```

```
$ git merge origin/master
Updating 2fae0b2..2e4c559
Fast-forward
 README |    1 +
 1 files changed, 1 insertions(+), 0 deletions(-)
```

## 43.3 再次检查 README

我们应当看到现在更改了。

```
$ cat README
```

```
$ cat README
This is the Hello World example from the git tutorial.
(changed in original)
```

即使 `git fetch` 不合并更改，然而我们仍然可以手动从远程仓库合并更改。

## 43.4 下一步

接下来让我们看看将 `fetch` 和 `merge` 组合成单个命令。