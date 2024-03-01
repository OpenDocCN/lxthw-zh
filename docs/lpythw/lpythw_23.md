# 练习 19.函数和变量

# 练习 19.函数和变量

函数这个概念也许承载了太多的信息量，不过别担心。只要坚持做这些练习，对照上个练习中的检查点检查一遍这次的联系，你最终会明白这些内容的。

有一个你可能没有注意到的细节，我们现在强调一下：函数里边的变量和脚本里边的变量之间是没有关系的。下面的这个练习可以让你对这一点有更多的思考：

```py
def cheese_and_crackers(cheese_count, boxes_of_crackers):
    print "You have %d cheeses!" % cheese_count
    print "You have %d boxes of crackers!" % boxes_of_crackers
    print "Man that's enough for a party!"
    print "Get a blanket.\n"

print "We can just give the function numbers directly:"
cheese_and_crackers(20, 30)

print "OR, we can use variables from our script:"
amount_of_cheese = 10
amount_of_crackers = 50

cheese_and_crackers(amount_of_cheese, amount_of_crackers)

print "We can even do math inside too:"
cheese_and_crackers(10 + 20, 5 + 6)

print "And we can combine the two, variables and math:"
cheese_and_crackers(amount_of_cheese + 100, amount_of_crackers + 1000) 
```

通过这个练习，你看到我们给函数`cheese_and_crackers`传递很多的参数，然后在函数里把它们打印出来。我们可以在函数里用变量名，可以在函数里做运算，甚至可以将变量和运算结合起来。

从一方面来说，函数的参数和我们的生成变量时用的`=`赋值符类似。事实上，如果你可以用`=`给一个东西命名，你也就可以将其作为参数传递给一个函数。

## 你看到的结果

你应该研究一下脚本的输出，和你想象的结果对比一下看有什么不同。

```py
$ python ex19.py
We can just give the function numbers directly:
You have 20 cheeses!
You have 30 boxes of crackers!
Man that's enough for a party!
Get a blanket.

OR, we can use variables from our script:
You have 10 cheeses!
You have 50 boxes of crackers!
Man that's enough for a party!
Get a blanket.

We can even do math inside too:
You have 30 cheeses!
You have 11 boxes of crackers!
Man that's enough for a party!
Get a blanket.

And we can combine the two, variables and math:
You have 110 cheeses!
You have 1050 boxes of crackers!
Man that's enough for a party!
Get a blanket. 
```

## 附加题

> 1.  倒着将脚本读完，在每一行上面添加一行注解，说明这行的作用。
> 2.  从最后一行开始，倒着阅读每一行，读出所有的重要字符来。
> 3.  自己编至少一个函数出来，然后用 10 种方法运行这个函数。

## 常见问题

### Q: 怎么可能有 10 中方法来运行一个函数？

> 信不信由你,理论上有无数种方法去调用一个函数。看看你对函数、变量、用户输入有多少想象力和创造力。

### Q:有没有一种方法分析一下这个函数是做什么的，这样能让我更方便的理解它？

> 有很多种方法可以做到,但是尽量采用给每行增加注释的方式。另一种方式是大声的读出代码。第三种方式是将代码打印在纸上，并添加图片和注释用来解释代码实现了什么功能。

### Q: 如果我希望用户输入芝士和饼干的数量，我该怎么做？

> 你可以使用`int()`把你从`raw_input()`获取的参数转化为数字。

### Q: 在函数中能否改变变量`cheese_count`和`amount_of_cheese`的值？

> 当然不能, 这些变量是独立的，在函数体之外。 他们被作为零食变量传递给函数是为了保证函数的正常运行，当函数退出的时候，这些临时变量也就消失了。继续学习本书，你会更明白这些。

### Q: 定义一个和函数名相同名字的全局变量是不是不好？

> 当然不好, 如果你这么做了，后面你就搞不清你在说变量还是函数了。 但有时候你可能必须要用相同的名字，否则你可能会遇到一些难题。但是不管怎么说，尽量避开这种做法。

### Q: 函数可以限制参数的传递个数？

> 这取决于你 python 的版本以及你用什么电脑，即使有这个限制的数字也是非常大的。为了使函数方便使用，实际的限制大约时 5 个参数，也就是说当函数参数超过 5 个的时候，函数就会变得不方便使用。

### Q:你能在一个函数中调用另一个函数吗？

> 可以，本书后面有一个制作游戏的例子就是这么做的。