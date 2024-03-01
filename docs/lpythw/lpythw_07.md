# 练习 3.数字和数学计算

# 练习 3.数字和数学计算

每一种编程语言都包含处理数字和进行数学计算的方法。不必担心，程序员经常撒谎说他们是多么牛的数学天才，其实他们根本不是。如果他们真是数学天才，他们早就去从事数学相关的行业了，而不是写写广告程序和社交网络游戏。

这节练习里有很多的数学运算符号。我们来看一遍它们都叫什么名字。你要一边写一边念出它们的名字来，直到你念烦了为止。名字如下：

```py
+ plus 加号 
- minus 减号
/ slash 斜杠 除法
* asterisk 星号 乘法
% percent 百分号 模除
< less-than 小于号
> greater-than 大于号
<= less-than-equal 小于等于号
>= greater-than-equal 大于等于号 
```

有没有注意到以上只是些符号，没有运算操作呢？写完下面的练习代码后，再回到上面的列表，写出每个符号的作用。例如`+`是用来做加法运算的。

```py
print "I will now count my chickens:"

print "Hens", 25 + 30 / 6
print "Roosters", 100 - 25 * 3 % 4

print "Now I will count the eggs:"

print 3 + 2 + 1 - 5 + 4 % 2 - 1 / 4 + 6

print "Is it true that 3 + 2 < 5 - 7?"

print 3 + 2 < 5 - 7

print "What is 3 + 2?", 3 + 2
print "What is 5 - 7?", 5 - 7

print "Oh, that's why it's False."

print "How about some more."

print "Is it greater?", 5 > -2
print "Is it greater or equal?", 5 >= -2
print "Is it less or equal?", 5 <= -2 
```

## 你看到的结果

```py
$ python ex3.py
I will now count my chickens:
Hens 30
Roosters 97
Now I will count the eggs:
7
Is it true that 3 + 2 < 5 - 7?
False
What is 3 + 2? 5
What is 5 - 7? -2
Oh, that's why it's False.
How about some more.
Is it greater? True
Is it greater or equal? True
Is it less or equal? False 
```

## 附加题

> 1.使用`#`在代码每一行的前一行为自己写一个注释，说明这一行的作用。2.记得`练习 0`的内容吧？用里边的方法把`Python`运行起来，然后使用刚才学到的运算符号，把 Python 当做计算器玩玩。3.自己找个需要计算的东西，写一个 `.py` 文件把它计算出来。4.有没有发现有些计算结果是”错”的呢？计算结果只有整数，没有小数部分。研究一下这是为什么，搜索一下“浮点数(floating point number)” 是什么东西。5.使用浮点数重写一遍`ex3.py`，让它的计算结果更准确(提示: 20.0 是一个浮点数)。

## 常见问题

### Q: 为什么`%`表示模除而不是“百分号”？

> 这个问题的答案正好就是问什么大部分程序员选择用这个运算符。平时我们把它看做一个“百分号”。在编程计算中，通常把它和`/`一样当做除法的运算符。`%`是一个不同的运算，只是用`%`符号来表示。

### Q: `%`如何运算的？

> 另一种说法是, "X 除以 Y 余 J." 比如, "100 除以 16 余数为 4." `%` 计算的结果就是这个余数。

### Q: 运算符的顺序是怎样的？

> 在美国我们用一个括弧来指定加减乘除的顺序。Python 中也同样遵循这个规律。

### Q: `/`是如何运算的？

> 它只是舍去了小数点后面的部分，比较一下`7.0 / 4.0`和 `7 / 4`,你就会明白其中的不同了。