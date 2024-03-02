# 练习 43\. 面向对象的分析和设计基础

> 原文：[`www.bookstack.cn/read/LearnPython3TheHardWay/spilt.48.learn-py3.md`](https://www.bookstack.cn/read/LearnPython3TheHardWay/spilt.48.learn-py3.md)

这个练习我想说一下当你想要用 Python 创建一个东西，尤其是面向对象编程的时候，过程是怎样的。我说的“过程”指的是我会给出一些有序的步骤，但你也不用生搬硬套，因为它们也不一定适用每一个问题。它们只不过是为很多编程问题提供一个很好的开端，而不是解决这类问题的唯一方法，只是你可以参考的其中一种方法。

过程如下：

*   把问题写或者划下来。

*   提炼出关键概念，并进行研究。

*   为这些概念创建一个类的层级和对象关系图。

*   写下这些类的代码，并测试运行。

*   重复和改进。

这是一种“自上而下”的方式，它从非常抽象、松散的想法开始，然后慢慢提炼，直到想法变得具体，可以通过代码来实现。

我会先从写下问题开始，尽可能地写下我所能想到的点。可能我还会画一两张图表、地图之类的，甚至会给我自己写一系列邮件来阐述这个问题。这样能让我针对这个问题把一些关键的概念表达出来，并且探索出关于该问题我可能已经掌握的东西。

然后我会过一遍这些笔记、图表以及描述，从其中抽象出关键概念。这里有一个小技巧：把你所写所画的东西里面所有的名词和动词列一个表出来，然后写下它们之间是如何相互关联的。这种方法让我得到了一个关于下一步的类、对象和函数名的列表。我拿着这个概念列表，研究其中我不明白的点，如果我需要的话，对其进行改进。

一旦我有了这个概念列表，我就创造了一个简单的概念框架，以及它们作为类是如何相互关联的。你可以经常列你的名词表，然后问自己“这个跟其他的概念名词类似吗？也就是说，它们有共同的父类吗？有的话应该叫什么？”重复这个过程直到你得到一个类的层级结构，可能就是一个简单的树状图或者示意图。然后把所有的动词挑出来，看看它们能不能作为每个类的函数名，然后把它们放到你的树状图里面。

等类的层级结构梳理清楚之后，我会坐下来，写一些基本的代码框架，只是一些类和它们的函数，没有其他东西。然后我会写一些测试代码，跑一下，看这些类有没有意义以及能不能正常运行。有时我会先写测试代码，有时候就是一小段测试，一小段代码，再一小段测试，以此类推，直到我把整个程序构建起来。

最后，我会重复这个过程，并且在运行的过程中不断精简，在添加更多应用之前让代码更简洁明了。如果我在某个特定环节因为一个概念或者我没有预料到的问题而卡壳，我会坐下来，只运行这一部分，直到把问题弄明白之后再继续。

我现在要通过一个游戏引擎和一个游戏练习来过一遍这个过程。

## 一个简单的游戏引擎分析

我要制作的这个游戏叫做“来自 25 号行星的哥顿人”（Gothons from Planet Percal #25），它是一个小型太空冒险游戏。因为我满脑子都是这个概念，我就去探索这个想法，然后思考如何把这个游戏做出来。

### 43.1.1 写或画出这个问题

我会写一小段关于这个游戏的文字：

“外星人入侵了一艘宇宙飞船，我们的英雄必须穿过迷宫般的房间打败他们，这样他才能逃到逃生舱去到下面的星球。游戏更像是 Zork 之类的文字冒险游戏，并且有着很有意思的死亡方式。这款游戏的引擎会运行一张满是房间或场景的地图。当玩家进入游戏时，每个房间都会打印自己的描述，然后告诉引擎下一步该运行地图中的哪个房间。”

这时我有了一个关于这个游戏以及它如何运行的好想法，所以现在我要描述一下每个场景：

**死亡（Death）**：玩家死的时候，会非常有意思。 **中央走廊（Central Corridor）**：这是起点，已经有一个哥顿人站在那里，在继续之前，玩家必须用一个笑话来击败他。 **激光武器军械库（Laser Weapon Armory）**：这是英雄在到达逃生舱之前用中子弹炸毁飞船的地方。这里有一个键盘，英雄必须猜出数字。 **桥（The Bridge）**：另一个和哥顿人战斗的场景，英雄在这里放置了炸弹。 **逃生舱（Escape Pod）**：英雄逃脱的地方，前提是他猜出正确的逃生舱。

到这一步我可能会画一幅映射图，或者为每个房间写更多的描述——反正就是当我探究这个问题的时候，任何我脑子里冒出的想法。

### 43.1.2 抽取关键概念并予以研究

我现在有足够的信息来提取其中的名词，并分析他们的类层级结构。首先，我会做一个所有名词的列表：


+    Alien（外星人）


+    Player（玩家）


+    Ship（飞船）


+    Maze（迷宫）


+    Room（房间）


+    Scene（场景）


+    Gothon（哥特人）


+    Escape Pod（逃生舱）


+    Planet（行星）


+    Map（地图）


+    Engine（引擎）


+    Death（死亡）


+    Central Corridor（中央走廊）


+    Laser Weapon Armory（激光武器军械库）


+    The Bridge（桥）

我可能还会浏览一遍所有的动词，看它们适不适合作为函数名，但是我会先暂时跳过这一步。

现在你可能也会研究一下每个概念以及任何你不明白的东西。比如，我会玩几个同类型的游戏，确保我知道它们是如何工作的。我可能还会研究船是如何设计的或者炸弹是怎么用的。还有一些技术性问题，比如如何把游戏状态储存在数据库中。当我完成这些研究，我可能会基于这些新信息从第一步开始，重新写我的描述，并做概念提取。

### 43.1.3 为这些概念创建类的层级结构和对象地图

我通过询问“什么与其他东西类似?”、“什么基本上就是另一个东西的另一个词?”来把我已经有的东西转换成类的层级结构。

很快我就发现“房间”（“Room”）和“场景”（“Scene”）基本上是同一种东西，取决于我想用它们来做什么。在这个游戏中我选择用“场景”。然后我意识到所有特定的房间比如“中央走廊”其实就是“场景”。我还发现“死亡”（“Death”）也可以说是场景，这确认了我选择“场景”而不是“房间”的正确性，因为你可以说“死亡”是一种场景，但如果说它是一个“房间”就有点奇怪了。“迷宫”（“Maze”）和“地图”（“Map”）也基本上是同一种东西，我会选择用“地图”，因为我更常用它。我不想做一个战斗系统，所以我会暂时忽略“外星人”（“Alien”）和“玩家”（“Player”）这两个东西，先保存起来以备后用。“行星”（“Planet”）也可以是另一种场景，而不是其他特定的东西。

经过上述思考过程，我开始创建一个看起来像这样的类的层级结构：

*   Map
*   Engine
*   Scene
    *   Death
    *   Central Corridor
    *   Laser Weapon Armory
    *   The Bridge
    *   Escape Pod

然后我会浏览一遍，基于我描述里面的东西，想想看每个类下面需要些什么动作。例如，我从描述里知道，我需要一种方式来“运行”这个引擎，从地图“到达下一个场景”，到达“开场”，并“进入”一个场景，我会像这样把这些动作加上：

*   Map – next_scene – opening_scene
*   Engine – play
*   Scene – enter
    *   Death
    *   Central Corridor
    *   Laser Weapon Armory
    *   The Bridge
    *   Escape Pod

注意我只把“enter”放在了“场景”下面，所有“场景”下面的东西都会继承这个动作，需要随后再重写。

### 43.1.4 编写类代码并通过测试来运行

一旦我有了这个类和函数的树状图，我在我的编辑器里面打开一个源文件，试着写它们的代码。通常我就是把树状图里的东西复制粘贴到源文件里，然后把它们编辑成类。下面是它们最开始的样子，文件最后放了一个小测试：

ex43_classes.py

```py
1  class  Scene(object):
2
3  def enter(self):
4  pass
5
6
7  class  Engine(object):
8
9  def __init__(self, scene_map):
10  pass
11
12  def play(self):
13  pass
14
15  class  Death(Scene):
16
17  def enter(self):
18  pass
19
20  class  CentralCorridor(Scene):
21
22  def enter(self):
23  pass
24
25  class  LaserWeaponArmory(Scene):
26
27  def enter(self):
28  pass
29
30  class  TheBridge(Scene):
31
32  def enter(self):
33  pass
34
35  class  EscapePod(Scene):
36
37  def enter(self):
38  pass
39
40
41  class  Map(object):
42
43  def __init__(self, start_scene):
44  pass
45
46  def next_scene(self, scene_name):
47  pass
48
49  def opening_scene(self):
50  pass
51
52
53 a_map =  Map('central_corridor')
54 a_game =  Engine(a_map)
55 a_game.play()
```

在这个文件中你可以看到，我只是复制了层级结构中我想要的东西，并在最后加上了一些测试代码来运行，看这个基本结构能不能成立。在这个练习后面的几部分，你会填上剩余的代码，让它像游戏描述中那样运行。

### 43.1.5 重复和改进

过程的最后一步准确来说不是一个步骤，而像是一个 while 循环。你不可能一次完成这个过程。相反，你会再次回顾整个过程，并根据你从后续步骤中学到的信息对其进行改进。有时我会进入第三步，然后意识到我需要再回到第一步和第二步，那我就会停下来，回到前面去做。有时我会灵光一闪，跳到最后，把脑子里的解决方案代码敲出来，然后再回过头来做前面的步骤，以确保我涵盖了所有可能的情况。

在这个过程中你需要注意的另一个问题是，它不仅仅是你在一个单一层面上做的事，而是当你遇到一个特定的问题时，你可以在每个层面上做的事情。假设我不知道怎么写 `Engine.play` 这个方法。我可以停下来，把整个过程专注在这一个函数上来弄明白代码应该怎么写。

## 自上而下 vs 自下而上

这个过程通常被称为“自上而下”，因为它从最抽象的概念（上）开始，然后一直向下到实际的应用。我希望你能从现在开始分析这本书里遇到的问题时使用我刚才描述的这个过程，但是你应该知道编程中还有另一种解决问题的方式，那就是，从写代码开始，然后逐渐“上升”到抽象的概念，这种方式被称为“自下而上”。它的步骤大致如下：

*   从问题中拿出一小部分，开始写简单的能运行的代码。

*   然后用类和自动化测试来把代码改进地更正式一些。

*   抽象出你所使用的关键概念，试着探究一下它们。

*   针对正在发生的事情写一段描述。

*   回过头去继续改进代码，也可能把之前写的删掉重新开始。

*   转到这个问题的其他部分，然后重复以上步骤。

这个过程只有在你对编程已经比较熟练并且面对问题能够自然使用编程思维的情况下才会更好，同时，当你知道整个工程的一小部分、却对全局概念的信息掌握不全的时候，这个方法也很好用。你可以将整个过程拆解成很多小块，然后边写代码边探索，这样可以帮助你一点一点地钻研这个问题，直到整个问题都得到解决。但是，请记住，你的解决方案很可能会曲折而怪异，所以我才把回顾、研究以及基于你所学到的东西对代码进行改进和清理这些步骤加入到我的过程描述中。

## “来自 25 号行星的哥顿人”游戏代码

停！接下来我要向你展示针对之前的问题我最终的解决方，但是我想让你直接跳进去开始敲代码，我希望你自己先基于描述粗略地写出代码框架，然后试着让它运行，一旦你有了你的解决方案，你再回来看我是怎么做的。

我会把最终的 ex43.py 拆成几个部分分别解释，而不是直接把所有代码一次全部给你。

ex43.py

```py
1  from sys import  exit
2  from random import randint
3  from textwrap import dedent
```

这是游戏所需库的基本引入。唯一的新东西是从 textwrap 模块导入 dedent 函数。这个函数将帮助我们使用 `"""` （三引号）字符串来编写我们的房间描述。它就是简单地从字符串的行首删除空白。如果没有这个函数，使用 `"""` 样式字符串就会失败，因为它们在屏幕上缩进的程度与 Python 代码相同。

ex43.py

```py
1  class  Scene(object):
2
3  def enter(self):
4  print("This scene is not yet configured.")
5  print("Subclass it and implement enter().")
6  exit(1)
```

正如你在框架代码中看到的，我有一个基类 Scene，它具有所有场景都具有的公共功能。在这个简单的程序中，它们不会做太多的工作，只是向你演示如何创建基类。

ex43.py

```py
1  class  Engine(object):
2
3  def __init__(self, scene_map):
4  self.scene_map = scene_map
5
6  def play(self):
7 current_scene =  self.scene_map.opening_scene()
8 last_scene =  self.scene_map.next_scene('finished')
9
10  while current_scene != last_scene:
11 next_scene_name = current_scene.enter()
12 current_scene =  self.scene_map.next_scene(next_scene_name)
13
14  # be sure to print out the last scene
15 current_scene.enter()
```

我还有 Engine 类。你可以看到我已经在使用 `Map.opening_scene` 和 `Map.next_scene` 这两个方法了。因为我已经提前计划好了，所以可以在写出 Map 类之前就把这些方法写下来并用起来。

ex43.py

```py
1  class  Death(Scene):
2
3 quips =  [
4  "You died. You kinda suck at this.",
5  "Your Mom would be proud...if she were smarter.",
6  "Such a luser.",
7  "I have a small puppy that's better at this.",
8  "You're worse than your Dad's jokes."
9 
10  ] 
11 
12  def enter(self):
13  print(Death.quips[randint(0, len(self.quips)-1)])
14  exit(1)
```

我的第一个场景很反常地设置为了 Death，主要是想向你展示你可以写的最简单的场景。

```py
1  class  CentralCorridor(Scene):
2
3  def enter(self):
4  print(dedent("""
5           The Gothons of Planet Percal #25 have invaded your ship and
6           destroyed your entire crew. You are the last surviving
7           member and your last mission is to get the neutron destruct
8           bomb from the Weapons Armory, put it in the bridge, and
9           blow the ship up after getting into an escape pod.
10
11          You're running down the central corridor to the Weapons
12          Armory when a Gothon jumps out, red scaly skin, dark grimy
13          teeth, and evil clown costume flowing around his hate
14          filled body. He's blocking the door to the Armory and
15          about to pull a weapon to blast you.
16          """))
17
18 action = input("> ")
19
20  if action ==  "shoot!":
21  print(dedent("""
22              Quick on the draw you yank out your blaster and fire
23              it at the Gothon. His clown costume is flowing and
24              moving around his body, which throws off your aim.
25              Your laser hits his costume but misses him entirely.
26              This completely ruins his brand new costume his mother
27              bought him, which makes him fly into an insane rage
28              and blast you repeatedly in the face until you are
29              dead. Then he eats you.
30              """))
31  return  'death'
32
33  elif action ==  "dodge!":
34  print(dedent("""
35              Like a world class boxer you dodge, weave, slip and
36              slide right as the Gothon's blaster cranks a laser
37              past your head. In the middle of your artful dodge
38              your foot slips and you bang your head on the metal
39              wall and pass out. You wake up shortly after only to
40              die as the Gothon stomps on your head and eats you.
41              """))
42  return  'death'
43
44  elif action ==  "tell a joke":
45  print(dedent("""
46              Lucky for you they made you learn Gothon insults in
47              the academy. You tell the one Gothon joke you know:
48              Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr,
49              fur fvgf nebhaq gur ubhfr. The Gothon stops, tries
50              not to laugh, then busts out laughing and can't move.
51              While he's laughing you run up and shoot him square in
52              the head putting him down, then jump through the
53              Weapon Armory door.
54              """))
55  return  'laser_weapon_armory'
56
57  else:
58  print("DOES NOT COMPUTE!")
59  return  'central_corridor'
```

然后我创建了中央走廊，这是游戏的开始。我把游戏的场景放在 Map 之前，是因为我需要在随后引用它们。你应该也看到了我在第 4 行用了 dedent 函数。稍后你可以尝试删除它，看看它会做什么。

ex43.py

```py
1  class  LaserWeaponArmory(Scene):
2
3  def enter(self):
4  print(dedent("""
5           You do a dive roll into the Weapon Armory, crouch and scan
6           the room for more Gothons that might be hiding. It's dead
7           quiet, too quiet. You stand up and run to the far side of
8           the room and find the neutron bomb in its container.
9           There's a keypad lock on the box and you need the code to
10          get the bomb out. If you get the code wrong 10 times then
11          the lock closes forever and you can't get the bomb. The
12          code is 3 digits.
13          """))
14
15 code = f"{randint(1,9)}{randint(1,9)}{randint(1,9)}"
16 guess = input("[keypad]> ")
17 guesses =  0
18
19  while guess != code and guesses <  10:
20  print("BZZZZEDDD!")
21 guesses +=  1
22 guess = input("[keypad]> ")
23
24  if guess == code:
25  print(dedent("""
26              The container clicks open and the seal breaks, letting
27              gas out. You grab the neutron bomb and run as fast as
28              you can to the bridge where you must place it in the
29              right spot.
30              """))
31  return  'the_bridge'
32  else:
33  print(dedent("""
34              The lock buzzes one last time and then you hear a
35              sickening melting sound as the mechanism is fused
36              together. You decide to sit there, and finally the
37              Gothons blow up the ship from their ship and you die.
38              """))
39  return  'death'
40
41
42
43  class  TheBridge(Scene):
44
45  def enter(self):
46  print(dedent("""
47          You burst onto the Bridge with the netron destruct bomb
48          under your arm and surprise 5 Gothons who are trying to
49          take control of the ship. Each of them has an even uglier
50          clown costume than the last. They haven't pulled their
51          weapons out yet, as they see the active bomb under your
52          arm and don't want to set it off.
53          """))
54
55 action = input("> ")
56
57  if action ==  "throw the bomb":
58  print(dedent("""
59              In a panic you throw the bomb at the group of Gothons
60              and make a leap for the door. Right as you drop it a
61              Gothon shoots you right in the back killing you. As
62              you die you see another Gothon frantically try to
63              disarm the bomb. You die knowing they will probably
64              blow up when it goes off.
65              """))
66  return  'death'
67
68  elif action ==  "slowly place the bomb":
69  print(dedent("""
70              You point your blaster at the bomb under your arm and
71              the Gothons put their hands up and start to sweat.
72              You inch backward to the door, open it, and then
73              carefully place the bomb on the floor, pointing your
74              blaster at it. You then jump back through the door,
75              punch the close button and blast the lock so the
76              Gothons can't get out. Now that the bomb is placed
77              you run to the escape pod to get off this tin can.
78              """))
79
80  return  'escape_pod'
81  else:
82  print("DOES NOT COMPUTE!")
83  return  "the_bridge"
84
85
86  class  EscapePod(Scene):
87
88  def enter(self):
89  print(dedent("""
90          You rush through the ship desperately trying to make it
91          the escape pod before the whole ship explodes. It seems
92          like hardly any Gothons are on the ship, so your run is
93          clear of interference. You get to the chamber with the
94          escape pods, and now need to pick one to take. Some of
95          them could be damaged but you don't have time to look.
96          There's 5 pods, which one do you take?
97          """))
98
99 good_pod = randint(1,5)
100 guess = input("[pod #]> ")
101
102
103  if  int(guess)  != good_pod:
104  print(dedent("""
105             You jump into pod {guess} and hit the eject button.
106             The pod escapes out into the void of space, then
107             implodes as the hull ruptures, crushing your body into
108             jam jelly.
109             """))
110  return  'death'
111  else:
112  print(dedent("""
113             You jump into pod {guess} and hit the eject button.
114             The pod easily slides out into space heading to the
115             planet below. As it flies to the planet, you look
116             back and see your ship implode then explode like a
117             bright star, taking out the Gothon ship at the same
118             time. You won!
119             """))
120
121  return  'finished'
122
123  class  Finished(Scene):
124
125  def enter(self):
126  print("You won! Good job.")
127  return  'finished'
```

这是游戏的剩余场景，因为我知道我需要它们，并且已经想过它们之间如何流转，所以我能直接把代码写出来。

顺便说一句，我不会把所有这些代码都输入进去。还记得我说过要循序渐进，一点一点来。现在我只给你们看最后的结果。

ex43.py

```py
1  class  Map(object):
2
3 scenes =  {
4  'central_corridor':  CentralCorridor(),
5  'laser_weapon_armory':  LaserWeaponArmory(),
6  'the_bridge':  TheBridge(),
7  'escape_pod':  EscapePod(),
8  'death':  Death(),
9  'finished':  Finished(),
10  }
11
12  def __init__(self, start_scene):
13  self.start_scene = start_scene
14
15  def next_scene(self, scene_name):
16 val =  Map.scenes.get(scene_name)
17  return val
18
19  def opening_scene(self):
20  return  self.next_scene(self.start_scene)
```

然后是我的 Map 类，你可以看到它把每个场景的名字存储在一个字典里，然后我用 Map.scenes 引用那个字典。这也是为什么地图出现在场景之后的原因，因为字典必须引用场景，所以场景必须先存在。

ex43.py

```py
1 a_map =  Map('central_corridor')
2 a_game =  Engine(a_map)
3 a_game.play()
```

最后是我通过制作地图来运行游戏的代码，在调用 play 使游戏工作之前，我把地图交给了引擎。

## 你会看到

确保你理解了这个游戏，并且你先试图自己去解决它。如果你被难住了，你可以通过阅读我的代码来作弊，然后继续尝试自己解决它。

以下是我运行我的游戏的结果：

练习 43 会话

```py
$ python3.6 ex43.py
The  Gothons of Planet  Percal  #25 have invaded your ship and destroyed your entire crew. You are the last surviving member and your last mission is to get the neutron destruct bomb from the Weapons Armory, put it in the bridge, and blow the ship up after getting into an escape pod.
You're running down the central corridor to the Weapons Armory when a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume flowing around his hate filled body. He's blocking the door to the Armory  and about to pull a weapon to blast you.
> dodge!
Like a world class boxer you dodge, weave, slip and slide right as the Gothon's blaster cranks a laser past your head. In the middle of your artful dodge your foot slips and you bang your head on the metal wall and pass out. You wake up shortly after only to die as the Gothon stomps on your head and eats you.
You're worse than your Dad's jokes.
```

## 附加练习

*   改变它！也许你不喜欢这个游戏，因为太暴力了，也可能你对科幻不感兴趣。先让游戏运行起来，然后把它变成你喜欢的样子。这是你的电脑，你可以让它做你想做的。

*   我这段代码有一个 bug。为什么门锁猜了 11 次?

*   解释一下如何返回隔壁房间。

*   在游戏中添加作弊代码，这样你就可以通过比较难的房间。我可以通过在一行写两个字来实现这一点。

*   回到我的描述和分析，然后尝试为这个英雄和他遇到的各种哥特人建立一个小的战斗系统。

*   这实际上是“有限状态机”（finite state machine）的一个小版本。读读相关的内容，你可能看不懂，但无论如何都要试一试。

## 常见问题

**我在哪里可以找到我自己的游戏故事？**你可以自己编，就像你给朋友讲故事一样。或者你可以从你喜欢的书或电影中选取一些简单的场景。