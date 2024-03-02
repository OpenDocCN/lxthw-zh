# 练习 52 创建你的 web 游戏

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.57.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.57.learn-py3.md)

这本书马上就要结束了。这节练习对你来说是个真正的挑战。当你完成以后，你就可以算是一个能力不错的 Python 初学者了。为了进一步学习，你还需要多读一些书，多写一些程序，不过你已经具备进一步学习的能力了。接下来的学习就只是时间、动力、以及资源的问题了。

在本节练习中，我们不会去创建一个完整的游戏，而是要为《练习 47》中的游戏创建一个“引擎(engine)”，让这个游戏能够在浏览器中运行起来。这会涉及到将《习题 43》中的游戏“重构(refactor)”，将《习题 47》中的架构混合进来，添加自动测试代码，最后创建一个可以运行游戏的 web 引擎。

这个练习会非常庞大。我预测你要花一周到一个月时间才能完成它。你最好一点一点来，每天晚上完成一点，在进行下一步之前确保上一步已经正确完成。

## 重构《练习 43》的游戏

你已经在两个练习中修改了 gothonweb 项目，这节习题中你会再修改一次。这种修改的技术叫做“重构（refactoring）”，或者用我喜欢的讲法来说，叫“修修补补（fixing stuff）”。重构是一个编程术语，它指的是清理旧代码或者为旧代码添加新功能的过程。你其实已经做过这样的事情了，只不过不知道这个术语而已。这是写软件过程的第二个自然属性。

你在本节中要做的，是将《习题 47》中的可以测试的房间地图，以及《习题 43》中的游戏这两样东西归并到一起，创建一个新的游戏架构。游戏的内容不会发生变化，只不过我们会通过“重构”让它有一个更好的架构而已。

第一步是将 `ex47/game.py` 的内容复制到 `gothonweb/planisphere.py` 中，然后将 `tests/ex47_tests.py` 的内容复制到 `tests/planisphere_tests.py` 中，然后再次运行 nosetests，确保他们还能正常工作。“planisphere”这个词是地图的同义词，用这个名字是为了避免 Python 内置的 map 函数。同义词典（Thesaurus）是个好东西，要善于利用它。

| 警告！ |
| --- |
| 从现在开始，我不会再向你展示我运行测试的输出结果了。我假设你会自己去做测试，所以测试是个前提，除非你遇到了错误。 |

当你把《练习 47》的代码复制好之后，你就该开始重构它了，让它包含《习题 43》中的地图。我一开始会把基本架构为你准备好，然后你需要去完成 `planisphere.py` 和 `planisphere_tests.py` 这两个文件里边的内容。

首先要做的是使用 Room 类来构建基本的地图架构：

planisphere.py

