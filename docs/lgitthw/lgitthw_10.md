# 第十章 历史

## 10.1 目的

学习如何查看项目的历史。

`git log` 命令能够获得已做过的更改清单。

```
$ git log
```

你应该看到：

```
$ git log
commit 1f7ec5eaa8f37c2770dae3b984c55a1531fcc9e7
Author: Jim Weirich <jim (at) neo.com>
Date:   Sat Apr 13 15:20:42 2013 -0400

    Added a comment

commit 582495ae59ca91bca156a3372a72f88f6261698b
Author: Jim Weirich <jim (at) neo.com>
Date:   Sat Apr 13 15:20:42 2013 -0400

    Added a default value

commit 323e28d99a07d404c04f27eb6e415d4b8ab1d615
Author: Jim Weirich <jim (at) neo.com>
Date:   Sat Apr 13 15:20:42 2013 -0400

    Using ARGV

commit 94164160adf8faa3119b409fcfcd13d0a0eb8020
Author: Jim Weirich <jim (at) neo.com>
Date:   Sat Apr 13 15:20:42 2013 -0400

    First Commit
```

这份清单是迄今为止我们对仓库所作的总共 4 次提交。

## 10.2 单行历史

你可以控制 `log` 命令要精确显示的内容。我喜欢单行格式：

```
$ git log --pretty=oneline
```

你应该看到：

```
$ git log --pretty=oneline
1f7ec5eaa8f37c2770dae3b984c55a1531fcc9e7 Added a comment
582495ae59ca91bca156a3372a72f88f6261698b Added a default value
323e28d99a07d404c04f27eb6e415d4b8ab1d615 Using ARGV
94164160adf8faa3119b409fcfcd13d0a0eb8020 First Commit
```

## 10.3 控制显示哪个条目

`log` 命令有许多选项用来选择显示哪个条目。试试下面的选项：

```
$ git log --pretty=oneline --max-count=2
$ git log --pretty=oneline --since='5 minutes ago'
$ git log --pretty=oneline --until='5 minutes ago'
$ git log --pretty=oneline --author=<your name>
$ git log --pretty=oneline --all
```

参阅 `man git-log` 了解更多细节。

## 10.4 更加漂亮

这是我用来复查上周所做更改的命令。如果我只想看自己所作的更改，那么我将添加 `--author=jim`。

```
$ git log --all --pretty=format:'%h %cd %s (%an)' \
    --since='7 days ago'
```

## 10.5 终极日志格式

随着时间的推移，我发现在工作时最喜欢下列日志格式。

```
$ git log --pretty=format:'%h %ad | %s%d [%an]' --graph \
    --date=short
```

它看起来像这样：

```
$ git log --pretty=format:'%h %ad | %s%d [%an]' --graph \
    --date=short
* 1f7ec5e 2013-04-13 | Added a comment (HEAD, master) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

让我们看一下细节：

*   `--pretty="..."` 定义输出的格式
*   `%h` 是提交 hash 的缩写
*   `%d` 是提交的装饰（如分支头或标签）
*   `%ad` 是创作日期
*   `%s` 是注释
*   `%an` 是作者姓名
*   `--graph` 使用 ASCII 图形布局显示提交树
*   `--date=short` 保留日期格式更好且更短

## 10.6 其它工具

gitx (Mac) 和 gitk (任意平台) 在浏览日志历史时十分有用。