# 练习 43.基本的面向对象的分析和设计

# 练习 43.基本的面向对象的分析和设计

在这节练习，我想给你介绍一个使用 python 创建某类东西的过程，也就是“面向对象编程”（OOP）。我把它叫做一个过程，是因为我将给出一系列按顺序进行的步骤，但是你也不应该死板的遵循这个步骤，企图用它解决所有难题。它们对于许多编程问题只是一个良好的开头，而不应该被认为是解决这些问题的唯一方法。这个过程只是一个你可以遵循的方法：

> 1.  写出或画出你的问题
> 2.  从 1 中提炼关键问题并搜索相关资料
> 3.  为 2 中的问题创建一个有层次结构的类和对象映射
> 4.  编写类和测试代码，并保证他们运行
> 5.  重复并精炼

按照这个顺序执行流程，叫做“自顶向下”的方式，意思是说，它从非常抽象宽松的想法开始，然后慢慢提炼，直到想法是坚实的东西，然后你再开始编码。

首先我只是写出这个问题，并试图想出任何我想要的东西就可以了。也许我会画一两个图表，或者某种可能的地图，甚至给自己写了一系列的电子邮件描述这个问题。这给了我表达了问题的关键概念的方法，并探测出我对于这个游戏有什么具体的想法和了解。

接下来，我浏览这些笔记，图表以及描述，通过这些记录我找到我需要的关键问题点。有一个简单的技巧：简单地列出你的笔记和图表中所有的名词和动词,然后写出他们是如何相关的。这一步其实也我为我下一步要写的类、对象、以及函数等提供了命名列表。我利用这个概念列表，研究任何我不明白的地方，如果我需要，我还可以进一步完善它们。

一旦我完成这个列表，我可以创建的一个简单的轮廓/树用来说明这些概念之间的关系。你还可以对着你的名词列表并询问“这个名词和其他的是一个概念吗？或者它们有一个通用的父类吗，那它们的父类是什么？”持续检查，直到你得到一个有层次结构的类，它应该像一棵简单的树或者图表。然后检查你的动词列表，看它们是否可以作为函数的名字添加到你的类树种。

随着这棵类树的生成，我坐下来写一些基本的框架代码，代码中只包括刚才提到的类，类中包含的函数。然后我再写一个测试用例，用来检验我刚才写的类是正确的。有时候我可能只需要在开始写一段测试代码，但是更多的时候，我需要写一段测试，再写一段代码，再写一段测试...直到整个项目完成。

最后，在我完成更多的工作之前，我周期性的重复和精炼这个流程，是他变得清楚和易于理解。如果我在一个没有预料到的地方被一些概念或问题卡住，我会停下来在这一小部分上投入更大的精力来分析解决，直到我解决了这问题，再继续下去。

这节练习中，我将通过建造一个游戏引擎带大家学习这一流程。

## 分析一个简单的游戏引擎

我打算制作一个叫做 "Gothons from Planet Percal #25"的游戏，这个一个小型的太空冒险游戏。

## 写或画出这个问题

我为这个游戏写了一小段描述：

“外星人乘坐一个宇宙飞船入侵,我们的英雄需要通过一个迷宫似的房间击败他们,然后他才能逃入一个逃生舱到达下面的行星。游戏将更像一个有着文本输出和有趣的死法的 Zork 或冒险类型游戏。游戏将包括一个引擎运行充满房间或场景的地图。 当玩家进入房间，每个房间将打印自己的描述,然后告诉引擎运行下一个地图。”

我先描述每个场景：

Death: 这是玩家死亡的场景，应该是有趣的。

Central Corridor: 这是游戏的起点，在这里已经有一个外星人等待英雄的到来，它们需要被一个玩笑打败。

Laser Weapon Armory: 这是英雄得到了中子弹获得的逃生舱之前要炸毁的船。它有一个需要英雄猜数的键盘。

The Bridge: 和外星人战斗的另一个场景，英雄防止炸弹的地方。

Escape Pod: 英雄逃脱的场景，但是需要英雄找对正确的逃生舱

现在，我可以绘制出它们的地图，或者对每个房间再多写一些描述，或者其他一些我脑中出现的想法。

## 提取关键概念并研究他们

现在我已经有足够多的信息还提取出名词，并分析它们的类结构。首先我列出所有的名词：