```py
1  class  Room(object):
2
3  def __init__(self, name, description):
4  self.name = name
5  self.description = description
6  self.paths =  {}
7
8  def go(self, direction):
9  return  self.paths.get(direction,  None)
10
11  def add_paths(self, paths):
12  self.paths.update(paths)
13
14
15 central_corridor =  Room("Central Corridor",
16  """
17  The Gothons of Planet Percal #25 have invaded your ship and destroyed
18  your entire crew. You are the last surviving member and your last
19  mission is to get the neutron destruct bomb from the Weapons Armory, put
20  it in the bridge, and blow the ship up after getting into an escape pod.
21
22  You're running down the central corridor to the Weapons Armory when a
23  Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown
24  costume flowing around his hate filled body. He's blocking the door to
25  the Armory and about to pull a weapon to blast you.
26  """)
27
28
29 laser_weapon_armory =  Room("Laser Weapon Armory",
30  """
31  Lucky for you they made you learn Gothon insults in the academy. You
32  tell the one Gothon joke you know: Lbhe zbgure vf fb sng, jura fur fvgf
33  nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr. The Gothon stops, tries
34  not to laugh, then busts out laughing and can't move. While he's
35  laughing you run up and shoot him square in the head putting him down,
36  then jump through the Weapon Armory door.
37
38  You do a dive roll into the Weapon Armory, crouch and scan the room for
39  more Gothons that might be hiding. It's dead quiet, too quiet. You
40  stand up and run to the far side of the room and find the neutron bomb
41  in its container. There's a keypad lock on the box and you need the
42  code to get the bomb out. If you get the code wrong 10 times then the
43  lock closes forever and you can't get the bomb. The code is 3 digits.
44  """)
45
46
47 the_bridge =  Room("The Bridge",
48  """
49  The container clicks open and the seal breaks, letting gas out. You
50  grab the neutron bomb and run as fast as you can to the bridge where you
51  must place it in the right spot.
52
53  You burst onto the Bridge with the netron destruct bomb under your arm
54  and surprise 5 Gothons who are trying to take control of the ship. Each
55  of them has an even uglier clown costume than the last. They haven't
56  pulled their weapons out yet, as they see the active bomb under your arm
57  and don't want to set it off.
58  """)
59
60
61 escape_pod =  Room("Escape Pod",
62  """
63  You point your blaster at the bomb under your arm and the Gothons put
64  their hands up and start to sweat. You inch backward to the door, open
65  it, and then carefully place the bomb on the floor, pointing your
66  blaster at it. You then jump back through the door, punch the close
67  button and blast the lock so the Gothons can't get out. Now that the
68  bomb is placed you run to the escape pod to get off this tin can.
69
70  You rush through the ship desperately trying to make it to the escape
71  pod before the whole ship explodes. It seems like hardly any Gothons
72  are on the ship, so your run is clear of interference. You get to the
73  chamber with the escape pods, and now need to pick one to take. Some of
74  them could be damaged but you don't have time to look. There's 5 pods,
75  which one do you take?
76  """)
77
78
79 the_end_winner =  Room("The End",
80  """
81  You jump into pod 2 and hit the eject button. The pod easily slides out
82  into space heading to the planet below. As it flies to the planet, you
83  look back and see your ship implode then explode like a bright star,
84  taking out the Gothon ship at the same time. You won!
85  """)
86
87
88 the_end_loser =  Room("The End",
89  """
90  You jump into a random pod and hit the eject button. The pod escapes
91  out into the void of space, then implodes as the hull ruptures, crushing
92  your body into jam jelly.
93  """
94  )
95
96 escape_pod.add_paths({
97  '2': the_end_winner,
98  '*': the_end_loser
99  })
100
101 generic_death =  Room("death",  "You died.")
102
103 the_bridge.add_paths({
104  'throw the bomb': generic_death,
105  'slowly place the bomb': escape_pod
106  })
107
108 laser_weapon_armory.add_paths({
109  '0132': the_bridge,
110  '*': generic_death
111  })
112
113 central_corridor.add_paths({
114  'shoot!': generic_death,
115  'dodge!': generic_death,
116  'tell a joke': laser_weapon_armory
117  })
118
119 START =  'central_corridor'
120
121  def load_room(name):
122  """
123     There is a potential security problem here.
124     Who gets to set name? Can that expose a variable?
125     """
126  return globals().get(name)
127
128  def name_room(room):
129  """
130     Same possible security problem. Can you trust room?
131     What's a better solution than this globals lookup?
132     """
133  for key, value in globals().items():
134  if value == room:
135  return key
```

你会发现我们的 Room 类和地图有一些问题：

*   我们必须把放在 if-else 语句中的文本在进入一个房间之前打印出来，作为每个房间的一部分。这就意味着你不能把 planisphere 打乱，这很好。你要在这个练习中慢慢修复它。

*   原版游戏中我们使用了专门的代码来生成一些内容，例如炸弹的激活键码，舰舱的选择等，这次我们做游戏时就先使用默认值好了，不过后面的附加练习里，我会要求你把这些功能再加到游戏中。

*   我为游戏中的所有失败结尾写了一个 `generic_death`，你需要去补全这个函数。你需要把原版游戏中所有的失败结尾都加进去，并确保代码能正确运行。

*   我添加了一种新的转换模式，以"*"为标记，用来在游戏引擎中实现“catch-all”动作。

等你把上面的代码基本写好以后，接下来就是引导你继续写下去的自动测试的内容 `tests/planisphere_test.py`：

