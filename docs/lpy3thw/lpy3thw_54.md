# 练习 50\. 你的第一个网站

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.55.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.55.learn-py3.md)

最后这三个练习会非常难，你可能得多花点时间。第一个练习是要你给你的游戏创建一个简单的网页。在你尝试这个练习之前，你必须已经成功完成了练习 46，正确安装了 pip，并且学会了如何安装软件包以及如何创建项目框架。如果你不记得这些内容，就回到《习题 46》重新复习一遍。

## 安装 Flask

在创建你的第一个网页应用程序之前，你需要安装一个叫做 flask 的“Web 框架”（web framework），所谓的“框架”通常是指“让某件事情做起来更容易的软件包”。在网页应用的世界里，人们创建了各种各样的“网页框架”，用来解决他们在创建网站时碰到的问题，然后把这些解决方案用软件包的方式发布出来，这样你就可以利用它们引导创建你自己的项目了。

在这个练习中，我们会使用 flask 框架，但是可选的框架类型有很多很多，不过在这里我们会使用 flask 框架。你可以先学会它，等到差不多的时候再去接触其它的框架（也可以一直用 flask，因为它真的很好用。）

用 pip 安装 flask:

```py
$ sudo pip install flask
[ sudo ] password for zedshaw:  Downloading/unpacking flask
Running setup.py egg_info for  package flask
Installing collected packages : flask Running setup.py install for flask
Successfully installed flask Cleaning up...
```

这是 Linux 和 macOS 电脑上的操作，如果是 windows，把 `sudo` 去掉，直接输入 `pip install flask` 即可。如果不行的话，回到练习 46，确保你把之前的步骤都做好了。

## 创建一个简单的 “Hello World” 项目

现在你要创建一个非常简单的“Hello World”网页应用，并且会用 flask 来创建项目目录。首先，创建你的项目目录：

```py
$ cd projects
$ mkdir gothonweb
$ cd gothonweb
$ mkdir bin gothonweb tests docs templates
$ touch gothonweb/__init__.py
$ touch tests/__init__.py
```

**ai 酱注：** 这里是 Linux/macOS 的命令，Windows 要换成 `new-item` 来创建新文件，具体可以参考练习 46。

你可以把练习 43 的游戏拿过来，把它做成一个网页应用，这也是为什么我们这个项目叫做 gothonweb。不过在你做之前，我们需要先创建好 flask 的基本应用。把下面这些代码输入到 `app.py` 中：

ex50.py

```py
1  from flask import  Flask
2 app =  Flask(__name__)
3
4  @app.route('/')
5  def hello_world():
6  return  'Hello, World!'
7
8  if __name__ ==  "__main__":
9 app.run()
```

然后像这样运行这个应用：

