# 第十五章 撤销暂存的更改

## 15.1 目的

学习如何还原已经暂存的更改。

## 15.2 更改文件并暂存更改

修改 `hello.rb` 文件来包含一个错误的注释。

```
# This is an unwanted but staged comment
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

然后去暂存它。

```
$ git add hello.rb
```

## 15.3 检查状态

检查你不想要的更改状态。

```
$ git status
```

```
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   modified:   hello.rb
#
```

`status` 输出显示更改已被暂存且准备提交。

## 15.4 重置暂存区

幸运的是 `status` 输出告诉我们取消暂存更改时需要做什么。

```
$ git reset HEAD hello.rb
```

```
$ git reset HEAD hello.rb
Unstaged changes after reset:
M   hello.rb
```

`reset` 命令重置 HEAD 中暂存区的内容。这将清除我们已经暂存的更改。

`reset` 命令（默认）不会更改工作目录。所以在工作目录中仍然有不想要的注释。我们可以使用之前实验中的 `checkout` 命令来从工作目录移除不想要的更改。

## 15.5 检出提交的版本

```
$ git checkout hello.rb
$ git status
```

```
$ git status
# On branch master
nothing to commit (working directory clean)
```

现在我们的工作目录又变干净了。