planisphere_tests.py

```py
1  from nose.tools import  *
2  from gothonweb.planisphere import  *
3
4  def test_room():
5 gold =  Room("GoldRoom",
6  """This room has gold in it you can grab. There's a
7       door to the north.""")
8 assert_equal(gold.name,  "GoldRoom")
9 assert_equal(gold.paths,  {})
10
11  def test_room_paths():
12 center =  Room("Center",  "Test room in the center.")
13 north =  Room("North",  "Test room in the north.")
14 south =  Room("South",  "Test room in the south.")
15
16 center.add_paths({'north': north,  'south': south})
17 assert_equal(center.go('north'), north)
18 assert_equal(center.go('south'), south)
19
20  def test_map():
21 start =  Room("Start",  "You can go west and down a hole."
22 west =  Room("Trees",  "There are trees here, you can go east.")
23 down =  Room("Dungeon",  "It's dark down here, you can go up.")
24
25 start.add_paths({'west': west,  'down': down})
26 west.add_paths({'east': start})
27 down.add_paths({'up': start})
28
29 assert_equal(start.go('west'), west)
30 assert_equal(start.go('west').go('east'), start)
31 assert_equal(start.go('down').go('up'), start)
32
33  def test_gothon_game_map():
34 start_room = load_room(START)
35 assert_equal(start_room.go('shoot!'), generic_death)
36 assert_equal(start_room.go('dodge!'), generic_death)
37
38 room = start_room.go('tell a joke')
39 assert_equal(room, laser_weapon_armory)
```

你在这部分练习中的任务是完成这个地图，并且让自动测试可以完整地检查过整个地图。这包括将所有的 `generic_death` 对象修正为游戏中实际的失败结尾。让你的代码成功运行起来，并让你的测试越全面越好。后面我们会对地图做一些修改，到时候这些测试将保证修改后的代码还可以正常工作。

## 创建一个引擎

你应该让你的游戏地图正常运行，并对它进行良好的单元测试。我现在想让你做一个简单的小游戏引擎，它将运行房间、收集来自玩家的输入，并跟踪玩家在游戏中的位置。我们将使用你刚刚学会的会话来创建一个简单的游戏引擎，这个引擎会做这些事情：

*   为新用户开启一个新游戏。

*   为用户展示房间。

*   从用户获取输入。

*   通过游戏运行用户的输入。

*   呈现结果，并继续运行，直至用户挂掉。

要做到这些，你需要使用你一直在写的可靠的 app.py，来创建一个运行良好的、基于会话的游戏引擎。问题是，我需要做一个非常简单的基本 HTML 文件，它将由你来完成它。这是基础引擎：

app.py

```py
1  from flask import  Flask, session, redirect, url_for, escape, request
2  from flask import render_template
3  from gothonweb import planisphere
4
5 app =  Flask(__name__)
6
7  @app.route("/")
8  def index():
9  # this is used to "setup" the session with starting value
10 session['room_name']  = planisphere.START
11  return redirect(url_for("game"))
12
13  @app.route("/game", methods=['GET',  'POST'])
14  def game():
15 room_name = session.get('room_name')
16
17  if request.method ==  "GET":
18  if room_name:
19 room = planisphere.load_room(room_name)
20  return render_template("show_room.html", room=room)
21  else:
22  # why is there here? do you need it?'
23  return render_template("you_died.html")
24  else:
25 action = request.form.get('action')
26
27  if room_name and action:
28 room = planisphere.load_room(room_name)
29 next_room = room.go(action)
30
31  if  not next_room:
32 session['room_name']  = planisphere.name_room
33  else:
34 session['room_name']  = planisphere.name_room
35
36  return redirect(url_for("game"))
37
38
39  # YOU SHOULD CHANGE THIS IF YOU PUT ON THE INTERNET
40 app.secret_key =  'A0Zr98j/3yX R~XHH!jmN]LWX/,?RT'
41
42  if __name__ ==  "__main__":
43 app.run()
```

