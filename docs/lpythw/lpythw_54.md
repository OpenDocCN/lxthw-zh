# 练习 50.你的第一个网站

# 练习 50.你的第一个网站

最后的 3 个练习将会很难，你需要在他们身上多花一些时间。第一个练习里你将创建一个简单的 web 版本的游戏。在你开始这节练习以前，你必须已经成功地完成过了《习题 46》的内容，正确安装了 pip，而且学会了如何安装软件包以及如何创建项目骨架。如果你不记得这些内容，就回到《习题 46》重新复习一遍。

## 安装 lpthw.web

在创建你的第一个网页应用程序之前，你需要安装一个“Web 框架”，它的名字叫`lpthw.web`。所谓的“框架”通常是指“让某件事情做起来更容易的软件包”。在网页应用的世界里，人们创建了各种各样的“网页框架”，用来解决他们在创建网站时碰到的问题，然后把这些解决方案用软件包的方式发布出来，这样你就可以利用它们引导创建你自己的项目了。

可选的框架类型有很多很多，不过在这里我们将使用`lpthw.web` 框架。你可以先学会它，等到差不多的时候再去接触其它的框架，不过 `lpthw.web` 本身挺不错的，所以就算你一直使用也没关系。

使用`pip`安装`lpthw.web`：

```py
$ sudo pip install lpthw.web
[sudo] password for zedshaw:
Downloading/unpacking lpthw.web
  Running setup.py egg_info for package lpthw.web

Installing collected packages: lpthw.web
  Running setup.py install for lpthw.web

Successfully installed lpthw.web
Cleaning up... 
```

以上是 Linux 和 Mac OSX 系统下的安装命令，如果你使用的是 Windows，那你只要把`sudo`去掉就可以了。如果你无法正常安装，请回到《习题 46》，确认自己学会了里边的内容。

> **Warning:**其他 Python 程序员会警告你说`lpthw.web`只是另外一个叫做`web.py`的 Web 框架的代码分支(fork)，而`web.py`又包含了太多的“魔法(magic)”在里边。如果他们这么说的话，你告诉他们`Google App Engine`最早用的就是 `web.py`，但没有一个 Python 程序员抱怨过它里边包含了太多的魔法，因为 Google 用它也没啥问题。如果 Google 觉得它可以，那它对你来说也不会差。所以还是回去继续学习吧，他们这些说法与其说是教导你，不如说是拿他们自己的教条束缚你，你还是忽略这些说法好了。

## 写一个简单的“Hello World”项目

现在我们使用`lpthw.web`做一个非常简单的“Hello World”项目出来，首先你要创建一个项目目录：

```py
$ cd projects
$ mkdir gothonweb
$ cd gothonweb
$ mkdir bin gothonweb tests docs templates
$ touch gothonweb/__init__.py
$ touch tests/__init__.py 
```

你最终的目的是把《习题 43》中的游戏做成一个 web 应用，所以你的项目名称叫做`gothonweb`，不过在此之前，你需要创建一个最基本的 `lpthw.web` 应用，将下面的代码放到 `bin/app.py` 中：

```py
import web

urls = (
  '/', 'index'
)

app = web.application(urls, globals())

class index:
    def GET(self):
        greeting = "Hello World"
        return greeting

if __name__ == "__main__":
    app.run() 
```

然后使用下面的方法来运行这个 web 程序：

```py
$ python bin/app.py
http://0.0.0.0:8080/ 
```

如果你这样做：

```py
$ cd bin/   # WRONG! WRONG! WRONG!
$ python app.py  # WRONG! WRONG! WRONG! 
```

那么你就错了。在所有 Python 项目中，都不会用`cd`到下一级目录中去启动服务，你就在最顶层的目录启动服务，这样所有的系统可以访问所有的模块和文件。 去重读习题 46 并理解项目布局和如何使用它。

最后，使用你的网页浏览器，打开 URL `http://localhost:8080/`，你应该看到两样东西，首先是浏览器里显示了 `Hello, world!`，然后是你的命令行终端显示了如下的输出：

```py
$ python bin/app.py
http://0.0.0.0:8080/
127.0.0.1:59542 - - [13/Jun/2011 11:44:43] "HTTP/1.1 GET /" - 200 OK
127.0.0.1:59542 - - [13/Jun/2011 11:44:43] "HTTP/1.1 GET /favicon.ico" - 404 Not Found 
```

