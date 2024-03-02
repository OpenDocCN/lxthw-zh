# 练习 28 布尔练习

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.33.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.33.learn-py3.md)

你上个练习所学的逻辑组合叫做“布尔”逻辑表达（Boolean logic expressions）。布尔逻辑在编程中无处不在。它是数学计算的基础模块，掌握它就跟掌握音乐里面的音阶一样重要。

在这个练习中，你将试着在 Python 中运用你在上个练习中所记忆的逻辑表。给以下每一个逻辑问题写下你认为的答案，要么是 True，要么是 False。等你把答案写下来，再在终端里运行 Python，输入每个逻辑问题，来确认你的答案是否正确。

```py
1.  `1.  True  and  True`2.  `2.  False  and  True`3.  `3.  1  ==  1  and  2  ==  1`4.  `4.  "test"  ==  "test"`5.  `5.  1  ==  1  or  2  !=  1`6.  `6.  True  and  1  ==  1`7.  `7.  False  and  0  !=  0`8.  `8.  True  or  1  ==  1`9.  `9.  "test"  ==  "testing"`10.  `10.  1  !=  0  and  2  ==  1`11.  `11.  "test"  !=  "testing"`12.  `12.  "test"  ==  1`13.  `13.  not  (True  and  False)`14.  `14.  not  (1  ==  1  and  0  !=  1)`15.  `15.  not  (10  ==  1  or  1000  ==  1000)`16.  `16.  not  (1  !=  10  or  3  ==  4)`17.  `17.  not  ("testing"  ==  "testing"  and  "Zed"  ==  "Cool Guy")`18.  `18.  1  ==  1  and  (not  ("testing"  ==  1  or  1  ==  0))`19.  `19.  "chunky"  ==  "bacon"  and  (not  (3  ==  4  or  3  ==  3))`20.  `20.  3  ==  3  and  (not  ("testing"  ==  "testing"  or  "Python"  ==  "Fun"))`
```

我还会教你一个小诀窍来帮你弄明白更复杂的问题。

不论何时，当你看到这些布尔逻辑表达式，你可以通过以下简单的几步来解决它们：

*   把每一个相等性测试（== 或者 !=）替换成真实性测试。

*   先解决圆括号里面的 and/or。

*   找到每一个 not，然后把它反转过来。

*   找到剩余的 and/or，然后解决掉。

*   当你完成的时候，你应该得到 True 或者 False。我会用一个变量来说明：

> 3 != 4 and not ("testing" != "test" or "Python" == "Python")

以下是我进行每一步逻辑运算的过程，最后我得出了一个单一的结果：

1、先解决每一个相等性测试：

> 3 != 4 是 True: True and not ("testing" != "test" or "Python" == "Python"； "testing" != "test" 是 True: True and not (True or "Python" == "Python")； "Python" == "Python": True and not (True or True)；

2、找到圆括号里的每一个 and/or：

> (True or True) 是 True: True and not (True)

3、找到每一个 not，然后把它转换过来：

> not (True) 是 False: True and False

4、找到其他剩余的 and/or 然后解决它们：

> True and False 是 False。

这样我们就完成了这个测试，并且知道结果是 False。

| 警告！ |
| --- |
| 更复杂的测试可能一看非常难。你应该先试试，不要一开始就气馁。我已经让你为做更难的“逻辑练习”做好了准备，只要你坚持下去，弄明白你出错的地方。你可能没办法一下子冒出答案，多多练习，总会达到的。 |

## 你会看到

在你尝试给出所有答案后，这是你可能会在 Python 运行后看到的会话结果：

```py
1.  `$ python3.6`2.  `Python  2.5.1  (r251:54863,  Feb  6  2009,  19:02:12)`3.  `[GCC 4.0.1  (  Apple  Inc  . build 5465)] on darwin`4.  `Type  "help"  ,  "copyright"  ,  "credits"  or  "license"  for more information`5.  `>>>  True  and  True`6.  `True`7.  `>>>  1  ==  1  and  2  ==  2`8.  `True`
```

## 附加练习

*   Python 中有很多类似于 `!=` 和 `==` 的运算符，试着尽可能多地找到这类“比较运算符”（ equality operators），比如 `<` 或者 `<=`。
*   写下这些比较运算符的名字，比如我们把 `!=` 叫做“不等于”。
*   在 Python 中输入新的布尔运算，在你敲下回车之前先把答案说出来，别思考，说出你脑子里第一个冒出来的答案。写下来，然后敲回车。算一算你对了多少，错了多少。
*   记完把纸扔掉，防止你下次再用。

## 常见问题

**为什么 "test" and "test" 返回的是 test，1 and 1 返回的是 1 而不是 True？** Python 和其他很多语言喜欢返回布尔表达式的运算数而不是只是 True 或者 False。这意味着，如果是 False and 1，你会得到第一个运算数（False），如果是 True and 1，你会得到第二个运算数（1），试着玩玩这个。

**`!=` 和 `<>` 有区别吗？** Python 已经不提倡使用 `<>` ，而是更多地使用 `!=`，除此之外，二者没有任何区别。

**有捷径吗？**有，任何包含一个 False 的 and 表达式结果都是 False。任何包含一个 True 的 or 表达式结果都是 True。但是你要掌握处理整个表达式的过程，后面会用到。