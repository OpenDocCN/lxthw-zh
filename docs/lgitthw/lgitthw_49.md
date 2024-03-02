# 第四十九章 拉取共享的更改

## 49.1 目的

学习如何从共享的仓库拉取更改。

迅速跳过克隆仓库，且让我们拉取刚才推送到共享仓库的更改。

```
$ cd ../cloned_hello
```

注意：现在在 cloned_hello 仓库中。

继续处理……

```
$ git remote add shared ../hello.git
$ git branch --track shared master
$ git pull shared master
$ cat README
```