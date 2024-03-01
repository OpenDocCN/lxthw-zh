# 练习 5.更多的变量和打印

# 练习 5.更多的变量和打印

我们现在要输入更多的变量并且把它们打印出来。这次我们将使用一个叫“格式化字符串(format string)”的东西. 每一次你使用`"` 把一些文本引用起来， 你就建立了一个字符串。字符串是程序将信息展示给人的方式。你可以打印它们，可以将它们写入文件，还可以将它们发送给网站服务器，很多事情都是通过字符串交流实现的。

字符串是非常好用的东西，所以在这节练习中你将学会如何创建包含变量内容的字符串。使用专门的格式和语法把变量的内容放到字符串里，相当于来告诉 `python`：“嘿，这是一个格式化字符串，把这些变量放到那几个位置。”

一样的，即使你读不懂这些内容，只要一字不差地输入就可以了。

```py
my_name = 'Zed A. Shaw'
my_age = 35 # not a lie
my_height = 74 # inches
my_weight = 180 # lbs
my_eyes = 'Blue'
my_teeth = 'White'
my_hair = 'Brown'

print "Let's talk about %s." % my_name
print "He's %d inches tall." % my_height
print "He's %d pounds heavy." % my_weight
print "Actually that's not too heavy."
print "He's got %s eyes and %s hair." % (my_eyes, my_hair)
print "His teeth are usually %s depending on the coffee." % my_teeth

# this line is tricky, try to get it exactly right
print "If I add %d, %d, and %d I get %d." % (
    my_age, my_height, my_weight, my_age + my_height + my_weight) 
```

> **Warning:**如果你使用了非 ASCII 字符而且碰到了编码错误，记得在最顶端加一行`# -- coding: utf-8 --`。

## 你应该看到的结果

```py
$ python ex5.py
Let's talk about Zed A. Shaw.
He's 74 inches tall.
He's 180 pounds heavy.
Actually that's not too heavy.
He's got Blue eyes and Brown hair.
His teeth are usually White depending on the coffee.
If I add 35, 74, and 180 I get 289. 
```

## 附加题

> 1.修改所有的变量名字，把它们前面的`my_`去掉。确认将每一个地方的都改掉，不只是你使用`=`赋值过的地方。2.试着使用变量将英寸和磅对应转换成厘米和千克。不要直接键入答案。使用 Python 的计算功能来完成。3.在网上搜索所有的 Python 格式化字符。4.试着使用更多的格式化字符。例如 `%r`就是是非常有用的一个，它的含义是“不管什么都打印出来”。

## 常见问题

### Q:我可以定义一个类似`1 = 'Zed Shaw'`的变量吗?

> 不可以，`1`不是一个合法的变量名.变量需要以字母开头 ，比如`a1`才是正确的变量命名。

### Q:这些字符`%s`, `%r`, `%d`是做什么的?

> 它们都是“格式化字符串”，你继续学习下去，就会学到关于它们更多的知识。它们告诉 Python 用后面的变量值代替字符串中的符号`%s`。那么什么是“格式化字符串呢”？ 我也说不清楚。教你学会编程有一个难题就是想要理解我在说什么，你必须先学会怎样编程。解决这个难题的办法就是先按照我的要求做我让你做的事情，后面会慢慢解释。如果你遇到一些类似的问题，你可以先记下来，后面我会慢慢解答。

### Q:怎样生成一个浮点数?

> 你可以像这样`round(1.7333)` 使用函数`round()`。

### Q:我遇到在这个报错信息:`'str' object is not callable.`

> 你可能忘记在字符串以及变量之间输入`%`。

### Q:为什么这个练习对我没有意义?

> 用你自己的数据修改脚本中的数字，看起来挺奇怪的，但是这些真实的信息能让这个练习更加真实，而且，你才刚刚开始学习，确实也不会有太大的意义，坚持做更多的练习题，你会有所收获。