# 练习 52.开始你的 web 游戏

# 练习 52.开始你的 web 游戏

这本书马上就要结束了。本章的练习对你是一个真正的挑战。当你完成以后，你就可以算是一个能力不错的 Python 初学者了。为了进一步学习，你还需要多读一些书，多写一些程序，不过你已经具备进一步学习的技能了。接下来的学习就只是时间、动力、以及资源的问题了。

在本章习题中，我们不会去创建一个完整的游戏，取而代之的是我们会为《习题 47》中的游戏创建一个“引擎(engine)”，让这个游戏能够在浏览器中运行起来。这会涉及到将《习题 43》中的游戏“重构(refactor)”，将《习题 47》中的架构混合进来，添加自动测试代码，最后创建一个可以运行游戏的 web 引擎。

这是一节很庞大的习题。我预测你要花一周到一个月才能完成它。最好的方法是一点点来，每天晚上完成一点，在进行下一步之前确认上一步有正确完成。

## 重构习题 43 的游戏

你已经在两个练习中修改了`gothonweb`项目，这节习题中你会再修改一次。这种修改的技术叫做“重构(refactoring)”，或者用我喜欢的讲法来说，叫“修修补补(fixing stuff)”。重构是一个编程术语，它指的是清理旧代码或者为旧代码添加新功能的过程。你其实已经做过这样的事情了，只不过不知道这个术语而已。这是写软件过程的第二个自然属性。

你在本节中要做的，是将《习题 47》中的可以测试的房间地图，以及《习题 43》中的游戏这两样东西归并到一起，创建一个新的游戏架构。游戏的内容不会变化，只不过我们会通过“重构”让它有一个更好的架构而已。

第一步是将`ex47/game.py`的内容复制到`gothonweb/map.py`中，然后将 `tests/ex47_tests.py`的内容复制到`tests/map_tests.py`中，然后再次运行 `nosetests`，确认他们还能正常工作。

> **NOTE:**从现在开始我不会再向你展示运行测试的输出了，我就假设你回去运行这些测试，而且知道怎样的输出是正确的。

将《习题 47》的代码拷贝完毕后，你就该开始重构它，让它包含《习题 43》中的地图。我一开始会把基本架构为你准备好，然后你需要去完成`map.py` 和`map_tests.py`里边的内容。

首先要做的是使用`Room`类来构建基本的地图架构：

```py
class Room(object):

    def __init__(self, name, description):
        self.name = name
        self.description = description
        self.paths = {}

    def go(self, direction):
        return self.paths.get(direction, None)

    def add_paths(self, paths):
        self.paths.update(paths)

central_corridor = Room("Central Corridor",
"""
The Gothons of Planet Percal #25 have invaded your ship and destroyed
your entire crew.  You are the last surviving member and your last
mission is to get the neutron destruct bomb from the Weapons Armory,
put it in the bridge, and blow the ship up after getting into an 
escape pod.

You're running down the central corridor to the Weapons Armory when
a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume
flowing around his hate filled body.  He's blocking the door to the
Armory and about to pull a weapon to blast you.
""")

laser_weapon_armory = Room("Laser Weapon Armory",
"""
Lucky for you they made you learn Gothon insults in the academy.
You tell the one Gothon joke you know:
Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr.
The Gothon stops, tries not to laugh, then busts out laughing and can't move.
While he's laughing you run up and shoot him square in the head
putting him down, then jump through the Weapon Armory door.

You do a dive roll into the Weapon Armory, crouch and scan the room
for more Gothons that might be hiding.  It's dead quiet, too quiet.
You stand up and run to the far side of the room and find the
neutron bomb in its container.  There's a keypad lock on the box
and you need the code to get the bomb out.  If you get the code
wrong 10 times then the lock closes forever and you can't
get the bomb.  The code is 3 digits.
""")

the_bridge = Room("The Bridge",
"""
The container clicks open and the seal breaks, letting gas out.
You grab the neutron bomb and run as fast as you can to the
bridge where you must place it in the right spot.

You burst onto the Bridge with the netron destruct bomb
under your arm and surprise 5 Gothons who are trying to
take control of the ship.  Each of them has an even uglier
clown costume than the last.  They haven't pulled their
weapons out yet, as they see the active bomb under your
arm and don't want to set it off.
""")

escape_pod = Room("Escape Pod",
"""
You point your blaster at the bomb under your arm
and the Gothons put their hands up and start to sweat.
You inch backward to the door, open it, and then carefully
place the bomb on the floor, pointing your blaster at it.
You then jump back through the door, punch the close button
and blast the lock so the Gothons can't get out.
Now that the bomb is placed you run to the escape pod to
get off this tin can.

You rush through the ship desperately trying to make it to
the escape pod before the whole ship explodes.  It seems like
hardly any Gothons are on the ship, so your run is clear of
interference.  You get to the chamber with the escape pods, and
now need to pick one to take.  Some of them could be damaged
but you don't have time to look.  There's 5 pods, which one
do you take?
""")

the_end_winner = Room("The End",
"""
You jump into pod 2 and hit the eject button.
The pod easily slides out into space heading to
the planet below.  As it flies to the planet, you look
back and see your ship implode then explode like a
bright star, taking out the Gothon ship at the same
time.  You won!
""")

the_end_loser = Room("The End",
"""
You jump into a random pod and hit the eject button.
The pod escapes out into the void of space, then
implodes as the hull ruptures, crushing your body
into jam jelly.
"""
)

escape_pod.add_paths({
    '2': the_end_winner,
    '*': the_end_loser
})

generic_death = Room("death", "You died.")

the_bridge.add_paths({
    'throw the bomb': generic_death,
    'slowly place the bomb': escape_pod
})

laser_weapon_armory.add_paths({
    '0132': the_bridge,
    '*': generic_death
})

central_corridor.add_paths({
    'shoot!': generic_death,
    'dodge!': generic_death,
    'tell a joke': laser_weapon_armory
})

START = central_corridor 
```

