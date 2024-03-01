# 练习 24.更多的练习

# 练习 24.更多的练习

你离这本书第一部分的结尾已经不远了，你应该已经具备了足够的 Python 基础知识，可以继续学习一些编程的原理了，但你应该做更多的练习。这个练习的内容比较长，它的目的是锻炼你的毅力，下一个习题也差不多是这样的，好好完成它们，做到完全正确，记得仔细检查。

```py
print "Let's practice everything."
print 'You\'d need to know \'bout escapes with \\ that do \n newlines and \t tabs.'

poem = """
\tThe lovely world
with logic so firmly planted
cannot discern \n the needs of love
nor comprehend passion from intuition
and requires an explanation
\n\t\twhere there is none.
"""

print "--------------"
print poem
print "--------------"

five = 10 - 2 + 3 - 6
print "This should be five: %s" % five

def secret_formula(started):
    jelly_beans = started * 500
    jars = jelly_beans / 1000
    crates = jars / 100
    return jelly_beans, jars, crates

start_point = 10000
beans, jars, crates = secret_formula(start_point)

print "With a starting point of: %d" % start_point
print "We'd have %d beans, %d jars, and %d crates." % (beans, jars, crates)

start_point = start_point / 10

print "We can also do that this way:"
print "We'd have %d beans, %d jars, and %d crates." % secret_formula(start_point) 
```

## 你看到的结果

```py
$ python ex24.py
Let's practice everything.
You'd need to know 'bout escapes with \ that do
 newlines and   tabs.
--------------

       The lovely world
with logic so firmly planted
cannot discern
 the needs of love
nor comprehend passion from intuition
and requires an explanation

              where there is none.

--------------
This should be five: 5
With a starting point of: 10000
We'd have 5000000 beans, 5000 jars, and 50 crates.
We can also do that this way:
We'd have 500000 beans, 500 jars, and 5 crates. 
```

## 附加题

> 1.  记得仔细检查结果，从后往前倒着检查，把代码朗读出来，在不清楚的位置加上注释。
> 2.  故意把代码改错，运行并检查会发生什么样的错误，并且确认你有能力改正这些错误。

## 常见问题

### Q:为什么在后面你把 `jelly_beans` 这个变量叫做 `beans`?

> 这是函数如何工作的一部分。记住，在函数中，变量都是临时的.当你返回一个变量的时候，你可以把它赋值给另一个变量。我只是定义了一个叫做‘beans’的新变量去接收返回值。

### Q:你所说的反向阅读代码是什么意思?

> 从最后一行开始阅读。对比你的代码和我的是不是一样。如果确认一样，向上移动一行阅读，直到你读到脚本的第一行为止。

### Q:那首诗是谁写的？

> 我写的。