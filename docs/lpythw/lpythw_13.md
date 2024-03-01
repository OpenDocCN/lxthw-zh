# 练习 9.打印, 打印, 打印

# 练习 9.打印, 打印, 打印

现在，你应该明白这本书的模式是用做很多的练习来教会你新知识。我以你可能不明白的代码开始教学，然后在用更多的习题去解释一些概念。即使你现在并不明白，经过大量的练习之后你也能明白了。记录你不明白的地方，然后坚持做练习题，你会收获更多。

```py
# Here's some new strange stuff, remember type it exactly.

days = "Mon Tue Wed Thu Fri Sat Sun"
months = "Jan\nFeb\nMar\nApr\nMay\nJun\nJul\nAug"

print "Here are the days: ", days
print "Here are the months: ", months

print """
There's something going on here.
With the three double-quotes.
We'll be able to type as much as we like.
Even 4 lines if we want, or 5, or 6.
""" 
```

## 你看到的结果

```py
$ python ex9.py
Here are the days:  Mon Tue Wed Thu Fri Sat Sun
Here are the months:  Jan
Feb
Mar
Apr
May
Jun
Jul
Aug

There's something going on here.
With the three double-quotes.
We'll be able to type as much as we like.
Even 4 lines if we want, or 5, or 6. 
```

## 附加题

> 1.  自己检查结果，记录你犯过的错误，并且在下个练习中尽量不犯同样的错误。

## 常见问题

### Q: 为什么当我使用`\n`来换行的时候，`%r`就不生效了？

> 这就是`%r`格式的工作原理；你如何输入的，它就如何打印输出。

### Q:为什么当我在 3 个双引号中间输入空格的时候，会报错？

> 你应该这样写`"""`而不是`" " "`,意思是说每两个双引号之间不能有空格。

### Q:我的错误经常是一些拼写错误，这样是不是很差?

> 在编程初期，大部分错误都是一些简单的错误，比如拼写问题，错别字，或者是将简单的事情搞砸。这很正常，不用担心，但是也要尽量不犯相同的错误。