你会发现我们的`Room`类和地图有一些问题：

> 1.  在进入一个房间以前会打印出一段文字作为房间的描述，我们需要将这些描述和每个房间关联起来，这样房间的次序就不会被打乱了，这对我们的游戏是一件好事。这些描述本来是在`if-else`结构中的，这是我们后面要修改的东西。
> 2.  原版游戏中我们使用了专门的代码来生成一些内容，例如炸弹的激活键码，舰舱的选择等，这次我们做游戏时就先使用默认值好了，不过后面的附加题里，我会要求你把这些功能再加到游戏中。
> 3.  我为所有的游戏中的失败结尾写了一个`generic_death`，你需要去补全这个函数。你需要把原版游戏中所有的失败结尾都加进去，并确保代码能正确运行。
> 4.  我添加了一种新的转换模式，以"*"为标记，用来在游戏引擎中实现“catch-all”动作。

等你把上面的代码基本写好以后，接下来就是引导你继续写下去的自动测试的内容`tests/map_test.py`了：

```py
from nose.tools import *
from gothonweb.map import *

def test_room():
    gold = Room("GoldRoom",
                """This room has gold in it you can grab. There's a
                door to the north.""")
    assert_equal(gold.name, "GoldRoom")
    assert_equal(gold.paths, {})

def test_room_paths():
    center = Room("Center", "Test room in the center.")
    north = Room("North", "Test room in the north.")
    south = Room("South", "Test room in the south.")

    center.add_paths({'north': north, 'south': south})
    assert_equal(center.go('north'), north)
    assert_equal(center.go('south'), south)

def test_map():
    start = Room("Start", "You can go west and down a hole.")
    west = Room("Trees", "There are trees here, you can go east.")
    down = Room("Dungeon", "It's dark down here, you can go up.")

    start.add_paths({'west': west, 'down': down})
    west.add_paths({'east': start})
    down.add_paths({'up': start})

    assert_equal(start.go('west'), west)
    assert_equal(start.go('west').go('east'), start)
    assert_equal(start.go('down').go('up'), start)

def test_gothon_game_map():
    assert_equal(START.go('shoot!'), generic_death)
    assert_equal(START.go('dodge!'), generic_death)

    room = START.go('tell a joke')
    assert_equal(room, laser_weapon_armory) 
```

你在这部分练习中的任务是完成地图，并且让自动测试可以完整地检查过整个地图。这包括将所有的`generic_death`对象修正为游戏中实际的失败结尾。让你的代码成功运行起来，并让你的测试越全面越好。后面我们会对地图做一些修改，到时候这些测试将保证修改后的代码还可以正常工作。

## 会话(session)和用户跟踪

在你的 web 程序运行的某个位置，你需要追踪一些信息，并将这些信息和用户的浏览器关联起来。在 HTTP 协议的框架中，web 环境是“无状态(stateless)”的，这意味着你的每一次请求都是独立于其他请求的。如果你请求了页面 A，输入了一些数据，然后点了一个页面 B 的链接，那你在页面 A 输入的数据就全部消失了。

