# 第三章 创建项目

## 3.1 目的

学习如何从零开始创建 Git 仓库。

## 3.2 创建“Hello, World”程序

在空工作目录中创建一个名为“hello”的空目录，然后创建名为 `hello.rb` 且包含如下内容的文件。

```
$ mkdir hello
$ cd hello
```

文件：hello.rb

```
puts "Hello, World"
```

## 3.3 创建仓库

你现在有一个包含单文件的目录。要从该目录创建 Git 仓库，需执行 `git init` 命令。

```
$ git init
```

输出：

```
$ git init
Initialized empty Git repository in /Users/jim/working/git/
git_immersion/auto/hello/.git/
```

## 3.4 添加程序到仓库

现在让我们添加“Hello, World”程序到仓库。

```
$ git add hello.rb
$ git commit -m "First Commit"
```

你应该看到：

```
$ git add hello.rb
$ git commit -m "First Commit"
[master (root-commit) 9416416] First Commit
 1 files changed, 1 insertions(+), 0 deletions(-)
 create mode 100644 hello.rb
```