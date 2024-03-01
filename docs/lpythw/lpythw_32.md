# 练习 28.布尔表达式

# 练习 28.布尔表达式

上一节学到的逻辑组合的正式名称是“布尔逻辑表达式(boolean logic expression)”。在编程中，布尔逻辑可以说是无处不在。它们是计算机运算的基础和重要组成部分，掌握它们就跟学音乐掌握音阶一样重要。

在这节练习中，你将在 python 里使用到上节学到的逻辑表达式。先为下面的每一个逻辑问题写出你认为的答案，每一题的答案要么为`True`要么为`False`。写完以后，你需要将 python 运行起来，把这些逻辑语句输入进去，确认你写的答案是否正确。

```py
True and True
False and True
1 == 1 and 2 == 1
"test" == "test"
1 == 1 or 2 != 1
True and 1 == 1
False and 0 != 0
True or 1 == 1
"test" == "testing"
1 != 0 and 2 == 1
"test" != "testing"
"test" == 1
not (True and False)
not (1 == 1 and 0 != 1)
not (10 == 1 or 1000 == 1000)
not (1 != 10 or 3 == 4)
not ("testing" == "testing" and "Zed" == "Cool Guy")
1 == 1 and (not ("testing" == 1 or 1 == 0))
"chunky" == "bacon" and (not (3 == 4 or 3 == 3))
3 == 3 and (not ("testing" == "testing" or "Python" == "Fun")) 
```

在本节结尾的地方我会给你一个理清复杂逻辑的技巧。

所有的布尔逻辑表达式都可以用下面的简单流程得到结果：

> 1.  找到相等判断的部分 (`==` 或者 `!=`)，将其改写为其最终值 (`True` 或 `False`)。
> 2.  找到括号里的 `and/or`，先算出它们的值。
> 3.  找到每一个`not`，算出他们反过来的值。
> 4.  找到剩下的 `and/or`，解出它们的值。
> 5.  等你都做完后，剩下的结果应该就是 `True` 或者 `False` 了。

下面我们以 20 行的逻辑表达式演示一下：

```py
3 != 4 and not ("testing" != "test" or "Python" == "Python") 
```

接下来你将看到这个复杂表达式是如何逐级解为一个单独结果的：

> 1.  > 解出每一个等值判断:
> 
> > a. `3 != 4` 为 `True`: `True and not ("testing" != "test" or "Python" == "Python")`b. `"testing" != "test"` 为 `True`: `True and not (True or "Python" == "Python")`c. `"Python" == "Python"`为`True`: `True and not (True or True)`
> 
> 1.  > 找到括号中的每一个`and/or`:
> 
> > a. `(True or True)` 为 True: `True and not (True)`
> 
> 1.  找到每一个 `not` 并将其逆转:> > a. `not (True)` 为 False: `True and False`
> 
> 1.  找到剩下的 `and/or`，解出它们的值:> > a. `True and False` 为 `False`

这样我们就解出了它最终的值为 False.

> **Warning:**复杂的逻辑表达式一开始看上去可能会让你觉得很难。而且你也许已经碰壁过了，不过别灰心，这些“逻辑体操”式的训练只是让你逐渐习惯起来，这样后面你可以轻易应对编程里边更酷的一些东西。只要你坚持下去，不放过自己做错的地方就行了。如果你暂时不太能理解也没关系，弄懂的时候总会到来的。

## 你看到的结果

以下内容是在你自己猜测结果以后，通过和 python 对话得到的结果：

```py
$ python
Python 2.5.1 (r251:54863, Feb  6 2009, 19:02:12)
[GCC 4.0.1 (Apple Inc. build 5465)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> True and True
True
>>> 1 == 1 and 2 == 2
True 
```

## 附加题

> 1.  Python 里还有很多和`!=`、 `==` 类似的操作符. 试着尽可能多地列出 Python 中的等价运算符。例如 `&lt;` 或者 `&lt;=` 。
> 2.  写出每一个等价运算符的名称。例如 `!=` 叫 “not equal（不等于）”。
> 3.  在 python 中测试新的布尔操作。在敲回车前你需要喊出它的结果。不要思考，凭自己的第一感就可以了。把表达式和结果用笔写下来再敲回车，最后看自己做对多少，做错多少。
> 4.  把习题 3 那张纸丢掉，以后你不再需要查询它了。

## 常见问题

### Q: 为什么`"test" and "test"` 返回 `"test"`以及`1 and 1` 返回 `1` 而不是 `True`?

> python 和很多语言可以返回布尔表达式中的一个操作数，而不仅仅是真或假。这意味着如果你计算`False and 1` 你会得到表达式的第一个操作数 (False) ，但是如果你计算`True and 1`的时候，你得到它的第二个操作数(1)。试一试吧。

### Q:`!=`和 `&lt;&gt;`有什么不同吗?

> Python 已经声明赞成使用`!=`而弃用`&lt;&gt;`所以尽量使用`!=`吧。其他的应该没有区别了。

### Q:有没有捷径去判断布尔表达式的值?

> 有的。任何的`and`表达式包含一个`False`结果就是`False`,任何`or`表达式有一个`True`结果就是`True`，你就可以在此处得到结果，但要确保你能处理整个表达式，因为后面这是一个很有用的技能。