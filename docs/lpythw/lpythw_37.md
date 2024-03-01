# 练习 33.while 循环

# 练习 33.while 循环

接下来是一个更在你意料之外的概念：`while 循环（while-loop）`。while 循环会一直执行它下面的代码片段，直到它对应的布尔表达式为`False`时才会停下来。

你还能跟得上这些术语吧？如果你的某一行是以`:`（冒号）结尾，那就意味着接下来的内容是一个新的代码片段，新的代码片段是需要缩进的。只有将代码用这样的方式格式化，Python 才能知道你的目的。如果你不太明白这一点，就回去看看“if 语句”和“函数”的章节，直到你明白为止。

接下来的练习将训练你的大脑去阅读这些结构化的代码。这和我们将布尔表达式烧录到你的大脑中的过程有点类似。

回到`while` 循环，它所作的和`if`语句类似，也是去检查一个布尔表达式的真假，不一样的是它下面的代码片段不是只被执行一次，而是执行完后再调回到 `while` 所在的位置，如此重复进行，直到`while`表达式为`False`为止。

`While` 循环有一个问题，那就是有时它永远不会结束。如果你的目的是循环到宇宙毁灭为止，那这样也挺好的，不过其他的情况下你的循环总需要有一个结束。

为了避免这样的问题，你需要遵循下面的规定：

> 1.  尽量少用`while-loop`，大部分时候`for-loop`是更好的选择。
> 2.  重复检查你的`while`语句，确定你的布尔表达式最终会变成`False` 。
> 3.  如果不确定，就在 while 循环的结尾打印出你测试的值。看看它的变化。

在这节练习中，你将通过上面的三个检查学会`while-loop` ：

```py
i = 0
numbers = []

while i < 6:
    print "At the top i is %d" % i
    numbers.append(i)

    i = i + 1
    print "Numbers now: ", numbers
    print "At the bottom i is %d" % i

print "The numbers: "

for num in numbers:
    print num 
```

### 你看到的结果

```py
$ python ex33.py
At the top i is 0
Numbers now:  [0]
At the bottom i is 1
At the top i is 1
Numbers now:  [0, 1]
At the bottom i is 2
At the top i is 2
Numbers now:  [0, 1, 2]
At the bottom i is 3
At the top i is 3
Numbers now:  [0, 1, 2, 3]
At the bottom i is 4
At the top i is 4
Numbers now:  [0, 1, 2, 3, 4]
At the bottom i is 5
At the top i is 5
Numbers now:  [0, 1, 2, 3, 4, 5]
At the bottom i is 6
The numbers: 
0
1
2
3
4
5 
```

## 附加题

> 1.  将这个`while`循环改成一个函数，将测试条件`(i &lt; 6)`中的 6 换成一个变量。
> 2.  使用这个函数重写你的脚本，并用不同的数字进行测试。
> 3.  为函数添加另外一个参数，这个参数用来定义第 8 行的加值 `+1` ，这样你就可以让它加任意值了。
> 4.  再使用该函数重写一遍这个脚本。看看效果如何。
> 5.  使用`for-loop`和`range`把这个脚本再写一遍。你还需要中间的加值操作吗？如果不去掉它，会有什么样的结果？

很有可能你会碰到程序跑着停不下来了，这时你只要按着 CTRL 再敲 c (CTRL-c)，这样程序就会中断下来了。

## 常见问题

### Q: for 循环和 while 循环有什么区别？

> for 循环只能对某种事物的集合做循环，而 while 可以进行任何种类的循环。但是，while 循环很容易出错，大部分情况 for 循环也是一个很好的选择。

### Q: 循环好难啊，我怎么才能掌握它？

> 人们不理解循环的主要原因是因为他们不理解代码的“跳跃性”。当一个循环运行的时候，它会执行完循环的代码块，然后从代码块的末尾跳到开头。想象一下，在循环中放一些打印语句，当 Python 运行的时候，看一下变量在这些位置是如何变化的。把打印语句写在循环之前，循环的开头，循环的中间，以及循环结束的位置，研究一下这些输出，再试着理解一下代码是如何跳跃的。