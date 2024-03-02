# 第六章 暂存更改

## 6.1 目的

学习如何暂存更改以便稍后进行提交。

## 6.2 添加更改

现在告诉 Git 暂存更改，并检查状态。

```
$ git add hello.rb
$ git status
```

你应该看到：

```
$ git add hello.rb
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   modified:   hello.rb
#
```

对 `hello.rb` 文件的更改已被暂存。这意味着 Git 现在了解这些更改，但还没有永久记录到仓库中。下面的提交操作将包含暂存的更改。

如果你决定不提交更改，那么 `status` 命令将提醒你使用 `git reset` 命令取消暂存更改。