> *   Alien
> *   Player
> *   Ship
> *   Maze
> *   Room
> *   Scene
> *   Gothon
> *   Escape Pod
> *   Planet
> *   Map
> *   Engine
> *   Death
> *   Central Corridor
> *   Laser Weapon Armory
> *   The Bridge

我也可能要列出所有的动词，看它们能否作为函数的名字，不过现在我要先跳过这一步。

你需要研究所有你现在还不知道的概念。例如，我可能会玩几个这种类型的游戏，并确保知道他们是如何工作的。我可能会研究船舶和炸弹的设计和工作原理。也许我会研究怎么样将游戏中的数据或状态存储在数据库等一些技术上的问题。我做完这个研究之后，我可能会回到第 1 步重新开始，根据新的信息，重写描述和提取新的概念。

## 创建一个层次结构的类和对象映射的概念

当我完成上面的步骤，我通过思考“哪些是类似于其他东西的”，把名词列表转换成一个有层次结构的类树，同样，我也会思考，哪些单词是其他东西的基础呢？

马上我发现，"Room" 和 "Scene"对于我要做的事情来说基本上是一样的事情。在这个游戏中，我选择使用"Scene" 。接下来我发现，所有的特殊房间比如"Central Corridor"基本上也跟"Scene"是一样的。我发现"Death"也是一个"Scene", 由于我选择了"Scene"而不是"Room"，你可以有一个“死亡场景”，而是不一个很奇怪的“死亡房间”。"Maze"和"Map"基本一样，所以我选择使用"Map"，因为我更多的时候都用它。我不想做一个战斗系统，所以我会先忽略"Alien"和 "Player"，但是会把他们保存下来以供以后使用。"Planet"也可能仅仅是另一个场景，而不是什么具体的事情。

在此之后，我开始创建一个层次结构的类：

> *   Map
> *   Engine
> *   Scene
> 
> *   Death
> *   Central Corridor
> *   Laser Weapon Armory
> *   The Bridge
> *   Escape Pod

然后，我会找出说明中每个动词都需要什么行动。比如，我从说明中得知，我需要一个方法来"run"这个引擎，通过地图获得下一个场景"get the next scene"，获得"opening scene"，或者"enter"一个场景。我把这些加到类树里：

> *   Map- next_scene- opening_scene
> *   Engine- play
> *   Scene- enter *Death* Central Corridor *Laser Weapon Armory* The Bridge* Escape Pod

注意一下，我只是把`-enter`放到`Scene`下面，因为我知道所有的场景都会继承它并重写它。

## 编码类和测试代码并运行它们

当我有了这个类树和一些功能之后，我在编辑器中打开源文件，并尝试编写代码。通常，我会复制粘贴这棵类树到源文件中，然后编辑它。下面是一个如何编码的小例子，文件末尾包含一个简单的测试用例：

```py
class Scene(object):

    def enter(self):
        pass

class Engine(object):

    def __init__(self, scene_map):
        pass

    def play(self):
        pass

class Death(Scene):

    def enter(self):
        pass

class CentralCorridor(Scene):

    def enter(self):
        pass

class LaserWeaponArmory(Scene):

    def enter(self):
        pass

class TheBridge(Scene):

    def enter(self):
        pass

class EscapePod(Scene):

    def enter(self):
        pass

class Map(object):

    def __init__(self, start_scene):
        pass

    def next_scene(self, scene_name):
        pass

    def opening_scene(self):
        pass

a_map = Map('central_corridor')
a_game = Engine(a_map)
a_game.play() 
```

在这个文件中，你可以看到我只是复制了我想要的层次结构,然后一点点的补齐代码再运行它,看看它在这个基本结构中是否运行顺利。 在这节练习后面的部分，你会填补这段代码的其余部分，使其正常工作，以配合练习开头的游戏描述。

## 重复并精炼

在我提供的流程中，最后一步并不是实际意义上的一步，而是要做一个循环。在编程的世界里，你永远做不到一次通过，相反，你退回整个过程，并再次根据你从后面的步骤中了解到的信息完善它。有时候我已经到了第 3 步，但是我发现我还需要在第 1、2 步做更多工作，我会停下来并返回去完善它。有时候我也会突然灵光一闪，跳到最后，用我脑子里更好的解决方案编码实现，但是之后，我仍然会回去完成前面的步骤，以确保我的工作覆盖了所有的可能性。

