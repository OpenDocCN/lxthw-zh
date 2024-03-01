# 练习 29.IF 语句

# 练习 29.IF 语句

下面是你要写又一个 python 脚本，这节练习会向你介绍“if 语句”。把这段代码输入脚本，让它正常运行，看看你有没有什么收获。

```py
people = 20
cats = 30
dogs = 15

if people < cats:
    print "Too many cats! The world is doomed!"

if people > cats:
    print "Not many cats! The world is saved!"

if people < dogs:
    print "The world is drooled on!"

if people > dogs:
    print "The world is dry!"

dogs += 5

if people >= dogs:
    print "People are greater than or equal to dogs."

if people <= dogs:
    print "People are less than or equal to dogs."

if people == dogs:
    print "People are dogs." 
```

## 你看到的结果

```py
$ python ex29.py
Too many cats! The world is doomed!
The world is dry!
People are greater than or equal to dogs.
People are less than or equal to dogs.
People are dogs. 
```

## 附加题

猜猜“if 语句”是什么，它有什么用处。在做下一道习题前，试着自己回答下面的问题:

> 1.  你认为 `if` 对于它下一行的代码做了什么？
> 2.  为什么 `if` 语句的下一行需要缩进？
> 3.  如果不缩进，会怎样？
> 4.  把习题 27 中的其它布尔表达式放到`if 语句`中能不能运行呢？试一下。
> 5.  如果把变量 `people`, `cats`, 和 `dogs` 的初始值改掉，会怎样？

## 常见问题

### Q: `+=`表示什么意思？

> 代码`x += 1`和`x = x + 1` 实现的是一样的功能，但是可以少输入一些字符。你可以称之为“增量”操作符。`-=` 也是相同的，后面你会看到更多的相关解释。