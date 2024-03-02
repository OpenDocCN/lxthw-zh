# 第二十八章 合并

## 28.1 目的

学习如何合并两个分叉的分支以便将更改带回到单一分支。

## 28.2 合并分支

合并将两个分支中的更改结合在一起。让我们回到 greet 分支， 并将 master 合并过来。

```
$ git checkout greet
$ git merge master
$ git hist --all
```

```
$ git checkout greet
Switched to branch 'greet'
$ git merge master
Merge made by recursive.
 README |    1 +
 1 files changed, 1 insertions(+), 0 deletions(-)
 create mode 100644 README
$ git hist --all
*   844d1ed 2013-04-13 | Merge branch 'master' into greet
| (HEAD, greet) [Jim Weirich]
|\
| * b59a8c2 2013-04-13 | Added README (master) [Jim Weirich]
* | 28917a4 2013-04-13 | Updated Rakefile [Jim Weirich]
* | 4dac415 2013-04-13 | Hello uses Greeter [Jim Weirich]
* | 39347b3 2013-04-13 | Added greeter class [Jim Weirich]
|/
* 96ee164 2013-04-13 | Added a Rakefile. [Jim Weirich]
* 0f36766 2013-04-13 | Moved hello.rb to lib [Jim Weirich]
* eb30103 2013-04-13 | Add an author/email comment [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta)
[Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

通过周期性地合并 master 到 greet 分支，你可以选择 master 的任意更改，并保持 greet 中的更改与主干中的更改兼容。

然而，这会产生丑陋的提交图。稍后我们将看看变基替代合并这个选项。

## 28.3 下一步

如果 master 中的更改与 greet 中的冲突怎么办？