在这一过程的另一个观点是，你不是仅在一个层面上使用这个流程，当你遇到某些特定问题的时候，你可以在任意一个层级上使用该流程。比方说，我不知道如何写`Engine.play`方法，我可以静下心来用这个流程只做这一种功能，直到弄清楚这个方法怎么写。

## 自顶向下和自下而上

因为这个流程在最抽象的概念（顶部）开始，然后再下降到实际执行过程中，因此这一流程通常标示为“自上而下”。我希望你使用这一流程，但你也应该知道，还有另一种方式来解决程序中的问题，这种方式是从代码开始，再“上升”到抽象的概念问题。这种方式被称为“自下而上”。下面是自下而下方式所遵循的步骤：

> 1.  取一小块问题，编写一些代码，并让他勉强运行
> 2.  完善代码，将其转换成一些更正式的包含类和自动化测试的代码。
> 3.  提取其中的关键概念，并尝试找出研究他们。
> 4.  写出到底发生了什么的描述。
> 5.  继续完善代码，也可能是把它扔掉，并重新开始。
> 6.  移动到其他问题上，重复步骤。

当你需要更优质的代码，并在代码中更自然的思考你要解决的问题时，这种方式更好一些。尤其是当你知道小块的难题,但没有足够的信息把握整个概念的时候，这个方式是一个解决问题很好的办法。将问题分解成碎片并探索代码,直到你解决这个问题。然而，你解决问题的途径可能是缓慢而曲折的，所以，我的这一流程中也包含后退并反复研究问题，直到你通过自己所为解决所有难题。

## “来自 Percal 25 号行星的哥顿人”的代码

我要告诉你我解决上述问题的最终办法,但我不希望你只是直接跳到这里并输入代码。我希望你能通过我的描述，完成我写的那个简单粗糙的代码框架，并让他运行起来。当你有了自己的解决方案时，你可以回来看看我是怎么解决的。

我准备把文件`ex43.py`拆成小块，再一一解释，而不是一次性提供完整的代码。

```py
from sys import exit
from random import randint 
```

这只是我们游戏需要导入的包，没什么新奇的。

```py
class Scene(object):

    def enter(self):
        print "This scene is not yet configured. Subclass it and implement enter()."
        exit(1) 
```

正如你在框架代码里看到的，我创建了基础类`Scene`,它将包含所有 scene 要做的所有的事。在这段代码中，它们并没有做什么，所以这只是给你的一个如果创建基类的示范。

```py
class Engine(object):

    def __init__(self, scene_map):
        self.scene_map = scene_map

    def play(self):
        current_scene = self.scene_map.opening_scene()
        last_scene = self.scene_map.next_scene('finished')

        while current_scene != last_scene:
            next_scene_name = current_scene.enter()
            current_scene = self.scene_map.next_scene(next_scene_name)

        # be sure to print out the last scene
        current_scene.enter() 
```

我同样创建了类`Engine`，并且你能看到我已经使用了方法`Map.opening_scene` 和 `Map.next_scene`。因为在我写`Map`类之前，做了一点计划，我可以假设我后面会写这些,然后提前使用它们。

```py
class Death(Scene):

    quips = [
        "You died.  You kinda suck at this.",
         "Your mom would be proud...if she were smarter.",
         "Such a luser.",
         "I have a small puppy that's better at this."
    ]

    def enter(self):
        print Death.quips[randint(0, len(self.quips)-1)]
        exit(1) 
```

我的第一个场景是一个叫做`Death`的场景，它给你展现了你能写的最简单的场景。