```py
(lpthw) $ python3.6 app.py
*  Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

最后，用你的浏览器打开 [`localhost:5000/`](http://localhost:5000/) 这个网址，你就可以看到两样东西。第一个是在你的浏览器中，你会看到 Hello, World!, 第二个是在你的终端，你会看到新的输出内容：

```py
(lpthw) $ python3.6 app.py
*  Running on http://127.0.0.1:5000/ (Press CTRL+C to quit) 127.0.0.1 –– [22/Feb/2017 14:28:50] ” GET / HTTP/1.1” 200–
127.0.0.1  ––  [22/Feb/2017  14:28:50]  ” GET /favicon.ico HTTP/1.1”  404–
127.0.0.1  ––  [22/Feb/2017  14:28:50]  ” GET /favicon.ico HTTP/1.1”  404–
```

这些是 flask 为你打印的日志消息，这样你就能看到服务器在正常工作，以及浏览器在屏幕后面都做了什么。这些日志信息可以帮助你调试代码，告诉你哪里出错了。比如，它会说，你的浏览器尝试获取了 `/favicon.ico` ，但是这个文件不存在，所以它返回了 `404 Not Found` 状态码。

我还没解释这种网页运行的原理，因为我想先让你做好准备，这样我可以在之后的两个练习中更好地给你解释。要实现这一点，我得让你用几种不同的方式来把你的 flask 应用拆解开来，然后再重组，这样你就能明白它是如何建立起来的了。

## 发生了什么？

当你的浏览器触发了你的应用，发生了这些事情：

*   浏览器通过网络连接到你自己的电脑，它的名字叫做 localhost，这是一个标准称谓，表示不管我的计算机在网络上叫什么名字，都可以用 localhost 来访问。它用到的网络端口是 5000。

*   连接成功以后，浏览器对 `app.py` 这个应用程序发出了 HTTP 请求(request)，要求访问 `/ URL`，这通常是一个网站的第一个 URL。

*   在 `app.py` 里有一个列表，里边包含了 URL 和类的匹配关系。我们这里只定义了一组匹配，那就是 '/', 'index' 的匹配。它的含义是：如果有人用浏览器访问 `/` 这一级目录， flask 就会找到这个 `def index`，然后用它来处理这个浏览器请求。

*   flask 找到 `def index` 以后，就会调用它来实际处理这个请求。函数运行之后会返回一个字符串，以供 flask 发送给浏览器。

*   最终，flask 处理了这个请求，并将这个响应发送给了浏览器，正如你所看到的那样。

确保你真正理解了以上这些，画一个流程图，展示一下信息是如何从浏览器去到 flask，再到 `def index` ，最后又返回到你的浏览器的。

* * *

**ai 酱注：** 以上这 5 条解释建议大家忽略，因为老肖的解释跟上面 app.py 里面的代码有点对不上，这些解释是旧版书中的解释，因为旧版书的这一节用了不同的方法，所以代码完全不同，但是老肖估计忘了修改这一块内容了。推荐大家去 flask 官网学习一下 [Flask 官方文档](http://docs.jinkan.org/docs/flask/quickstart.html#quickstart)，里面有对这段代码的解释： 1\. 首先，我们导入了 Flask 类。这个类的实例将会是我们的 WSGI （Web 服务器网关接口，Python Web Server Gateway Interface，缩写为 WSGI）应用程序。 2\. 接下来，我们创建一个该类的实例，第一个参数是应用模块或者包的名称。 如果你使用单一的模块（如本例），你应该使用 `**name**` ，因为模块的名称将会因其作为单独应用启动还是作为模块导入而有不同（ 也即是 `'**main**'` 或实际的导入名）。这是必须的，这样 Flask 才知道到哪去找模板、静态文件等等。详情见 Flask 的文档。 3\. 然后，我们使用 `route()` 装饰器告诉 Flask 什么样的 URL 能触发我们的函数。（装饰器可以参考廖雪峰老师的讲解：[装饰器](https://www.liaoxuefeng.com/wiki/1016959663602400/1017451662295584)） 4\. 这个函数的名字也在生成 URL 时被特定的函数采用，这个函数返回我们想要显示在浏览器中的信息。 5\. 最后我们用 `run()` 函数来让应用运行在本地服务器上。 其中`if **name** == '**main**':` 确保服务器只会在该脚本被 Python 解释器直接执行的时候才会运行，而不是作为模块导入的时候。

* * *

## 修正错误

首先，把第 8 行的 greeting 变量赋值删掉，然后刷新浏览器。再用 `CTRL-C` 关掉 flask 再重启，当它再次运行的时候，刷新你的浏览器，你应该会看到一个“Internal Server Error”。回到终端，你会看到这个 (`[VENV]` 是你的 `.venvs/` 目录的路径。)：

**ai 酱注：** 上面的代码中并没有 greeting 变量，我在网上找到了另一个版本的 [LP3THW](http://anyflip.com/fkxr/vvmy/basic/251-300)，其 app.py 的代码跟我们在用的这一版略有区别，def hello_world() 下面是两行内容，第 1 行：`greeting = "World"`，第 2 行：`return f'Hello, {greeting}!'`。大家可以修改一下再按照上面一段内容进行操作。

```py
1.  `(lpthw) $ p`ython3.6 app.py`2.  `*   Running on http://127.0.0.1 :5000/ (Press CTRL+C to quit) [2017-02-22 14:35:54,256] ERROR in app:   Exception on / [GET] Traceback ( most recent call last ):`3.  `File “[VENV]/site-packages/flask/app.py”, line 1982, in wsgi_app`4.  `response = self.full_dispatch_request() File “[VENV]/site-packages/flask/app.py”,`5.  `line 1614, in full_dispatch_request rv = self . handle_user_exception(e)`6.  `File    “[VENV]/site-packages/flask/app.py”, line 1517, in handle_user_exception reraise(exc_type, exc_value, tb)`7.  `File “[VENV]/site—packages/flask/_compat.py”, line 33, in reraise`8.  `raise value`9.  `File “[VENV]/site—packages/flask/app.py”, line 1612, in full_dispatch_request`10.  `rv = self.dispatch_request()`11.  `File “[VENV]/site —packages/flask/app.py”, line 1598, in dispatch_request`12.  `return self.view_f unctionsrule.end point`13.  `File“app.py”, line 8, in index`14.  `return render_template(“index.html”, greeting=greeting) NameError: name 'greeting'  is not defined`15.  `127.0.0.1--[22/Feb/2017 14:35:54] “GET / HTTP/1.1” 500—`
```

这样可以正常运行，不过你也可以在“调试模式”（debugger mode）下运行 Flask。你会得到一个更好的错误页面，以及更多的有用信息。不过，调试模式的问题是它在互联网上运行不够安全，因此，你必须像这样打开它：

```py
(lpthw) $ export FLASK_DEBUG=1
(lpthw) $ python3.6 app.py
*  Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
*  Restarting  with stat
*  Debugger  is active!
*  Debugger pin code:  222—752—342
```

**ai 酱注：** 上面第一行是 linux/macOS 下的命令，windows 系统输入 `set FLASK_DEBUG=1`。（可是我运行之后页面跟原来的一样，并没有多出什么信息来（摊手））

然后，刷新你的浏览器，你就可以得到一个更详细的页面，上面有可以用来调试这个应用的信息，还有一个实时控制台来帮你查找更多的信息。

| 警告！ |
| --- |
| 正是 Flask 实时控制台和升级版的输出信息才让调试模式在网上变得危险。有了这些信息，攻击者可以完全远程控制你的电脑。如果你还没有将你的网页应用放到网上，不要激活调试模式。事实上，我会让激活 `FLASK_DEBUG` 变得很难。当然，你也很容易为了在开发中省掉一个步骤而黑掉这个启动选项，但是这会作用于你的 web 服务器，从而使它变成一个真正的入侵，而不只是你在疲惫夜晚的一个犯懒之举。 |

## 创建基本的模板

你可以把你的 flask 应用拆解开，但是不知你是否注意到。“Hello World”并不是一个很好的 HTML 页面？这是一个网页应用，因此它需要一个适当的 HTML 响应。要实现这一点，你需要创建一个简单的模板，让“Hello World”以一个大的绿色字体呈现。

第一步是创建一个如下的 `templates/index.html` 文件：

index.html

```py
<html>
<head>
<title>Gothons Of Planet Percal #25</title>
</head>
<body>

    7.  ``{% if greeting %}``
    8.  ``I just wanted to say``
    9.  ``<em  style="color: green; font-size:  2em;">{{ greeting }}</em>``
    10.  ``{% else %}``
    11.  ``<em>Hello</em>, world!``
    12.  ``{% endif %}``

    14.  ```</body>```py
    15.  ```</html>```py
