# 练习 21.函数的返回值

# 练习 21.函数的返回值

你已经学过使用`=`给变量命名，将变量定义为某个数字或者字符串。接下来我们将让你见证更多奇迹。我们要给你演示如何使用`=`以及一个新的 Python 关键字`return`来将变量设置为“一个函数的值”。有一点你需要极其注意，不过我们先来编写下面的脚本吧：

```py
def add(a, b):
    print "ADDING %d + %d" % (a, b)
    return a + b

def subtract(a, b):
    print "SUBTRACTING %d - %d" % (a, b)
    return a - b

def multiply(a, b):
    print "MULTIPLYING %d * %d" % (a, b)
    return a * b

def divide(a, b):
    print "DIVIDING %d / %d" % (a, b)
    return a / b

print "Let's do some math with just functions!"

age = add(30, 5)
height = subtract(78, 4)
weight = multiply(90, 2)
iq = divide(100, 2)

print "Age: %d, Height: %d, Weight: %d, IQ: %d" % (age, height, weight, iq)

# A puzzle for the extra credit, type it in anyway.
print "Here is a puzzle."

what = add(age, subtract(height, multiply(weight, divide(iq, 2))))

print "That becomes: ", what, "Can you do it by hand?" 
```

现在我们创建了自己的加减乘除数学函数： `add`, `subtract`, `multiply`, 以及 `divide`。重要的是函数的最后一行，例如 `add` 的最后一行是 `return a + b`，它实现的功能是这样的:

> 1.  我们调用函数时使用了两个参数： a 和 b 。
> 2.  我们打印出这个函数的功能，这里就是计算加法（adding）
> 3.  接下来我们告诉 Python 让它做某个回传的动作：我们将 `a + b` 的值返回(return)。或者你可以这么说：“我将 a 和 b 加起来，再把结果返回。”
> 4.  Python 将两个数字相加，然后当函数结束的时候，它就可以将 `a + b` 的结果赋予一个变量。

和本书里的很多其他东西一样，你要慢慢消化这些内容，一步一步执行下去，追踪一下究竟发生了什么。为了帮助你理解，本节的附加题将让你解决一个迷题，并且让你学到点比较酷的东西。

## 你看到的结果

```py
$ python ex21.py
Let's do some math with just functions!
ADDING 30 + 5
SUBTRACTING 78 - 4
MULTIPLYING 90 * 2
DIVIDING 100 / 2
Age: 35, Height: 74, Weight: 180, IQ: 50
Here is a puzzle.
DIVIDING 50 / 2
MULTIPLYING 180 * 25
SUBTRACTING 74 - 4500
ADDING 35 + -4426
That becomes:  -4391 Can you do it by hand? 
```

## 附加题

> 1.  如果你不是很确定`return`的功能，尝试自己写几个函数出来，让它们返回一些值。你可以将任何可以放在`=`右边的东西作为一个函数的返回值。
> 2.  这个脚本的结尾是一个迷题。我将一个函数的返回值用作了另外一个函数的参数。我将它们连接一起，就像写数学等式一样。这样可能有些难懂，不过运行一下你就知道结果了。你可以试试看能不能用正常的方法实现和这个表达式一样的功能。
> 3.  一旦你解决了这个迷题，试着修改一下函数里的某些部分，然后看会有什么样的结果。你可以有目的地修改它，让它输出另外一个值。
> 4.  颠倒过来再做一次。写一个简单的等式，使用相同的函数来计算它。

这节习题可能会让你有些头大，不过慢慢来，把它当做一个小游戏，解决这样的迷题也是编程的乐趣之一。后面你还会看到类似的小谜题。

## 常见问题

### Q:为什么 Python 打印公式或函数是反向的？

> 它们并不是真正的反向的, it's "inside out." When you start breaking down the function into separate formulas and function calls you'll see how it works. Try to understand what I mean by "inside out" rather than "backward."

### Q: 怎样使用`raw_input()` 输入我自己的值？

> 还记得 `int(raw_input())`吗? 这样做有一个问题就是你不能输入浮点数，不过你可以使用 `float(raw_input())`来输入。

### Q: 你说的 "写一个公式"是什么意思?

> 试试先写`24 + 34 / 100 - 1023`，再用我们的函数转化一下。现在给你的数学公式加入变量，这样它就变成了一个公式。