解决这个问题的方法是为 web 程序建立一个很小的数据存储功能，给每个浏览器进程赋予一个独一无二的数字，用来跟踪浏览器所作的事情。这个存储通常用数据库或者存储在磁盘上的文件来实现。这就是所谓的“会话跟踪”和在浏览器中使用 Cookies 以保持用户状态。在`lpthw.web`这个小框架中实现这样的功能是很容易的，以下就是一个这样的例子：

```py
import web

web.config.debug = False

urls = (
    "/count", "count",
    "/reset", "reset"
)
app = web.application(urls, locals())
store = web.session.DiskStore('sessions')
session = web.session.Session(app, store, initializer={'count': 0})

class count:
    def GET(self):
        session.count += 1
        return str(session.count)

class reset:
    def GET(self):
        session.kill()
        return ""

if __name__ == "__main__":
    app.run() 
```

为了实现这个功能，你需要创建一个`sessions/`文件夹作为程序的会话存储位置，创建好以后运行这个程序，然后检查`/count`页面，刷新一下这个页面，看计数会不会累加上去。关掉浏览器后，程序就会“忘掉”之前的位置，这也是我们的游戏所需的功能。有一种方法可以让浏览器永远记住一些信息，不过这会让测试和开发变得更难。如果你回到`/reset/`页面，然后再访问`/count` 页面，你可以看到你的计数器被重置了，因为你已经把会话杀掉了。

你需要花点时间弄懂这段代码，注意会话开始时 `count`的值是如何设为 0 的。另外再看看 `sessions/`下面的文件，看你能不能把它们打开。下面是我把一个 Python 会话打开并且解码的过程：

```py
>>> import pickle
>>> import base64
>>> base64.b64decode(open("sessions/XXXXX").read())
"(dp1\nS'count'\np2\nI1\nsS'ip'\np3\nV127.0.0.1\np4\nsS'session_id'\np5\nS'XXXX'\np6\ns."
>>>
>>> x = base64.b64decode(open("sessions/XXXXX").read())
>>>
>>> pickle.loads(x)
{'count': 1, 'ip': u'127.0.0.1', 'session_id': 'XXXXX'} 
```

所以会话其实就是使用`pickle`和`base64`这些库写到磁盘上的字典。存储和管理会话的方法很多，大概和 Python 的 web 框架那么多，所以了解它们的工作原理并不重要。当然如果你需要调试或者清空会话时，知道点原理还是有用的。

## 创建引擎

你应该已经写好了游戏地图和它的单元测试代码。现在我要求你制作一个简单的游戏引擎，用来让游戏中的各个房间运转起来，从玩家收集输入，并且记住玩家到了那一幕。我们将用到你刚学过的会话来制作一个简单的引擎，让它可以：

> 1.  为新用户启动新的游戏。
> 2.  将房间展示给用户。
> 3.  接受用户的输入。
> 4.  在游戏中处理用户的输入。
> 5.  显示游戏的结果，继续游戏的下一幕，知道玩家角色死亡为止.

为了创建这个引擎，你需要将我们久经考验的`bin/app.py`搬过来，创建一个功能完备的、基于会话的游戏引擎。这里的难点是我会先使用基本的 HTML 文件创建一个非常简单的版本，接下来将由你完成它，基本的引擎是这个样子的：

```py
import web
from gothonweb import map

urls = (
  '/game', 'GameEngine',
  '/', 'Index',
)

app = web.application(urls, globals())

# little hack so that debug mode works with sessions
if web.config.get('_session') is None:
    store = web.session.DiskStore('sessions')
    session = web.session.Session(app, store,
                                  initializer={'room': None})
    web.config._session = session
else:
    session = web.config._session

render = web.template.render('templates/', base="layout")

class Index(object):
    def GET(self):
        # this is used to "setup" the session with starting values
        session.room = map.START
        web.seeother("/game")

class GameEngine(object):

    def GET(self):
        if session.room:
            return render.show_room(room=session.room)
        else:
            # why is there here? do you need it?
            return render.you_died()

    def POST(self):
        form = web.input(action=None)

        # there is a bug here, can you fix it?
        if session.room and form.action:
            session.room = session.room.go(form.action)

        web.seeother("/game")

if __name__ == "__main__":
    app.run() 
```