```py
class CentralCorridor(Scene):

    def enter(self):
        print "The Gothons of Planet Percal #25 have invaded your ship and destroyed"
        print "your entire crew.  You are the last surviving member and your last"
        print "mission is to get the neutron destruct bomb from the Weapons Armory,"
        print "put it in the bridge, and blow the ship up after getting into an "
        print "escape pod."
        print "\n"
        print "You're running down the central corridor to the Weapons Armory when"
        print "a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume"
        print "flowing around his hate filled body.  He's blocking the door to the"
        print "Armory and about to pull a weapon to blast you."

        action = raw_input("> ")

        if action == "shoot!":
            print "Quick on the draw you yank out your blaster and fire it at the Gothon."
            print "His clown costume is flowing and moving around his body, which throws"
            print "off your aim.  Your laser hits his costume but misses him entirely.  This"
            print "completely ruins his brand new costume his mother bought him, which"
            print "makes him fly into an insane rage and blast you repeatedly in the face until"
            print "you are dead.  Then he eats you."
            return 'death'

        elif action == "dodge!":
            print "Like a world class boxer you dodge, weave, slip and slide right"
            print "as the Gothon's blaster cranks a laser past your head."
            print "In the middle of your artful dodge your foot slips and you"
            print "bang your head on the metal wall and pass out."
            print "You wake up shortly after only to die as the Gothon stomps on"
            print "your head and eats you."
            return 'death'

        elif action == "tell a joke":
            print "Lucky for you they made you learn Gothon insults in the academy."
            print "You tell the one Gothon joke you know:"
            print "Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr."
            print "The Gothon stops, tries not to laugh, then busts out laughing and can't move."
            print "While he's laughing you run up and shoot him square in the head"
            print "putting him down, then jump through the Weapon Armory door."
            return 'laser_weapon_armory'

        else:
            print "DOES NOT COMPUTE!"
            return 'central_corridor' 
```

接下来，我创建了`CentralCorridor`，这是游戏的开始。我在写`Map`之前，为游戏制作了这个场景，是因为我后面要引用它们。

```py
class LaserWeaponArmory(Scene):

    def enter(self):
        print "You do a dive roll into the Weapon Armory, crouch and scan the room"
        print "for more Gothons that might be hiding.  It's dead quiet, too quiet."
        print "You stand up and run to the far side of the room and find the"
        print "neutron bomb in its container.  There's a keypad lock on the box"
        print "and you need the code to get the bomb out.  If you get the code"
        print "wrong 10 times then the lock closes forever and you can't"
        print "get the bomb.  The code is 3 digits."
        code = "%d%d%d" % (randint(1,9), randint(1,9), randint(1,9))
        guess = raw_input("[keypad]> ")
        guesses = 0

        while guess != code and guesses < 10:
            print "BZZZZEDDD!"
            guesses += 1
            guess = raw_input("[keypad]> ")

        if guess == code:
            print "The container clicks open and the seal breaks, letting gas out."
            print "You grab the neutron bomb and run as fast as you can to the"
            print "bridge where you must place it in the right spot."
            return 'the_bridge'
        else:
            print "The lock buzzes one last time and then you hear a sickening"
            print "melting sound as the mechanism is fused together."
            print "You decide to sit there, and finally the Gothons blow up the"
            print "ship from their ship and you die."
            return 'death'

class TheBridge(Scene):

    def enter(self):
        print "You burst onto the Bridge with the netron destruct bomb"
        print "under your arm and surprise 5 Gothons who are trying to"
        print "take control of the ship.  Each of them has an even uglier"
        print "clown costume than the last.  They haven't pulled their"
        print "weapons out yet, as they see the active bomb under your"
        print "arm and don't want to set it off."

        action = raw_input("> ")

        if action == "throw the bomb":
            print "In a panic you throw the bomb at the group of Gothons"
            print "and make a leap for the door.  Right as you drop it a"
            print "Gothon shoots you right in the back killing you."
            print "As you die you see another Gothon frantically try to disarm"
            print "the bomb. You die knowing they will probably blow up when"
            print "it goes off."
            return 'death'

        elif action == "slowly place the bomb":
            print "You point your blaster at the bomb under your arm"
            print "and the Gothons put their hands up and start to sweat."
            print "You inch backward to the door, open it, and then carefully"
            print "place the bomb on the floor, pointing your blaster at it."
            print "You then jump back through the door, punch the close button"
            print "and blast the lock so the Gothons can't get out."
            print "Now that the bomb is placed you run to the escape pod to"
            print "get off this tin can."
            return 'escape_pod'
        else:
            print "DOES NOT COMPUTE!"
            return "the_bridge"

class EscapePod(Scene):

    def enter(self):
        print "You rush through the ship desperately trying to make it to"
        print "the escape pod before the whole ship explodes.  It seems like"
        print "hardly any Gothons are on the ship, so your run is clear of"
        print "interference.  You get to the chamber with the escape pods, and"
        print "now need to pick one to take.  Some of them could be damaged"
        print "but you don't have time to look.  There's 5 pods, which one"
        print "do you take?"

        good_pod = randint(1,5)
        guess = raw_input("[pod #]> ")

        if int(guess) != good_pod:
            print "You jump into pod %s and hit the eject button." % guess
            print "The pod escapes out into the void of space, then"
            print "implodes as the hull ruptures, crushing your body"
            print "into jam jelly."
            return 'death'
        else:
            print "You jump into pod %s and hit the eject button." % guess
            print "The pod easily slides out into space heading to"
            print "the planet below.  As it flies to the planet, you look"
            print "back and see your ship implode then explode like a"
            print "bright star, taking out the Gothon ship at the same"
            print "time.  You won!"

            return 'finished'

class Finished(Scene):

    def enter(self):
        print "You won! Good job."
        return 'finished' 
```