```

如果你知道 HTML 是什么，那这些代码你应该看起来很熟悉。如果不知道的话，搜一下 HTML，试着亲手写一些网页，这样你就能知道它是如何运行的。这个 HTML 文件只是一个模板，这意味着 flask 会将你给传给它的变量放进模板中的这些“洞”（holes）里。每个 `$greeting` 所在的地方都代表一个变量，你可以传给这个模板来改变它的内容。

要让你的 app.py 做到这些，你需要添加一些代码来告诉 flask 从哪里加载这个模板以及如何渲染它。把 `app.py` 拿过来，做如下改动：

app.py

```py
1  from flask import  Flask
2  from flask import render_template
3
4 app =  Flask(__name__)
5
6  @app.route("/")
7  def index():
8 greeting =  "Hello World"
9  return render_template("index.html", greeting=greeting)
10
11  if __name__ ==  "__main__":
12 app.run()
```

注意一下新的 `render` 变量。以及我如何改变 `index.GET` 的最后一行，使得它能返回 `render.index()`, 并传入你的 `greeting` 变量。

有了这些之后，在浏览器中重新加载 web 页面，你应该会看到一条绿色的消息。你还应该能够在浏览器的页面上“查看源代码”，以查看它是否是有效的 HTML。

这些可能对你来说有点太快了，所以我会给你解释一下模板的原理：

*   在 app.py 中，你在最开始引入了一个名为 `render_template` 的新函数。

*   这个 `render_template` 知道如何从 `templates/` 目录中加载 `.html` 文件，因为这是一个 Flask 应用的默认设置。

*   在你后面的代码中，当浏览器触发了 `def index` 之后，它没有再返回简单的 `greeting` 字符串，取而代之的是调用了 `render_template`，并且将问候语句作为一个变量传递给它。

*   然后，这个 `render_template` 方法加载了 `templates/index.html` 文件（虽然你没有明确说它是模板）并进行了处理。

*   在这个 `templates/index.html` 文件中，你有了看起来像普通 HTML 的文件，但是还有代码放在两种标记中。一种是 `{% %}`，代表了“可执行代码”（executable code）（if 语句、for 循环等）；另一个是 `{{ }}` ，代表了要被转化为文本并放到 HTML 输出结果中的变量。`{% %}` 可执行代码不会显示在 HTML 中。要了解更多关于模板语言的内容，可以阅读 [Jinja2 文档](http://docs.jinkan.org/docs/jinja2/)。

要深入理解这个过程，你可以修改 `greeting` 变量以及 HTML 模板的内容，看看会有什么效果。然后创建一个叫做 `templates/foo.html` 的模板，并用前面讲到的方法来渲染它。

## 附加练习

*   阅读这个文档：[`flask.pocoo.org/docs/0.12/`](http://flask.pocoo.org/docs/0.12/), 它和 flask 项目是一样的。（**ai 酱注：** 中文版传送门：[Flask 官方文档](http://docs.jinkan.org/docs/flask/)）
*   实验一下你在上述网站看到的所有东西，包括里边的示例代码。
*   阅读一下 HTML5 和 CSS3 相关的东西，自己练习写几个 `.html` 和 `.css` 文件。
*   如果你有一个懂 Django 的朋友，并且愿意帮你的话，你可以试着使用 Django 完成一下习题 50、51、52，看看结果会是什么样子。

## 常见问题

**我好像无法连接 [`localhost:5000/`](http://localhost:5000/)。** 试一下 [`127.0.0.1:5000/`](http://127.0.0.1:5000/) 这个网址。

**flask 和 `web.py` 的区别是什么？** 没有区别。我只是“锁定”（locked）了一个特定版本的 `web.py`，以使它对学生来说保持一致，然后把它叫做 flask。之后的 `web.py` 版本可能跟这一版不一样。

**我找不到 `index.html`（以及其他相关的东西）。** 你可能是先做了 `cd bin/`，然后才运行这个项目。别这样做，所有的命令和指导都假设你处于 `bin/` 的上一级目录中，所以如果你不能输入 `python3.6 app.py`，那你就是处在错误的目录下。

**为什么调用 template 时要写 `greeting=greeting` ？** 这一句并不是赋值给 `greeting` ，而是将一个命名参数传到模板中。这也算是一种赋值，不过只会在模板函数的调用中生效。

**我无法使用 5000 端口。** 可能是哪个杀毒软件占用了这个端口，那就换一个端口。

**安装 flask 时出现 ImportError "No module named web"。** 很有可能是你在系统中安装了多个版本的 Python，而在这里你用了错误的一个。或者由于 pip 版本太旧导致安装没有正确完成。试着卸载并重装 flask 。如果还不行，那就再仔细检查确认自己用了正确版本的 Python。