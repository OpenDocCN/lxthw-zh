# 第一章 设置

## 1.1 目的

设置 Git 以便准备开始工作。

## 1.2 设置姓名和邮箱

如果你以前从来没有使用过 Git，那么你必需先做一些设置。执行下列命令能够让 Git 知道你的姓名和邮箱。如果你已经设置了 Git，那么可以跳到下一节。

```
$ git config --global user.name "Your Name"
$ git config --global user.email "your_email@whatever.com"
```

## 1.3 设置行尾选项

Unix/Mac 用户：

```
$ git config --global core.autocrlf input
$ git config --global core.safecrlf true
```

Windows 用户：

```
$ git config --global core.autocrlf true
$ git config --global core.safecrlf true
```