这是游戏剩下的场景。因为我知道我需要他们，并且已经想好他们应该如何交织在一起，所以我可以直接编码。

顺便说一下，我不是直接输入这些代码。记得我说过的吗，用增量的方法尝试构建所有的代码，一次只写一小部分。我只是给你看了最终的结果。

```py
class Map(object):

    scenes = {
        'central_corridor': CentralCorridor(),
        'laser_weapon_armory': LaserWeaponArmory(),
        'the_bridge': TheBridge(),
        'escape_pod': EscapePod(),
        'death': Death(),
        'finished': Finished(),
    }

    def __init__(self, start_scene):
        self.start_scene = start_scene

    def next_scene(self, scene_name):
        val = Map.scenes.get(scene_name)
        return val

    def opening_scene(self):
        return self.next_scene(self.start_scene) 
```

在这之后，我写了`Map`类，你可以看到它通过名字把所有的场景存在了字典中。我把这个字典叫做`Map.scenes`。这也是为什么 map 是在 scens 之后才写的原因，因为这个字典需要包含所有已存在的场景。

```py
a_map = Map('central_corridor')
a_game = Engine(a_map)
a_game.play() 
```

最后，我让我的代码通过创建一个`Map`，并在调用`play`之前把 map 交给`Engine`,把游戏运行起来，

## 你看到的结果

确保你明白这个游戏，并且首先尝试自己解决它。如果你被难住了，可以阅读一小部分我的代码，然后再尝试自己搞定它。

当我运行我的游戏的时候，我可以看到：

```py
$ python ex43.py
The Gothons of Planet Percal #25 have invaded your ship and destroyed
your entire crew.  You are the last surviving member and your last
mission is to get the neutron destruct bomb from the Weapons Armory,
put it in the bridge, and blow the ship up after getting into an
escape pod.

You're running down the central corridor to the Weapons Armory when
a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume
flowing around his hate filled body.  He's blocking the door to the
Armory and about to pull a weapon to blast you.
>  dodge!
Like a world class boxer you dodge, weave, slip and slide right
as the Gothon's blaster cranks a laser past your head.
In the middle of your artful dodge your foot slips and you
bang your head on the metal wall and pass out.
You wake up shortly after only to die as the Gothon stomps on
your head and eats you.
Your mom would be proud...if she were smarter. 
```

## 附加题

> 1.  修改这个游戏！你可能不喜欢这个游戏。让游戏运行起来，然后按照你的喜好修改它。这是你的电脑，你可以用它做你想做的事情
> 2.  代码中有一个 bug，为什么门锁了 11 次？
> 3.  解释一下返回至下一个房间的工作原理。
> 4.  增加作弊代码，这样你能通过一些更难的房间。我能只在一行上加两个单词做到这些。
> 5.  回到我的描述和分析，尝试为英雄和他遇见的各种哥顿人创建一个小型作战系统。
> 6.  这其实是一个小版本的“有限状态机(finite state machine)”，找资料阅读了解一下，虽然你可能看不懂，但还是找来看看吧。

## 常见问题

### Q: 我在哪里可以为我的游戏找到故事情节

> 你可以就像给朋友讲述一个故事一样，来创建游戏。或者你可以采取简单的你喜欢的书或电影场景。