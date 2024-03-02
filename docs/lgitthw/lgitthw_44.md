# 第四十四章 拉取更改

## 44.1 目的

学习 `git pull` 等价于 `git fetch` 和 `git merge`。

## 44.2 讨论

我们不会创建另外的更改过程并再次拉取它，而是做你想要知道的做法：

```
$ git pull
```

等价于以下两步：

```
$ git fetch
$ git merge origin/master
```