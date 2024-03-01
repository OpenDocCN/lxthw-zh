# 练习 17.更多文件操作

# 练习 17.更多文件操作

现在让我们再学习几种文件操作。我们将编写一个 Python 脚本，将一个文件中的内容拷贝到另外一个文件中。这个脚本很短，不过它会让你对于文件操作有更多的了解。

```py
from sys import argv
from os.path import exists

script, from_file, to_file = argv

print "Copying from %s to %s" % (from_file, to_file)

# we could do these two on one line, how?
in_file = open(from_file)
indata = in_file.read()

print "The input file is %d bytes long" % len(indata)

print "Does the output file exist? %r" % exists(to_file)
print "Ready, hit RETURN to continue, CTRL-C to abort."
raw_input()

out_file = open(to_file, 'w')
out_file.write(indata)

print "Alright, all done."

out_file.close()
in_file.close() 
```

你应该很快注意到了我们`import`了又一个很好用的命令`exists`。这个命令将文件名字符串作为参数，如果文件存在的话，它将返回`True`，否则将返回 `False`。在本书的下半部分，我们将使用这个函数做很多的事情，不过现在你应该学会怎样通过 import 调用它.

通过使用`import`，你可以在自己代码中直接使用其他更厉害的（通常是这样，不过也不 尽然）程序员写的大量免费代码，这样你就不需要重写一遍了。

## 你看到的结果

和你前面写的脚本一样，运行该脚本需要两个参数，一个是待拷贝的文件，一个是要拷贝至的文件。我再创建一个名为`test.txt`的测试文件，我们将看到如下的结果:

```py
$ echo "This is a test file." > test.txt 
```

$ cat test.txt This is a test file. $ $ python ex17.py test.txt new_file.txt Copying from test.txt to new_file.txt The input file is 21 bytes long Does the output file exist? False Ready, hit RETURN to continue, CTRL-C to abort.

```py
Alright, all done. 
```

该命令对于任何文件都应该是有效的。试试操作一些别的文件看看结果。不过小心别把你的重要文件给弄坏了。

> **Warning:**你看到我用`echo`命令创建一个文件，并用`cat`命令展示一个文件了吧？它们只能在 Linux 和 OSX 下使用，你可以阅读附录 A 获得者两个命令的使用方法。

## 附加题

> 1.  这个脚本 实在是有点烦人。没必要在拷贝之前问一遍把，没必要在屏幕上输出那么多东西。试着删掉脚本的一些功能，让它使用起来更加友好。
> 2.  看看你能把这个脚本改多短，我可以把它写成一行。
> 3.  我使用了一个叫`cat`的东西，这个古老的命令的用处是将两个文件“连接(con_cat_enate)”到一起，不过实际上它最大的用途是打印文件内容到屏幕上。你可以通过 `man cat` 命令了解到更多信息。(windows 下没有这个命令)
> 4.  找出为什么你需要在代码中写 output.close() 。
> 5.  再多读读和`import`相关的材料，将 python 运行起来，试试这一条命令。试着看看自己能不能摸出点门道，当然了，即使弄不明白也没关系。

## 常见问题

### Q: 为什么`'w'`要写在引号里？

> 它只是个字符串，你已经做过太多关于字符串的练习了，你知道什么是字符串的，对吗？

### Q:总是感觉这些练习很难，这正常吗？

> 这很正常的。直到你做完练习 36 甚至完成这本书的学习，用 python 做出一些作品，编程对你来说可能都不是一件简单的事情。每个人都不一样，所以只要坚持复习你认为困难的习题，直到你真的搞明白它们,要有耐心。

### Q:函数`len()`是干什么用的？

> 它能获得参数的长度，返回值是一个数字，你试着用用这个方法。

### Q:我尝试改短代码的时候，在脚本的结尾处遇到一个关于文件关闭的问题。

> 你可能做了一些类似这样的事情，比如`indata = open(from_file).read()`,这样写的话，就不需要在执行关闭操作，当执行完这一行的时候，文件自动就被关闭了。

### Q: 我遇到一个异常`Syntax:EOL while scanning string literal`

> 你应该是忘记在字符串的结尾加上引号了，回到你出错的那行代码，检查一下。