这个脚本里你可以看到更多的新东西，不过了不起的事情是，整个基于网页的游戏引擎只要一个小文件就可以做到了。这段脚本里最有技术含量的事情就是将会话带回来的那几行，这对于调试模式下的代码重载是必须的，否则每次你刷新网页，会话就会消失，游戏也不会再继续了。

在你运行`bin/app.py`之前，你需要修改`PYTHONPATH`环境变量。不知道什么是环境变量？为了运行一个最基本的 Python 程序，你就得学会环境变量，Python 的这一点确实有点挫。不过没办法，用 Python 的人就喜欢这样：在你的命令行终端，输入:

```py
export PYTHONPATH=$PYTHONPATH:. 
```

如果你用的是 Windows，那就输入:

```py
$env:PYTHONPATH = "$env:PYTHONPATH;." 
```

你只要针对每一个命令行会话界面输入一次就可以了，不过如果你运行 Python 代码时看到了 import 错误，那你就需要去执行一下上面的命令，或者也许是因为你上次执行的 有错才导致 import 错误的。

接下来你需要删掉`templates/hello_form.html`和 `templates/index.html`，然后重新创建上面代码中提到的两个模板。这里是一个非常简单的 `templates/show_room.html` 供你参考：

```py
$def with (room)

<h1> $room.name </h1>

<pre>
$room.description
</pre>

$if room.name == "death":
    <p><a href="/">Play Again?</a></p>
$else:
    <p>
    <form action="/game" method="POST">
        - <input type="text" name="action"> <input type="SUBMIT">
    </form>
    </p> 
```

这就用来显示游戏中的房间的模板。接下来，你需要在用户跑到地图的边界时，用一个 模板告诉用户他的角色的死亡信息，也就是 `templates/you_died.html` 这个模板：

```py
<h1>You Died!</h1>

<p>Looks like you bit the dust.</p>
<p><a href="/">Play Again</a></p> 
```

准备好了这些文件，你现在可以做下面的事情了：

> 1.  让测试代码 `tests/app_tests.py` 再次运行起来，这样你就可以去测试这个游戏。由于会话的存在，你可能顶多只能实现几次点击，不过你应该可以做出一些基本的测试来。
> 2.  删除 `sessions/*`下的文件，再重新运行一遍游戏，确认游戏是从一开始运行起来的。
> 3.  执行 `python bin/app.py` 脚本，试玩一下你的游戏。

你需要和往常一样刷新和修正你的游戏，慢慢修改游戏的 HTML 文件和引擎，直到你实现游戏需要的所有功能为止。

## 你的期末考试

你有没有觉着我一下子给了你超多的信息呢？那就对了，我想要你在学习技能的同时可以有一些可以用来鼓捣的东西。为了完成这节习题，我将给你最后一套需要你自己完成的练习。你将注意到，到目前为止你写的游戏并不是很好，这只是你的第一版代码而已。你现在的任务是通过做这些事让游戏更加完善：

> 1.  修正代码中所有我提到和没提到的 bug，如果你发现了新的 bug，你可以告诉我。
> 2.  改进所有的自动测试，让你可以测试更多的内容，直到你可以不用浏览器就能测到所有的内容为止。
> 3.  让 HTML 页面看上去更美观一些。
> 4.  研究一下网页登录系统，为这个程序创建一个登录界面，这样人们就可以登录这个游戏，并且可以保存游戏高分。
> 5.  完成游戏地图，尽可能地把游戏做大，功能做全。
> 6.  给用户一个“帮助系统”，让他们可以查询每个房间里可以执行哪些命令。
> 7.  为你的游戏添加新功能，想到什么功能就添加什么功能。
> 8.  创建多个地图，让用户可以选择他们想要玩的一张来进行游戏。你的 `bin/app.py` 应该可以运行提供给它的任意的地图，这样你的引擎就可以支持多个不同的游戏。
> 9.  最后，使用你在习题 48 和 49 中学到的东西来创建一个更好的输入处理器。你手头已经有了大部分必要的代码，你只需要改进语法，让它和你的输入表单以及游戏引擎挂钩即可。

祝你好运！

## 常见问题

### Q: 我在游戏中使用了`sessions`，但是我没办法利用`nosetests`来测试它

> 你需要了解 sessions 的机制。`http://webpy.org/cookbook/session_with_reloader`。

### Q: 我遇到报错`ImportError`

> 错误的目录。 错误的 Python 版本。 `PYTHONPATH`没有设置，没有`__init__.py`文件，检查`import`中的拼写错误。