这个脚本中有更多的新东西，但神奇的是，这个小文件是一个完全基于 web 的游戏引擎。在运行 `app.py` 之前，需要更改 PYTHONPATH 环境变量。不知道那是什么？我知道这有点枯燥，但你必须学习这是什么来运行基本的 Python 程序，没办法，用 Python 的人就喜欢这样。

在你的终端输入：

```py
export PYTHONPATH=$PYTHONPATH:.
```

在 Windows 的 PowerShell 中输入：

```py
$env:PYTHONPATH =  "$env:PYTHONPATH;."
```

你只要针对每一个命令行会话界面输入一次就可以了，不过如果你运行 Python 代码时看到了 import error，或者你输入错误，那就需要再去执行一下上面的命令。

接下来你需要删掉 `templates/hello_form.html` 和 `templates/index.html`，并创建两个前面代码中提到的模板。这是一个非常简单的 `templates/show_room.html`：

show_room.html

```py
1. {%  extends  "layout.html"  %}

3.  {% block content %}

5.  <h1>  {{ room.name }}  </h1>

7.  <pre>
8.  {{ room.description }}
9.  </pre>

11.  {%  if room.name in  ["death",  "The End"]  %}
12.  <p><a href="/">Play  Again?</a></p>
13.  {%  else  %}
14.  <p>
15.  <form action="/game" method="POST">
16.  -  <input type="text" name="action">  <input type="SUBMIT">
17.  </form>
18.  </p>
19.  {% endif %}

21.  {% endblock %}
```

这是在游戏中显示房间的模板。接下来你需要一个模板来告诉用户他们已经死了，以防他们意外地去到地图的结尾，也就是 templates/you_die .html：

you_died.html

```py
1.  <h1>You Died!</h1>

3.  <p>Looks like you bit the dust.</p>
4.  <p><a  href="/">Play Again</a></p>
```

这些都弄好了之后，你可以这样做：

*   让 `tests/app_tests.py` 再次运行来测试这个游戏。因为有会话，所以你只需要在游戏里点几下就行。不过，你应该能做一些基本操作。
*   运行 `python3.6 app.py` 脚本来玩一下这个游戏。你需要和往常一样刷新和修正你的游戏，慢慢修改游戏的 HTML 文件和引擎，直到你实现游戏需要的所有功能为止。

## 你的期末考试

你有没有觉着我一下子给了你超多的信息呢？那就对了，我想要你在学习技能的同时可以有一些可以用来鼓捣的东西。为了完成这节习题，我会给你最后一套需要你自己完成的练习。你应该注意到，到目前为止你写的游戏并不是很好，这只是你的第一版代码而已。你现在的任务是让游戏更加完善，实现下面的这些功能：

*   修正代码中所有我提到和没提到的 bug，如果你发现了新的 bug，可以告诉我。
*   改进所有的自动测试，让你可以测试更多的内容，直到你可以不用浏览器就能测到所有的内容为止。
*   让 HTML 页面看上去更美观一些。
*   研究一下网页登录系统，为这个程序创建一个登录界面，这样人们就可以登录这个游戏，并且可以保存游戏高分。
*   完成游戏地图，尽可能地把游戏做大，功能做全。
*   给用户一个“帮助系统”，让他们可以查询每个房间里可以执行哪些命令。
*   为你的游戏添加任何你能想到的新功能。
*   创建多个地图，让用户可以选择他们想要玩的一张来进行游戏。你的 `app.py` 应该可以运行提供给它的任意的地图，这样你的引擎就可以支持多个不同的游戏。
*   最后，使用你在练习 48 和 49 中学到的东西来创建一个更好的输入处理器。你手头已经有了大部分必要的代码，你只需要改进语法，让它和你的输入表单以及游戏引擎挂钩即可。祝你好运！

## 常见问题

**我在游戏中用了 session，但不能用 nosetests 测试。** 阅读 Flask 测试文档（Flask Testing Documentation）中的“其他测试技巧”（Other Testing Tricks），了解关于在游戏中创建“假会话”（fake sessions）的信息。

**我收到了一个 `ImportError`。** 可能是以下情况中的一种或几种： 错误的目录，错误的 Python 版本，没有设置 PYTHON-PATH，没有 **init**.py 文件，以及（或者）import 中存在拼写错误。