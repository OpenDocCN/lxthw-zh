# 练习 7.更多的打印（输出）

# 练习 7.更多的打印（输出）

现在我们将做一批练习，在练习的过程中你需要输入代码，并让它们运行起来。我不会解释太多，因为这节的内容都是以前熟悉过的。这节练习的目的是巩固你学到的东西。我们几个练习后再见。不要跳过这些习题。不要复制粘贴！

```py
print "Mary had a little lamb."
print "Its fleece was white as %s." % 'snow'
print "And everywhere that Mary went."
print "." * 10  # what'd that do?

end1 = "C"
end2 = "h"
end3 = "e"
end4 = "e"
end5 = "s"
end6 = "e"
end7 = "B"
end8 = "u"
end9 = "r"
end10 = "g"
end11 = "e"
end12 = "r"

# watch that comma at the end.  try removing it to see what happens
print end1 + end2 + end3 + end4 + end5 + end6,
print end7 + end8 + end9 + end10 + end11 + end12 
```

## 你看到的结果

```py
$ python ex7.py
Mary had a little lamb.
Its fleece was white as snow.
And everywhere that Mary went.
..........
Cheese Burger 
```

## 附加题

> 1.逆向阅读，给每一行的加上注释。2.倒着朗读出来，找出自己的错误。3.从现在开始，把你犯过的错误记录一张纸上。4.在开始下一节习题时，阅读一遍你记录下来的错误，并且尽量避免在下个练习中再犯同样的错误。5.记住，每个人都会犯错误。程序员和魔术师一样，他们希望大家认为他们从不犯错，不过这只是表象而已，他们每时每刻都在犯错。

## 常见问题

### Q: 为什么使用名字为'snow'的变量?

> 这个可不是一个变量，这只是一个字符串，变量的两边可不会出现单引号。

### Q:有必要像你在附加题 1 中说的那样，给每一行代码加上英文注释吗？

> 也不是，你给每一行加上注释，只是方便你理解每一行代码的功能，不过，有时候当你要编码解决一个较难的问题时，还是需要加上注释的，这样能训练你将代码翻译成自己的语言。

### Q:我可以用单引号或双引号标识一个字符串，那它们有什么不同吗?

> 在 Python 中，单双引号都可以用来标识一个字符串，单引号更多用在较短的字符串上。

### Q:能不能不用逗号，而把最后两行合并到一行的`print`里?

> 当然可以，你能很容易做到这一点，但是这一行会变的很长，会超过 80 个字符，这在 Python 中可不是好的代码风格。