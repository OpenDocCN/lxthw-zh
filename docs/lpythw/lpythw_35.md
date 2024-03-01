# 练习 31.做出决定

# 练习 31.做出决定

这本书的上半部分你打印了一些东西，而且调用了函数，不过一切都是直线式进行的。你的脚本从最上面一行开始，一路运行到结束，但其中并没有决定程序流向的分支点。现在你已经学了`if`,`else`,和`elif`，你就可以开始创建包含条件判断的脚本了。

上一个脚本中你写了一系列的简单提问测试。这节的脚本中，你将需要向用户提问，依据用户的答案来做出决定。把脚本写下来，多多鼓捣一阵子，看看它的工作原理是什么。

```py
print "You enter a dark room with two doors.  Do you go through door #1 or door #2?"

door = raw_input("> ")

if door == "1":
    print "There's a giant bear here eating a cheese cake.  What do you do?"
    print "1\. Take the cake."
    print "2\. Scream at the bear."

    bear = raw_input("> ")

    if bear == "1":
        print "The bear eats your face off.  Good job!"
    elif bear == "2":
        print "The bear eats your legs off.  Good job!"
    else:
        print "Well, doing %s is probably better.  Bear runs away." % bear

elif door == "2":
    print "You stare into the endless abyss at Cthulhu's retina."
    print "1\. Blueberries."
    print "2\. Yellow jacket clothespins."
    print "3\. Understanding revolvers yelling melodies."

    insanity = raw_input("> ")

    if insanity == "1" or insanity == "2":
        print "Your body survives powered by a mind of jello.  Good job!"
    else:
        print "The insanity rots your eyes into a pool of muck.  Good job!"

else:
    print "You stumble around and fall on a knife and die.  Good job!" 
```

这里的重点是你可以在“if 语句”内部再放一个“if 语句”。这是一个很强大的功能，可以用来创建嵌套(nested)，其中的一个分支将引向另一个分支的子分支。

你需要理解`if 语句`包含`if 语句`的概念。做一下附加题，确保自己真正理解了它们。

## 你看到的结果

下面是我玩这个小游戏的结果，我玩的不怎么样：

```py
$ python ex31.py
You enter a dark room with two doors.  Do you go through door #1 or door #2?
>  1
There's a giant bear here eating a cheese cake.  What do you do?
1\. Take the cake.
2\. Scream at the bear.
>  2
The bear eats your legs off.  Good job! 
```

## 附加题

> 1.  为游戏添加新的部分，改变玩家做决定的位置。尽自己的能力扩展这个游戏，不过别把游戏弄得太怪异了。
> 2.  写一个全新的游戏，你可能不喜欢我提供的这个，那么自己写一个玩玩。这是你的电脑，你可以用它做任何自己想做的事情。

## 常见问题

### Q: 可以用`if-else`替换`elif` 吗？

> 某些情况下可以, 但是这个也依赖于每一个`if/else`是怎么写的 。这也意味着， Python 会检查每个 if-else 的组合，而不是只检查`if-elif-else`组合中的第一个为假的分支，尝试用两种方式多编写一些代码，以找出他们的不同点。

### Q:我怎么知道一个数字是在一个数字范围之间？

> 有两种方法: 一种经典的方式是使用`0 &lt; x &lt; 10` 或者 `1 &lt;= x &lt; 10`,另一中方式是使用`x in range(1, 10)`。

### Q: 怎样才能在`if-elif-else`代码块中增加更多的选择？

> 为每一个可能的选择增加一个`elif` 代码块。