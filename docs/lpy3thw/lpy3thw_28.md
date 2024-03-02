# 练习 24 更多练习

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.29.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.29.learn-py3.md)

快到这部分的尾声了。现在你应该已经有了足够多的 Python 技能来继续学习编程到底是怎么回事儿，但是你应该做更多的练习，这个练习很长，纯粹是为了夯实基础。好好练吧，准确输入，仔细检查。

ex24.py

```py
1  print("Let's practice everything.")
2  print('You\'d need to know \'bout escapes with \\ that do:')
3  print('\n newlines and \t tabs.')
4
5 poem =  """
6   \tThe lovely world
7   with logic so firmly planted
8   cannot discern \n the needs of love
9   nor comprehend passion from intuition
10  and requires an explanation
11  \n\t\twhere there is none.
12  """
13
14  print("--------------")
15  print(poem)
16  print("--------------")
17
18
19 five =  10  -  2  +  3  -  6
    20.  `20  print(f"This should be five: {five}")` 
21
22  def secret_formula(started):
23 jelly_beans = started *  500
24 jars = jelly_beans /  1000
25 crates = jars /  100
26  return jelly_beans, jars, crates
27
28
29 start_point =  10000
30 beans, jars, crates = secret_formula(start_point)
31
32  # remember that this is another way to format a string
33  print("With a starting point of: {}".format(start_point))
34  # it's just like with an f"" string
35  print(f"We'd have {beans} beans, {jars} jars, and {crates} crates.")
36
37 start_point = start_point /  10
38
39  print("We can also do that this way:")
40 formula = secret_formula(start_point)
41  # this is an easy way to apply a list to a format string
42  print("We'd have {} beans, {} jars, and {} crates.".format(*formula))
```

## 你会看到

练习 24 会话

```py
$ python3.6 ex24.py
Let's practice everything.
You'd need to know 'bout escapes with \ that do:
5.  ``newlines and   tabs.``6.  ``--------------``8.  ```The lovely world```py9.  ```with logic so firmly planted cannot discern```py10.  ```the needs of love```py11.  ```nor comprehend passion from intuition```py12.  ```and requires an explanation```py14.  ````where there is none.```py`15.  ```--------------```py16.  ```This should be five: 5```py17.  ```With a starting point of: 10000```py18.  ```We'd have 5000000 beans,  5000.0 jars,  and  50.0 crates.```py19.  ```We can also do that this way:```py20.  ```We'd have 500000.0 beans, 500.0 jars, and 5.0 crates.```py
```

 ``## 附加练习

*   确保你做了检查：从后往前读代码，大声读出来，然后在不明白的地方加上注释。
*   有意打乱这个文件，然后运行，看看你会收到什么样的错误信息，确保你能把它修复好。

## 常见问题

﻿**为什么你给变量叫 `jelly_beans` 但是后面又用的是 `beans` 这个名字？** 这是函数如何运行的一部分。记住，在函数内部变量是暂时的。当你返回它的时候，它可以被分配给一个变量以便之后使用。我只是创建了一个新的变量 `beans` 来保存返回的值。

﻿**你说的从后往前读代码是什么意思？**从最后一行开始，把你的代码跟我的代码进行比较，如果完全一样，就转到上一行，直到你检查到这个文件的第一行。

**这首诗是谁写的？**是我，其实我写的不全是烂诗。``