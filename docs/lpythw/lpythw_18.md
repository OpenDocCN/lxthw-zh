# 练习 14.提示和传递

# 练习 14.提示和传递

这节练习让我们使用`argv`和 `raw_input`一起来向用户提一些特别的问题。下一节习题你会学习如何读写文件，这节练习是下节的基础。在这道习题里我们将用略微不同的方法使用 `raw_input`，让它打出一个简单的 `&gt;` 作为提示符。这和一些游戏中的方式类似，例如 Zork 或者 Adventure 这两款游戏。

```py
from sys import argv

script, user_name = argv
prompt = '> '

print "Hi %s, I'm the %s script." % (user_name, script)
print "I'd like to ask you a few questions."
print "Do you like me %s?" % user_name
likes = raw_input(prompt)

print "Where do you live %s?" % user_name
lives = raw_input(prompt)

print "What kind of computer do you have?"
computer = raw_input(prompt)

print """
Alright, so you said %r about liking me.
You live in %r.  Not sure where that is.
And you have a %r computer.  Nice.
""" % (likes, lives, computer) 
```

我们将用户提示符设置为变量 `prompt`，这样我们就不需要在每次用到 `raw_input` 时重复输入提示用户的字符了。而且如果你要将提示符修改成别的字串，你只要改一个位置就可以了。

是不是非常方便？

## 你看到的结果

当你运行这个脚本时，记住你需要把你的名字赋给这个脚本，让 argv 参数接收到你的名称。

```py
$ python ex14.py zed
Hi zed, I'm the ex14.py script.
I'd like to ask you a few questions.
Do you like me zed?
>  Yes
Where do you live zed?
>  San Francisco
What kind of computer do you have?
>  Tandy 1000

Alright, so you said 'Yes' about liking me.
You live in 'San Francisco'.  Not sure where that is.
And you have a 'Tandy 1000' computer.  Nice. 
```

## 附加题

> 1.  查一下 Zork 和 Adventure 是两个怎样的游戏。看看能不能下载到一版，然后玩玩看。
> 2.  将 `prompt` 变量改成完全不同的内容再运行一遍。
> 3.  给你的脚本再添加一个参数，让你的程序用到这个参数，像你在上一个练习中用到的解包操作`first, second = ARGV`。
> 4.  确认你弄懂了三个引号 `"""` 可以定义多行字符串，而 `%` 是字符串的格式化工具。

## 常见问题

### Q:我遇到一个报错`SyntaxError:invalid syntax`.

> 重申一遍，你要在命令行里执行脚本，而不是在 Python 的解释器里。如果在 python 解析器里再输入`python ex14.py Zed` 一定会出错的，因为你是在 Python 里运行 Python 脚本了。

### Q:我不太明白你说的改变变量`prompt`的值?

> 看到代码的这句了么`prompt = '&gt; '`，改变它的值就是让你修改 `prompt` 为一个不同 于`&gt;` 的值，只是修改一个字符串而已，你已经做过 13 个练习题，这次试试看自己解决这个问题。

### Q:我遇到一个错误信息`need more than 1 value to unpack`.

> 看看“你看到的结果”这部分，并且看看我是怎么运行脚本的。你应该注意我是如何输入命令的，为什么我输入了一个命令行参数？

### Q:怎样在 IDLE 运行程序?

> 不要用 IDLE，现在只用文本编辑器就够了。

### Q:我能给变量`prompt`用双引号吗？

> 当然可以，尽管试试看。

### Q:我遇到一个明明错误: `name 'prompt' is not defined`.

> 你可能是拼写错了 prompt 或者是丢掉了代码的那一行。逐行对比下你和我的代码那里不一样。你遇到这类错误意味着你有拼写错误或者你根本没有定义这个变量。