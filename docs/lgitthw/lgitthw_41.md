# 第四十一章 更改原始仓库

## 41.1 目的

对原始仓库做些更改以便我们可以尝试拉取更改。

## 41.2 在原始的 hello 仓库中做更改

```
$ cd ../hello
# (You should be in the original hello repository now)
```

注意：现在在 hello 仓库中。

对 `README` 做下列更改：

```
This is the Hello World example from the git tutorial.
(changed in original)
```

现在添加并提交此更改。

```
$ git add README
$ git commit -m "Changed README in original repo"
```

## 41.3 下一步

原始仓库现在有克隆版本中所没有的更改。接下来我们将拉取这些更改到克隆仓库中。