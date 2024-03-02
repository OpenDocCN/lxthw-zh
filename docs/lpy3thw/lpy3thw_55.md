# 练习 51\. 从浏览器获取输入

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.56.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.56.learn-py3.md)

虽然能让浏览器显示“Hello World”是件很激动人心的事情，但是如果能让用户通过表单(form)向你的应用程序提交文本，那就更令人兴奋了。在这个练习中，我们会使用 form 改进你的 web 程序，并且将用户相关的信息保存到他们的“会话(session)”中。

## Web 是如何工作的？

该学点无趣的东西了。在创建 form 前你需要先多学一点关于 web 的工作原理。这里的描述并不完整，但是相当准确，在你的程序出错时，它会帮你找到出错的原因。另外，如果你理解了 form 的应用，那么创建 form 对你来说就会更容易。

我会从一个简单的图示讲起，它向你展示了 web 请求的不同部分，以及信息传递的大致流程：为了方便讲述一个常规请求（request）的流程，我在每条线上面加了字母标签以作区别：

![request 流程.png](img/e21389f3c099b6fe538226d20f97726a.png)

*   你在浏览器输入网址 [`test.com//`](http://test.com//)，它会通过你电脑的网络设备发送请求（线路 A）。

*   你的请求被传送到互联网（线路 B），然后再抵达远程服务器（线路 C），然后我的服务器会接受这个请求。 **ai 酱注：** 这里之所以用“my server”是因为旧版书中，作者举例用的链接是 [`learnpythonthehardway.org/`](http://learnpythonthehardway.org/)，这是作者自己的网站，所以对应也会指向他的服务器。在新版书中，虽然更换了链接，但是作者并没有对这里的表述加以更正。

*   我的服务器接受请求后，我的 web 应用程序就会去处理这个请求（线路 D），然后我的 Python 代码会去运行 `index.GET` 这个“处理程序(handler)”。

*   在代码 return 的时候，我的 Python 服务器就会发出响应(response)，这个响应会再通过线路 D 传递到你的浏览器。

*   运行这个网站的服务器会从线路 D 获得响应，然后服务器将这个网站通过线路 C 传回至互联网。

*   响应通过互联网由线路 B 传至你的计算机，计算机的网卡再通过线路 A 将响应传给你的浏览器。

*   最后，你的浏览器显示了这个响应的内容。

这段描述中有几个术语需要你了解一下，以便你在谈论 web 应用时能够明白并应用它们：

**浏览器（browser）** 这是你几乎每天都会用到的软件。大部分人并不知道它真正的原理，他们只会把它叫作“网”（the Internet）。它的作用其实是接收你输入到地址栏网址(例如[`learnpythonthehardway.org`](http://learnpythonthehardway.org))，然后使用该信息向该网址对应的服务器提出请求。

**地址（address）** 通常这是一个像 [`test.com//`](http://test.com//) 一样的 URL (Uniform Resource Locator，统一资源定位器)，它告诉浏览器该打开哪个网站。前面的 http 指出了你要使用的协议 (protocol)，这里我们用的是“超文本传输协议(Hyper-Text Transport Protocol)”。你还可以试试 [ftp://ibiblio.org/](https://www.zybuluo.com/Standalone/note/ftp:/ibiblio.org) ，这是一个“FTP 文件传输协议(File Transport Protocol)”的例子。`test.com` 这部分是“主机名(hostname)”，也就是一个便于人阅读和记忆的地址，主机名会被匹配到一串叫作“IP 地址”的数字上面，这个“IP 地址”就相当于网络中一台计算机的电话号码，通过这个号码可以访问到这台计算机。最后，URL 后面还可以跟一个路径，就像 [`test.com//book/`](http://test.com//book/) 中的 `/book/` 部分，它对应的是服务器上的某个文件或者某些资源，通过访问这样的网址，你可以向服务器发出请求，然后获得这些资源。网站地址还有很多别的组成部分，不过这些是最主要的。

**连接（connection）** 一旦浏览器知道了你想用的协议(http)、你想访问的服务器([`test.com/`](http://test.com/))、以及该服务器需要获取的资源，它就要创建一个连接。浏览器会让操作系统(Operating System, OS)打开计算机的一个“端口(port)”（通常是 80 端口），端口准备好以后，操作系统会回传给你的程序一个类似文件的东西，它所做的事情就是通过网络传输和接收数据，让你的计算机和 [`test.com/`](http://test.com/) 这个网站所属的服务器之间实现数据交换。当你使用 [`localhost:8080/`](http://localhost:8080/) 访问你自己的站点时，发生的事情其实是一样的，只不过这次你告诉了浏览器要访问的是你自己的计算机(localhost)，要使用的端口不是默认的 80，而是 8080。你还可以直接访问 [`test.com:80/`](http://test.com:80/)，这和不输入端口效果一样，因为 HTTP 的默认端口本来就是 80。

**请求（request）** 你的浏览器通过你提供的地址建立了连接，现在它需要从远端服务器要到它（或你）想要的资源。如果你在 URL 的结尾加了 `/book/`，那你想要的就是 `/book/` 对应的文件或资源，大部分的服务器会直接为你调用 `/book/index.html` 这个文件，不过我们就假装它不存在好了。浏览器为了获得服务器上的资源，它需要向服务器发送一个“请求”。这里我就不讲细节了，你只需要明白，为了得到服务器上的内容，它必须先向服务器发送一个请求才行。有意思的是，“资源”不一定非要是文件。例如当浏览器向你的应用程序提出请求的时候，服务器返回的其实是你的 Python 代码生成的一些东西。

**服务器（server）** 服务器指的是浏览器另一端连接的计算机，它知道如何回应浏览器请求的文件和资源。大部分的 web 服务器只要发送文件就可以了，这也是服务器流量的主要部分。不过你学的是使用 Python 组建一个服务器，这个服务器知道如何接受请求，然后返回用 Python 处理过的字符串。当你使用这种处理方式时，你其实是假装把文件发给了浏览器，其实你用的都只是代码而已。就像你在《练习 50》中看到的，要构建一个“响应”其实也不需要多少代码。

**响应（response）** 这就是你的服务器回复你的请求，发回至浏览器的 HTML（包括 css、javascript 或 images）。以文件响应为例，服务器只要从磁盘读取文件，发送给浏览器就可以了，不过它还要将这些内容包在一个特别定义的“头部信息(header)”中，这样浏览器就会知道它获取的是什么类型的内容。以你的 web 应用程序为例，你发送的其实还是一样的东西，包括 header 也一样，只不过这些数据是你用 Python 代码即时生成的。

这可以算是你能在网上找到的关于浏览器如何访问网站的最快的快速课程了。这个课程应该可以帮你更容易地理解本节的练习，如果你还是不明白，就找找资料多多了解这方面的信息，直到你明白为止。有一个很好的方法，就是你对照着上面的图示，把你在《练习 50》中创建的 web 程序中的内容分成几个部分，让其中的各部分对应到上面的图示中。如果你可以正确地将程序的各部分对应到这个图示，那你就大致明白它的工作原理了。

## 表单（forms）是如何工作的

熟悉“表单”最好的方法就是写一个可以接收表单数据的程序出来，然后看你可以对它做些什么。先将你的 `app.py` 文件修改成下面的样子：

form_test.py

```py
1  from flask import  Flask
2  from flask import render_template
3  from flask import request
4
5 app =  Flask(__name__)
6
7  @app.route("/hello")
8  def index():
9 name = request.args.get('name',  'Nobody')
10
11  if name:
12 greeting = f"Hello, {name}"
13  else:
14 greeting =  "Hello World"
15
16  return render_template("index.html", greeting=greeting)
17
18  if __name__ ==  "__main__":
19 app.run()
```

重启 flask（按 CTRL + C，然后再次运行）确保它再次加载，然后用浏览器访问 [`localhost:5000/hello`](http://localhost:5000/hello)，应该会显示 “I just wanted to say Hello, Nobody.” 接着，把浏览器中的 URL 改为 [`localhost:5000/hello?name=Frank`](http://localhost:5000/hello?name=Frank)，你会看到 “Hello, Frank.” 最后，把 `name=Frank` 这里改成你的名字，它就会对你说 Hello。

让我们拆解一下脚本中的这些变更：

*   我们没有直接为 `greeting` 赋值，而是使用了 `request.args` 从浏览器获取数据。这是一个用键值对（key=value pairs） 来包含表单值的简单字典。
*   然后我用新的 `name` 构建 `greeting`，这句你应该已经很熟悉了。
*   其他的内容和以前是一样的，我们就不再分析了。URL 中还可以包含多个参数。将本例的两个变量改成这样：[`localhost:5000/hello?name=Frank&greet=Hola`](http://localhost:5000/hello?name=Frank&greet=Hola)。然后修改代码，让它像这样获取 `name` 和 `greet`：

```py
greet = request.args.get(  ' greet '  ,  ' Hello '  )
greeting = f"{greet}, {name}"
```

你还应该试着不在 URL 上给出 greet 和 name 参数，只让浏览器访问 [`localhost:5000/hello`](http://localhost:5000/hello)，然后你会看到，`name` 会默认为 “Nobody”，`greet` 会默认为 “Hello”。

## 创建 HTML 表单

在 URL 上传递参数也可以，但就是有点丑，而且对普通用户来说有点难用。你真正想要的是一个“发送表单”（POST form），这是一个特殊的 HTML 文件，里面有一个 `<form>` 标签。这个表单会从用户那里收集信息，然后发送给你的网站，就像你之前做的那样。

让我们来快速创建一个，从中你可以看出它的工作原理。你需要创建一个新的 HTML 文件 templates/hello_form.html：

```py
hello_form.html

    3.  ``<html>``
    4.  ``<head>``
    5.  ``<title>Sample  Web  Form</title>``
    6.  ``</head>``
    7.  ``<body>``

    9.  ```<h1>Fill  Out  This  Form</h1>```py

    11.  ````<form action="/hello" method="POST">```py`
    12.  ```A Greeting:  <input type="text" name="greet">```py
    13.  ```<br/>```py
    14.  ```Your  Name:  <input type="text" name="name">```py
    15.  ```<br/>```py
    16.  ```<input type="submit">```py
    17.  ```</form>```py

    19.  ````</body>```py`
    20.  ```</html>```py
```

 ``然后你需要把 app.py 改成这样：

app.py

```py
1  from flask import  Flask
2  from flask import render_template
3  from flask import request
4
5 app =  Flask(__name__)
6
7  @app.route("/hello", methods=['POST',  'GET'])
8  def index():
9 greeting =  "Hello World"
10
11  if request.method ==  "POST":
12 name = request.form['name']
13 greet = request.form['greet']
14 greeting = f"{greet}, {name}"
15  return render_template("index.html", greeting=greeting)
16  else:
17  return render_template("hello_form.html")
18
19
20  if __name__ ==  "__main__":
21 app.run()
```

改完之后，再次重启 web 应用，像之前一样刷新浏览器。

这次你会看到一个表单，向你获取“A Greeting”和“Your Name.”。当你点击表单上的提交（ Submit ）按钮时，它会给你跟之前一样的问候。不过这次，浏览器上面的 URL 还是 [`localhost:5000/hello`](http://localhost:5000/hello)，哪怕你已经传递了参数。

让这个发挥作用的是 `hello_form.html` 文件中的这一行：`<form action="/hello" method="POST">`。这告诉浏览器：

*   从表单中的各个栏位收集用户输入的数据。
*   使用一种 POST 类型的请求，将这些数据发送给服务器。这是另外一种浏览器请求，它会将表单栏位“隐藏”起来。
*   将这个请求发送至 `/hello` URL，这是由 `action="/hello"` 这部分内容告诉浏览器的。你可以看到这两个 `<input>` 标签是如何和你新代码中的变量名相匹配的。还要注意一下，在 `class index` 里面，我没有用 GET 方法，而是使用了 POST 方法。这个新程序的工作原理如下：

*   你的新请求像之前一样去到了 `index()`，不过现在有一个 if 语句来检查 `request.method` 是 "POST" 还是 "GET" 方法。这样浏览器就能告诉 `app.py` 一个请求是表单提交还是 URL 参数。

*   如果 `request.method` 是 "POST"，程序就会对表单填写和提交的内容进行处理，并返回合适的问候语。

*   如果 `request.method` 是其他东西，那你只要返回 `hello_form.html` 让用户来填写。

作为练习，在 `templates/index.html` 中添加一个链接，让它指向 `/hello`，这样你可以反复填写、提交表单并查看结果。

确认你可以解释清楚这个链接的工作原理，以及它是如何让你实现在 `templates/index.html` 和 `templates/hello_form.html` 之间循环跳转的，还有就是要明白你新修改过的 Python 代码中，运行的是哪一部分代码。

## 创建布局模板(layout template)

在你下一节练习创建游戏的过程中，你需要创建很多的小 HTML 页面。如果你每次都写一个完整的网页，你会很快感觉到厌烦的。幸运的 是你可以创建一个“布局模板”，也就是一种提供了通用的头文件（headers）和脚注（footers）的外壳模板，你可以用它将你所有的其他网页包裹起来。好程序员会尽可能减少重复动作，所以要做一个好程序员，使用布局模板是很重要的。

将 `templates/index.html` 修改为这样：

index_laid_out.html

```py
{%  extends  "layout.html"  %}

    3.  ``{% block content %}``
    4.  ``{%  if greeting %}``
    5.  ``I just wanted to say``
    6.  ``<em style="color: green; font-size: 2em;">{{ greeting }}</em>.``
    7.  ``{%  else  %}``
    8.  ``<em>Hello</em>, world!``
    9.  ``{% endif %}``

    11.  ```{% endblock %}```py
```

 ``然后将 `templates/hello_form.html` 修改为这样：

hello_form_laid_out.html

```py
{%  extends  "layout.html"  %}

    3.  ``{% block content %}``

    5.  ```<h1>Fill  Out  This  Form</h1>```py

    7.  ````<form action="/hello" method="POST">```py`
    8.  ```A Greeting:  <input type="text" name="greet">```py
    9.  ```<br/>```py
    10.  ```Your  Name:  <input type="text" name="name">```py
    11.  ```<br/>```py
    12.  ```<input type="submit">```py
    13.  ```</form>```py

    15.  ````{% endblock %}```py`
```

 ``我们所做的就是把每一个页面顶部和底部反复用到的“boilerplate”（样板）代码去掉。这些被去掉的代码会被放到一个单独的 `templates/layout.html` 文件中，之后，这些反复用到的代码就由 layout.html 来提供了。

修改好之后，创建一个 `templates/layout.html` 文件，内容如下：

layout.html

```py
<html>
<head>
<title>Gothons From Planet Percal #25</title>
</head>
<body>

    7.  ``{% block content %}``

    9.  ```{% endblock %}```py
    10.  ```</body>```py
    11.  ```</html>```py
```

 ``这个文件和普通的模板文件类似，不过它会收到其它模板传递的内容，并将它们“包裹”起来。任何写在这里的内容都无需写在别的模板中了。你的其他 HTML 模板会被插入到 `{% block content %}` 中。Flask 知道要把 `layout.html` 文件用作布局，因为你在模板的顶部放了 `{% extends "layout.html" %}`。

## 为表单撰写自动测试代码

使用浏览器测试 web 程序是很容易的，只要点刷新按钮就可以了。不过毕竟我们是程序员嘛，如果我们可以写一些代码来测试我们的程序，为什么还要重复手动测试呢？接下来你要做的，就是为你的 web 程序写一个小测试。这会用到你在《练习 47》学过的一些东西，如果你不记得的话，可以回去复习一下。

创建一个新文件，并命名为 tests/app_tests.py，其内容如下：

app_tests.py

```py
1  from nose.tools import  *
2  from app import app
3
4 app.config['TESTING']  =  True
5 web = app.test_client()
6
7  def test_index():
8 rv = web.get('/', follow_redirects=True)
9 assert_equal(rv.status_code,  404)
10
11 rv = web.get('/hello', follow_redirects=True)
12 assert_equal(rv.status_code,  200)
13 assert_in(b"Fill Out This Form", rv.data)
14
15 data =  {'name':  'Zed',  'greet':  'Hola'}
16 rv = web.post('/hello', follow_redirects=True, data=data)
17 assert_in(b"Zed", rv.data)
18 assert_in(b"Hola", rv.data)
```

最后，用 `nosetests` 运行这个测试程序，来测试你的 web 应用：

```py
$ nosetests
.
---------------
Ran  1 test in  0.059s OK
```

我在这儿其实是把整个应用都从 `app.py` 模块中引入进来了，然后手动运行它。flask 框架有一个非常简单用来处理请求的 API，它看起来像这样：

```py
data =  {'name':  'Zed',  'greet':  'Hola'}
rv = web.post('/hello', follow_redirects=True, data=data)
```

这意味着你可以用 `post()` 方法发送一个 POST 请求，然后把表单数据作为字典传给它。其他都和测试 `web.get()` 请求一模一样。

在 `tests/app_tests.py` 自动测试脚本中，我首先确认 `/` 返回了一个“404 Not Found”响应，因为这个 URL 其实是不存在的。然后我检查了 `/hello` 在 GET 和 POST 两种请求的情况下都能正常工作。就算你没有弄明白测试的原理，这些测试代码应该是很好读懂的。

花些时间研究一下这个最新版的 web 程序，重点研究一下自动测试的工作原理。确保你理解了将 `app.py` 做为一个模块导入，然后进行自动化测试的流程。这是一个很重要的技巧，它会引导你学到更多东西。

## 附加练习

*   阅读和 HTML 相关的更多资料，然后为你的表单设计一个更好的输出格式。你可以先在纸上设计出来，然后用 HTML 去实现它。
*   这是一道难题，试着研究一下如何进行文件上传，通过网页上传一张图像，然后将其保存到磁盘中。
*   更难的难题，找到 HTTP RFC 文件（讲述 HTTP 工作原理的技术文件），然后努力阅读一下。这是一篇很无趣的文档，不过偶尔你也会用到里边的一些知识。
*   又是一道难题，找人帮你设置一个 web 服务器，例如 Apache、Nginx 或者 thttpd。试着让服务器 serve 一下你创建的 `.html` 和 `.css` 文件。如果失败了也没关系，web 服务器本来就都有点烂。
*   完成上面的任务后休息一下，然后试着多创建一些 web 程序出来。

## 拆解

这里很适合讲一下如何拆解 web 应用。你应该这样做：

*   打开 `FLASK_DEBUG` 会造成多大的损害？注意做这个的时候别把自己电脑搞垮了。

*   假设你没有为表单设置默认参数，哪里会出错？

*   你先检查 `POST` 然后是“其他东西”。你可以用 `curl` 命令行工具生成不同的请求类型。看看会发生什么？```py`````