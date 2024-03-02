# 第五章 做更改

## 5.1 目的

学习如何监视工作目录的状态。

## 5.2 更改“Hello, World”程序

是时候更改我们的 `hello` 程序以便使它能从命令行传递参数了。将文件更改为：

```
puts "Hello, #{ARGV.first}!"
```

## 5.3 检查状态

现在检查工作目录的状态。

```
$ git status
```

你应该看到：

```
$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in
#   working directory)
#
#   modified:   hello.rb
#
no changes added to commit (use "git add" and/or "git commit -a")
```

值得注意的第一件事是 Git 知道 `hello.rb` 文件已被修改，但它还没有被通知到。

另外要注意的是状态信息提示你接下来需要做什么。如果你想要将这些更改添加到仓库，那么使用 `git add` 命令。否则，使用 `git checkout` 命令放弃更改。

## 5.4 下一步

让我们暂存更改。