这些是`lpthw.web` 打印出的 log 信息，从这些信息你可以看出服务器有在运行，而且能了解到程序在浏览器背后做了些什么事情。这些信息还有助于你发现程序的问题。例如在最后一行它告诉你浏览器试图获取`/favicon.ico`，但是这个文件并不存在，因此它返回的状态码是 `404 Not Found`。

到这里，我还没有讲到任何 web 相关的工作原理，因为首先你需要完成准备工作，以便后面的学习能顺利进行，接下来的两节习题中会有详细的解释。我会要求你用各种方法把你的 lpthw.web 应用程序弄坏，然后再将其重新构建起来：这样做的目的是让你明白运行 lpthw.web 程序需要准备好哪些东西.

## 发生了什么？

在浏览器访问到你的网页应用程序时，发生了下面一些事情：

> 1.  浏览器通过网络连接到你自己的电脑，它的名字叫做`localhost`，这是一个标准称谓，表示的谁就是网络中你自己的这台计算机，不管它实际名字是什么，你都可以使用 localhost 来访问。它使用到的网络端口是 8080。
> 2.  连接成功以后，浏览器对`bin/app.py`这个应用程序发出了 HTTP 请求(request)，要求访问 URL `/`，这通常是一个网站的第一个 URL。
> 3.  在`bin/app.py` 里，我们有一个列表，里边包含了 URL 和类的匹配关系。我们这里只定义了一组匹配，那就是 `'/', 'index'` 的匹配。它的含义是：如果有人使用浏览器访问 / 这一级目录，`lpthw.web` 将找到并加载 `class index`，从而用它处理这个浏览器请求。
> 4.  现在 `lpthw.web` 找到了`class index`，然后针对这个类的一个实例调用了 `index.GET` 这个方法函数。该函数运行后返回了一个字符串，以供`lpthw.web` 将其传递给浏览器。
> 5.  最后`lpthw.web` 完成了对于浏览器请求的处理，将响应(response)回传给浏览器，于是你就看到了现在的页面。

确定你真的弄懂了这些，你需要画一个流程图，来理清信息是如何从浏览器传递到`lpthw.web`，再到`index.GET`，再回到你的浏览器的。

## 修正错误

第一步，把第 11 行的`greeting`变量赋值删掉，然后刷新浏览器。你应该会看到一个错误页面，你可以通过这一页丰富的错误信息看出你的程序崩溃的原因是什么。当然你已经知道出错的原因是`greeting`的赋值丢失了，不过 `lpthw.web`还是会给你一个挺好的错误页面，让你能找到出错的具体位置。试试在这个错误页面上做以下操作：

> 1.  检查每一段`Local vars`输出（用鼠标点击它们），追踪里边提到的变量名称，以及它们是在哪些代码文件中用到的。
> 2.  阅读`Request Information` 一节，看看里边哪些知识是你已经熟悉了的。Request 是浏览器发给你的 `gothonweb`应用程序的信息。这些知识对于日常网页浏览没有什么用处，但现在你要学会这些东西，以便写出 web 应用程序来。3.试着把这个小程序的别的位置改错，探索一下会发生什么事情。`lpthw.web` 的会把一些错误信息和堆栈跟踪(stack trace)信息显示在命令行终端，所以别忘了检查命令行终端的信息输出。

## 创建基本的模板文件

你已经试过用各种方法把这个 lpthw.web 程序改错，不过你有没有注意到“Hello World”不是一个好 HTML 网页呢？这是一个 web 应用，所以需要一个合适的 HTML 响应页面才对。为了达到这个目的，下一步你要做的是将“Hello World”以较大的绿色字体显示出来。

第一步是创建一个`templates/index.html`文件，内容如下：

```py
$def with (greeting)

<html>
    <head>
        <title>Gothons Of Planet Percal #25</title>
    </head>
<body>

$if greeting:
    I just wanted to say <em style="color: green; font-size: 2em;">$greeting</em>.
$else:
    <em>Hello</em>, world!

</body>
</html> 
```

如果你学过 HTML 的话，这些内容你看上去应该很熟悉。如果你没学过 HTML，那你应该去研究一下，试着用 HTML 写几个网页，从而知道它的工作原理。不过我们这里的 HTML 文件其实是一个“模板(template)”，如果你向模板提供一些参数，`lpthw.web` 就会在模板中找到对应的位置，将参数的内容填充到模板中。例如每一个出现 `$greeting`的位置，`$greeting`的内容都会被替换成对应这个变量名的参数。

