# 练习 8.打印, 打印

# 练习 8.打印, 打印

现在，我们学习一个字符串怎样使用更复杂的格式化字符。下面的代码看起来很复杂，但是如果你能将代码分段，并给每一行加上注释，你一样可以弄明白代码的意思。

```py
formatter = "%r %r %r %r"

print formatter % (1, 2, 3, 4)
print formatter % ("one", "two", "three", "four")
print formatter % (True, False, False, True)
print formatter % (formatter, formatter, formatter, formatter)
print formatter % (
    "I had this thing.",
    "That you could type up right.",
    "But it didn't sing.",
    "So I said goodnight."
) 
```

## 你看到结果

```py
$ python ex8.py
1 2 3 4
'one' 'two' 'three' 'four'
True False False True
'%r %r %r %r' '%r %r %r %r' '%r %r %r %r' '%r %r %r %r'
'I had this thing.' 'That you could type up right.' "But it didn't sing." 'So I said goodnight.' 
```

仔细研究一下，并尝试分析下我是怎样在一个格式化字符串内部嵌套使用格式化的

## 附加题

> 1.自己检查结果，记下你犯过的错误，并且在下个练习中尽量不犯同样的错误。2.注意最后一行程序中既有单引号又有双引号，你觉得它是如何工作的？

## 常见问题

### Q:我可以用`%s`或者`%r`来格式化字符串吗？

> 可以用`%s`，但是尽量在做调试的时候使用`%r`。%r 显示的是变量“原始”的数据值，%r 在打印的时候能够重现它代表的对象。

### Q:为什么给`one`使用引号，而不给`True`和`False`使用？

> Python 识别 `True`和`False`表示真假的概念。如果你给它们加上引号，它们就变成了字符串，而不能用来判别真假了。在后面的习题 27 里，你会学到这些布尔值是如何运行的。

### Q: 我尝试在字符串中输入一些中文(或者其它非 ASCII 字符)，但是`%r`打印出一些奇怪的符号。

> 换成`%s`试试，就能正常打印啦。

### Q:为什么有时候我写的是双引号，而`%r`打印输出的是单引号？

> Python 可以用最有效的方式打印输出字符串，而不是直接复制你写的代码。你说的情况是很正常的，因为`%r`常用来调试或检查，因此没必要将它输出的很漂亮。

### Q:这些代码在 Python3 中为什么没有执行?

> 不要用 Python3.用 python2.7 会好一些，最好用 Python2.6。

### Q:我可以用 IDE 来执行程序吗？

> 不行，你现在需要学习使用命令行模式。这是你开始学习编程最好的方法，对你学习编程是很重要的。IDE 不利于你使用本书学习编程。