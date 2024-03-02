# 第七章 暂存与提交

在 Git 中分开暂存是直到你需要使用源码控制处理的协调解决方法。你可以继续对工作目录做更改，然后当你想要与源码控制交互时，Git 允许你使用微小的提交来精确地记录所作的更改。

例如，假设你编辑了三个文件（`a.rb`、`b.rb` 及 `c.rb`）。现在你想提交所有更改，但你想要 `a.rb` 和 `b.rb` 中的更改作为单个提交，而 `c.rb` 的更改与前两个文件在逻辑上不相关，那么应该分开提交。

你可以执行下列命令：

```
$ git add a.rb
$ git add b.rb
$ git commit -m "Changes for a and b"

$ git add c.rb
$ git commit -m "Unrelated change to c"
```

通过分开暂存和提交，你能更容易地微调每一个提交。