# 练习 4.变量和命名

# 练习 4.变量和命名

你已经学会了使用 print 语句和算术运算。下一步你要学的是“变量”。在编程中，变量只不过是用来指代某个东西的名字。程序员通过使用变量名可以让他们的程序读起来更像英语。而且因为程序员的记性都不怎么地，变量名可以让他们更容易记住程序的内容。如果他们没有在写程序时使用好的变量名，在下一次读到原来写的代码时他们会大为头疼的。

如果你被这节习题难住了的话，记得我之前教过的：找到不同点、注意细节。

> 1.  给每一行代码加上注释，给自己解释一下这一行的作用。
> 2.  倒着读你的`.py`文件。
> 3.  朗读你的`.py`文件，将每个字符朗读出来。

```py
cars = 100
space_in_a_car = 4.0
drivers = 30
passengers = 90
cars_not_driven = cars - drivers
cars_driven = drivers
carpool_capacity = cars_driven * space_in_a_car
average_passengers_per_car = passengers / cars_driven

print "There are", cars, "cars available."
print "There are only", drivers, "drivers available."
print "There will be", cars_not_driven, "empty cars today."
print "We can transport", carpool_capacity, "people today."
print "We have", passengers, "to carpool today."
print "We need to put about", average_passengers_per_car, "in each car." 
```

> **NOTE:**`space_in_a_car` 中的`_`是下划线。你要自己学会怎样打出这个字符来。这个符号在变量里通常被用作假想的空格，用来隔开单词。

## 你应该看到的结果

```py
$ python ex4.py
There are 100 cars available.
There are only 30 drivers available.
There will be 70 empty cars today.
We can transport 120.0 people today.
We have 90 to carpool today.
We need to put about 3 in each car. 
```

## 附加题

当我第一次写这个程序时我犯了个错误，python 告诉我这样的错误信息：

```py
Traceback (most recent call last):
  File "ex4.py", line 8, in <module>
    average_passengers_per_car = car_pool_capacity / passenger
NameError: name 'car_pool_capacity' is not defined 
```

用自己的话解释一下这个错误信息，解释时记得使用行号，而且要说明原因。

更多的附加题

> 1.我在程序里用了 4.0 作为`space_in_a_car`的值，这样做有必要吗？如果只用 4 会有什么问题?2.记住 4.0 是一个`浮点数`，自己研究一下这是什么意思。浮点数是带有小数点的数字。3.在每一个变量赋值的上一行加上一行注释。4.记住`=`的名字是等于(equal)，它的作用是为东西取名。5.记住`_`是下划线字符(underscore)。6.将`python`作为计算器运行起来，就跟以前一样，不过这一次在计算过程中使用变量名来做计算，常见的变量名有 i, x, j 等等。

## 常见问题

### Q: `=` (单等号)和`==`(双等号)之间的区别?

> `=` (单等号) 用来赋值，`==`(双等号)用来判断等号两边的值是否相等。你会在 27 节习题里学到这些。

### Q: 我们能用`x=100` 代替`x = 100`吗?

> 当然可以, 但是这种写法不好。你应该在操作符的两边加上空格，这样能提高你的代码易读性。

### Q: 在打印输出的时候，怎样进行字符串拼接?

> 你可以这样做: `print "Hey %s there." % "you".`, 以后你会经常这么干。

### Q: "倒着读文件"是什么意思?

> 非常简单.想象你有一个 16 行代码的文件 。从第 16 行开始读，并和我的代码的第 16 行进行比较。然后对第 15 行代码重复上面的操作，直到你倒序的读完整个文件。

### Q: 为什么用`4.0`作为`space_in_a_car`的值?

> 它的主要目的就是引出什么是浮点数。看看附加题部分。