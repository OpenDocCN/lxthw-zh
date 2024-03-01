# 练习 20.函数和文件

# 练习 20.函数和文件

回忆一下函数的要点，然后一边做这节练习，一边注意一下函数和文件是如何在一起协作发挥作用的。

```py
from sys import argv

script, input_file = argv

def print_all(f):
    print f.read()

def rewind(f):
    f.seek(0)

def print_a_line(line_count, f):
    print line_count, f.readline()

current_file = open(input_file)

print "First let's print the whole file:\n"

print_all(current_file)

print "Now let's rewind, kind of like a tape."

rewind(current_file)

print "Let's print three lines:"

current_line = 1
print_a_line(current_line, current_file)

current_line = current_line + 1
print_a_line(current_line, current_file)

current_line = current_line + 1
print_a_line(current_line, current_file) 
```

特别注意一下，每次运行`print_a_line`时，我们是怎样传递当前的行号信息的。

## 你看到的结果

```py
$ python ex20.py test.txt
First let's print the whole file:

This is line 1
This is line 2
This is line 3

Now let's rewind, kind of like a tape.
Let's print three lines:
1 This is line 1

2 This is line 2

3 This is line 3 
```

## 附加题

> 1.  通读脚本，在每行之前加上注解，以理解脚本里发生的事情。
> 2.  每次`print_a_line`运行时，都传递了一个叫`current_line`的变量。在每次调用函数时，打印出`current_line`的值，跟踪一下它在`print_a_line`中是怎样变成`line_count`的。
> 3.  找出脚本中每一个用到函数的地方。检查`def`一行，确认参数没有用错。
> 4.  上网研究一下`file`中的`seek`函数是做什么用的。试着运行`pydoc file`看看能不能学到更多。
> 5.  研究一下`+=`这个简写操作符的作用，写一个脚本，把这个操作符用在里边试一下。

## 常见问题

### Q:函数`print_all`中的`f`是什么?

> `f` 就是一个变量，就好像在练习 18 中其他的变量一样，只不过这次它代表了一个文件。 Python 中的文件就好像老旧的磁带驱动器，或者是像现在的 DVD 播放器。它有一个 "磁头"，你可以在文件中"查找"到这个磁头的位置，并且从那个位置开始运行。你每执行一次 `f.seek(0)`，就靠近文件的开头一点。每执行一次`f.readline()`你就从文件中读取一行内容，并且把“磁头”移动到文件末尾，换行符`\n`的后面。继续学习本书，你会看到更多的解释。

### Q: 文件中为什么有 3 个空行？

> 函数 `readline()` 返回一行以`\n`结尾的文件内容， 在你调用 print 函数的最后增加一个逗号','，用来避免为每一行添加两个换行符`\n`。

### Q:为什么`seek(0)`方法没有把`current_line`的值修改为 0？

> 首先，`seek()`方法是按字节而不是按行为处理单元的。代码`seek(0)`重新定位在文件的第 0 位（第一个字节处）。再次，`current_line`是一个变量，在文件中没有真正的意义可言。我们是在手动的增加它的值。

### Q:`+=`是什么?

> 你应该知道在英语里我们可以简写 "it is" 为 "it's"，简写 "you are" 为 "you're"。在英语里我们把这种写法称为缩写，同样的，`+=`是 `=`和 `+`两个操作符的缩写. 比如`x = x + y`可以缩写为`x += y`.

### Q:`readline()`怎么知道每一行的分界在哪里？

> `readline()`内部代码是扫描文件的每一个字节，直到找到一个`\n`字符代码，然后停止阅读，并返回到此之前获得的所有内容。代码中 f 的责任是在每次调用`readline()`之后，维护“磁头”在文件中的位置，以保证继续读后面的每一行。