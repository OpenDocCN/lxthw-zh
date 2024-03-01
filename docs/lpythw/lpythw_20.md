# 练习 16.读写文件

# 练习 16.读写文件

如果你做了上一个练习的附加题部分，你应该已经了解了文件相关的各种命令（方法/函数）。下面的这张表，是你应该记住的命令：

> *   close -- 关闭文件。跟你编辑器的 文件->保存.. 一个意思。
> *   read -- 读取文件内容。你可以把结果赋给一个变量。
> *   readline -- 读取文本文件中的一行。
> *   truncate -- 清空文件，请谨慎使用该命令。
> *   write('stuff') -- 将 stuff 写入文件。

这是你现在该知道的重要命令。有些命令需要接受参数，这对我们并不重要。你只要记住 `write` 需要接收一个字符串作为参数，从而将该字符串写入文件。

让我们来使用这些命令做一个简单的文本编辑器吧:

```py
from sys import argv

script, filename = argv

print "We're going to erase %r." % filename
print "If you don't want that, hit CTRL-C (^C)."
print "If you do want that, hit RETURN."

raw_input("?")

print "Opening the file..."
target = open(filename, 'w')

print "Truncating the file.  Goodbye!"
target.truncate()

print "Now I'm going to ask you for three lines."

line1 = raw_input("line 1: ")
line2 = raw_input("line 2: ")
line3 = raw_input("line 3: ")

print "I'm going to write these to the file."

target.write(line1)
target.write("\n")
target.write(line2)
target.write("\n")
target.write(line3)
target.write("\n")

print "And finally, we close it."
target.close() 
```

这个文件是够大的，大概是你创建过的最大的文件。所以慢慢来，仔细检查，让它能运行起来。有一个小技巧就是你可以让你的脚本一部分一部分地运行起来。先写 1-8 行，让它运行起来，再多运行 5 行，再接着多运行几行，以此类推，直到整个脚本运行起来为止。

## 你看到的结果

你将看到两样东西，一个是你脚本的输出:

```py
$ python ex16.py test.txt
We're going to erase 'test.txt'.
If you don't want that, hit CTRL-C (^C).
If you do want that, hit RETURN.
?
Opening the file...
Truncating the file.  Goodbye!
Now I'm going to ask you for three lines.
line 1:  Mary had a little lamb
line 2:  Its fleece was white as snow
line 3:  It was also tasty
I'm going to write these to the file.
And finally, we close it. 
```

接下来打开你新建的文件（我的是 test.txt）检查一下里边的内容，怎么样，不错吧？

## 附加题

> 1.  如果你觉得自己没有弄懂的话，用我们的老办法，在每一行之前加上注解，为自己理清思路。就算不能理清思路，你也可以知道自己究竟具体哪里没弄明白。
> 2.  写一个和上一个练习类似的脚本，使用`read`和`argv`读取你刚才新建的文件。
> 3.  文件中重复的地方太多了。试着用一个 `target.write()` 将 line1, line2, line3 打印出来，你可以使用字符串、格式化字符、以及转义字符。
> 4.  找出为什么我们需要给 open 多赋予一个 'w' 参数。提示： open 对于文件的写入操作态度是安全第一，所以你只有特别指定以后，它才会进行写入操作。
> 5.  如果你使用'w' 模式打开一个文件，那么还需要`target.truncate()`吗?阅读 Python 关于`open`函数的文档， 看你理解的对不对。

## 常见问题

### Q:`truncate()`方法必须要有参数'w'吗?

> 参考附加题 5

### Q: 'w'参数是什么意思?

> 它只是打开文件的一种模式。如果你用了这个参数，表示"以写（`write`）模式打开文件。同样有`'r'`表示只读模式，`'a'`表示追加模式，还有一些其他的修饰符。

### Q: 有什么修饰符我可以用在打开文件的模式上？

> 最重要的一个就是`+`, 使用它，你可以有`'w+'`, `'r+'`, 和`'a+'`模式. 这样可以同时以读写模式打开文件。

### Q: `open(filename)`是以'r' (只读) 模式打开文件吗?

> 是的，'r' 是 `open()`函数的默认参数值。