为了让你的`bin/app.py`处理模板，你需要写一写代码，告诉`lpthw.web` 到哪里去找到模板进行加载，以及如何渲染(render)这个模板，按下面的方式修改你的 app.py：

```py
import web

urls = (
  '/', 'Index'
)

app = web.application(urls, globals())

render = web.template.render('templates/')

class Index(object):
    def GET(self):
        greeting = "Hello World"
        return render.index(greeting = greeting)

if __name__ == "__main__":
    app.run() 
```

特别注意一下`render`这个新变量名，注意我修改了`index.GET` 的最后一行，让它返回了`render.index()`，并且将`greeting` 变量作为参数传递给了这个函数。

改好上面的代码后，刷新一下浏览器中的网页，你应该会看到一条和之前不同的绿色信息输出。你还可以在浏览器中通过“查看源文件(View Source)”看到模板被渲染成了标准有效的 HTML 源代码。

这么讲也许有些太快了，我来详细解释一下模板的工作原理吧：

> 1.  在`bin/app.py`里面你添加了一个叫做`render`的新变量，它本身是一个 `web.template.render`对象。
> 2.  你将`templates/` 作为参数传递给了这个对象，这样就让`render` 知道了从哪里去加载模板文件。
> 3.  在你后面的代码中，当浏览器一如既往地触发了`index.GET` 以后，它没有再返回简单的`greeting`字符串，取而代之的是你调用了 `render.index`，而且将问候语句作为一个变量传递给它。
> 4.  这个`render_template`函数可以说是一个“魔法函数”，它看到了你需要的是`index.html`，于是就跑到`templates/`目录下，找到名字为`index.html` 的文件，然后就把它渲染(render)一遍（叫“转换一遍”也可以）。
> 5.  在`templates/index.html`文件中，你可以看到初始定义一行中说这个模板需要使用一个叫`greeting`的参数，这和函数定义中的格式差不多。另外和 Python 语法一样，模板文件是缩进敏感的，所以要确认自己弄对了缩进。
> 6.  最后，你让`templates/index.html`去检查`greeting`这个变量，如果这个变量存在的话，就打印出变量的内容，如果不存在的话，就会打印出一个默认的问候信息。

要深入理解这个过程，你可以修改 greeting 变量以及 HTML 模板的内容，看看会有什么效果。然后创建一个叫做`templates/foo.html` 的模板，并且使用一个新的`render.foo()`去渲染它。从这个过程你也可以看出， `render` 调用的函数名称只要跟 `templates/`下的 `.html` 文件名匹配到，这个 HTML 模板就可以被渲染到了。

## 附加题

> 1.  阅读`http://webpy.org/` 里边的文档，它其实和`lpthw.web` 是同一个项目。
> 2.  实验一下你在上述网站看到的所有的东西，包括里边的代码示例。
> 3.  阅读以下 HTML5 和 CSS3 相关的东西，自己练习着写几个 `.html` 和 `.css 文件`。
> 4.  如果你有一个懂 Django 朋友可以帮你的话，你可以试着使用 Django 完成一下习题 50、51、52，看看结果会是什么样子的。

## 常见问题

### Q: 我好想无法连接到`http://localhost:8080/`

> 那么试试访问`http://127.0.0.1:8080/`

### Q: `lpthw.web` 和 `web.py`有什么区别？

> 没有区别。我只是在特定版本“锁定”`web.py`，以使它对所有学生都是一样的，然后再命名为`lpthw.web`，上一个版本的`web.py`可能就不同于这一版本。

### Q: 我的代码找不到`index.html`(或者其他文件)

> 你可能是先执行了`cd bin/`，不要执行这一句，所有的命令都应该在`bin/`的上一级目录执行，所以如果你不能执行`python bin/app.py`,说明你在错误的目录上。

### Q: 当我们调用模板的时候，为什么要执行`greeting=greeting`赋值操作

> 你并没有给`greeting`赋值，你只是给模板设定一个命名参数。这是声明的一种，但它只影响调用模板的功能。

### Q: 我的电脑上不能使用 8080 端口

> 你可能有一个杀毒程序占用了这个端口，试试别的端口。

### Q: 安装`lpthw.web` 时，我遇到报错信息`ImportError "No module named web"`

> 你可能安装了多个版本的 Python 并且正在使用一个错误的版本，或者你是因为使用了一个旧版本的`pip`，导致安装没有成功，试着先卸载`lpthw.web`，在重装一次，如果还没有解决问题，再次确认下你是否使用了正确的 Python 版本。