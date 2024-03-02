# 第三十四章 变基

## 34.1 目的

使用 `rebase` 命令代替 `merge` 命令。

我们回到了第一次合并前的时间点，并且我们想要将 master 中的更改集成到 greet 分支。

这次我们将使用 `rebase` 命令代替 `merge` 命令来从 master 分支中引入更改。

```
$ git checkout greet
$ git rebase master
$ git hist
```

```
$ go greet
Switched to branch 'greet'
$
$ git rebase master
First, rewinding head to replay your work on top of it...
Applying: added Greeter class
Applying: hello uses Greeter
Applying: updated Rakefile
$
$ git hist
* 2fae0b2 2013-04-13 | Updated Rakefile (HEAD, greet)
[Jim Weirich]
* 1c23048 2013-04-13 | Hello uses Greeter [Jim Weirich]
* 62d7ce0 2013-04-13 | Added greeter class [Jim Weirich]
* b59a8c2 2013-04-13 | Added README (master) [Jim Weirich]
* 96ee164 2013-04-13 | Added a Rakefile. [Jim Weirich]
* 0f36766 2013-04-13 | Moved hello.rb to lib [Jim Weirich]
* eb30103 2013-04-13 | Add an author/email comment [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta)
[Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

## 34.2 合并 VS 变基

变基的最终结果与合并很相似。greet 分支现在包含它的全部更改以及来自 master 分支中的所有更改。然而，提交树却十分不同。greet 分支的提交树已被重写，以致 master 分支成为了其提交历史的一部分。这使提交链更加线性，且更易阅读。

## 34.3 何时变基，何时合并?

不要使用变基……

如果是公开且与其他人共享的分支，那么重写公开的共享分支将会搞砸团队中的其他会员。

要是提交分支的精确历史重要（因为变基将重写提交历史）。

根据上述准则，我会针对短期生命的本地分支使用变基，而对公开仓库的分支使用合并。