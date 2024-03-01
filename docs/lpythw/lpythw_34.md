# 练习 30.Else 和 If

# 练习 30.Else 和 If

上一节习题中你写了一些“if 语句(if-statements)”，并且试图猜出它们实现的是什么功能。在你继续学习之前，我给你解释一下上一节的附加题的答案。上一节的附加习题你做过了吧

> 1.  认为 `if` 对于它下一行的代码做了什么?`If 语句`为代码创建了一个所谓的“分支”， 这有点像选择自己毛线的书籍，你做了选择会打开一个页面，如果做了另一个选择，会到一个不同的方向。`if`语句告诉你的脚本：“如果这个布尔表达式是真的，就执行它下面的语句，否则就跳过这段代码”。
> 
> 1.  为什么 if 语句的下一行需要缩进？代码的最后又一个冒号“：”，是告诉 python 要创建一个新代码块的方式，缩进 4 个空格，是标志那些代码属于这个代码块。这和你在本书的上半部分中定义函数的做法是一样的。
> 
> 1.  如果不缩进，会怎样？如果没有缩进，你的代码将会报错，Python 需要你在输入一行以冒号结尾的代码后有缩进。
> 
> 1.  把习题 27 中的其它布尔表达式放到 if 语句中能不能运行呢？试一下。 可以。而且不管多复杂都可以，虽然写复杂的东西并不是一种好的编程风格。
> 
> 1.  如果把变量`people`,`cats`,和`dogs`的初始值改掉，会怎样？因为你比较的对象是数字，如果你把这些数字改掉的话，某些位置的`if`语句会被演绎为 True，而它下面的代码区段将被运行。你可以试着修改这些数字，然后在头脑里假想一下那一段代码会被运行。

对比咱们的答案，确认自己真正懂得“代码块”的含义。这点对于你下一节的练习很重要，因为你将会写很多的 if 语句。

把下面这段写下来，并让它运行起来：

```py
people = 30
cars = 40
trucks = 15

if cars > people:
    print "We should take the cars."
elif cars < people:
    print "We should not take the cars."
else:
    print "We can't decide."

if trucks > cars:
    print "That's too many trucks."
elif trucks < cars:
    print "Maybe we could take the trucks."
else:
    print "We still can't decide."

if people > trucks:
    print "Alright, let's just take the trucks."
else:
    print "Fine, let's stay home then." 
```

## 你看到的结果

```py
$ python ex30.py
We should take the cars.
Maybe we could take the trucks.
Alright, let's just take the trucks. 
```

## 附加题

> 1.  想一下`elif` 和 `else` 的功能。
> 2.  将 `cars`, `people`, 和 `buses` 的数量改掉，然后追溯每一个 `if` 语句。看看最后会打印出什么来。
> 3.  试着写一些复杂的布尔表达式，例如 `cars &gt; people` 和 `buses &lt; cars`等。
> 4.  给每一行加上注释，解释每一句代码是什么功能。1

## 常见问题

### Q: 如果多个`elif`块为真，会怎样？

> Python 的启动和运行只会针对第一个为真的代码块，所以你说的那种情况，只会执行第一块。