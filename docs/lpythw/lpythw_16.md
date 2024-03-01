# 练习 12.提示别人

# 练习 12.提示别人

当你输入`raw_input()` 的时候，你需要键入 `(` 和 `)` 也就是“括号(parenthesis)”。这和你格式化输出两个以上变量时的情况有点类似，比如说 "%s %s" % (x, y) 里边就有括号。对于 raw_input 而言，你还可以让它显示出一个提示，从而告诉别人应该输入什么东西。你可以在 () 之间放入一个你想要作为提示的字符串，如下所示：

```py
y = raw_input("Name? ") 
```

这句话会用 “Name?” 提示用户，然后将用户输入的结果赋值给变量 y。这就是我们提问用户并且得到答案的方式。

也就是说，我们的上一个练习可以使用 `raw_input`重写一次。所有的提示都可以通过`raw_input` 实现。

```py
age = raw_input("How old are you? ")
height = raw_input("How tall are you? ")
weight = raw_input("How much do you weigh? ")

print "So, you're %r old, %r tall and %r heavy." % (
    age, height, weight) 
```

## 你看到的结果

```py
$ python ex12.py
How old are you?  38
How tall are you?  6'2"
How much do you weigh?  180lbs
So, you're '38' old, '6\'2"' tall and '180lbs' heavy. 
```

## 附加题

> 1.  在命令行界面下运行你的程序，然后在命令行输入 `pydoc raw_input` 看它说了些什么。如果你用的是 Window，那就试一下 `python -m pydoc raw_input` 。
> 2.  输入 `q` 退出 `pydoc`。
> 3.  上网找一下 `pydoc` 命令是用来做什么的。
> 4.  使用 `pydoc` 再看一下 `open`, `file`, `os`, 和 `sys` 的含义。看不懂没关系，只要通读一下，记下你觉得有意思的点就行了。

## 常见问题

### Q:我运行`pydoc` 的时候，为什么会遇到这个报错`invalid syntax`?

> 你没有在命令行里执行`pydoc`; 你是不是在启动`python`后执行的？退出 Python 试试吧.

### Q:我执行`pydoc`的时候，我遇到一个提示`pydoc 不是内部或外部命令` 。

> 有一些 windows 上的 Python 版本没有提供这个命令,你可以跳过这个附加练习，当你需要阅读 Python 文档的时候，你在网上搜索就可以了。

### Q:为什么用`%r`而不是`%s`?

> 请务必记住 `%r` 会原样输出你输入的每一个字符，而`%s`是用来显示你的输入的。下次，我不会再回答相同的问题。这是大家重复问到次数最多的问题，但是一遍一遍问相同的问题，说明你没有记住我讲过的内容。

### Q:为什么不能这样输入`"How old are you?" , raw_input()`?

> 你觉得它会生效的, 但是 Python 认为这种写法是不合法的. 我能告诉你的也只能是你不能这样么写。