# 练习 35.分支和函数

# 练习 35.分支和函数

你已经学会了 if 语句、函数、还有列表。现在你要练习扭转一下思维了。把下面的代码写下来，看你是否能弄懂它实现的是什么功能。

```py
from sys import exit

def gold_room():
    print "This room is full of gold.  How much do you take?"

    choice = raw_input("> ")
    if "0" in choice or "1" in choice:
        how_much = int(choice)
    else:
        dead("Man, learn to type a number.")

    if how_much < 50:
        print "Nice, you're not greedy, you win!"
        exit(0)
    else:
        dead("You greedy bastard!")

def bear_room():
    print "There is a bear here."
    print "The bear has a bunch of honey."
    print "The fat bear is in front of another door."
    print "How are you going to move the bear?"
    bear_moved = False

    while True:
        choice = raw_input("> ")

        if choice == "take honey":
            dead("The bear looks at you then slaps your face off.")
        elif choice == "taunt bear" and not bear_moved:
            print "The bear has moved from the door. You can go through it now."
            bear_moved = True
        elif choice == "taunt bear" and bear_moved:
            dead("The bear gets pissed off and chews your leg off.")
        elif choice == "open door" and bear_moved:
            gold_room()
        else:
            print "I got no idea what that means."

def cthulhu_room():
    print "Here you see the great evil Cthulhu."
    print "He, it, whatever stares at you and you go insane."
    print "Do you flee for your life or eat your head?"

    choice = raw_input("> ")

    if "flee" in choice:
        start()
    elif "head" in choice:
        dead("Well that was tasty!")
    else:
        cthulhu_room()

def dead(why):
    print why, "Good job!"
    exit(0)

def start():
    print "You are in a dark room."
    print "There is a door to your right and left."
    print "Which one do you take?"

    choice = raw_input("> ")

    if choice == "left":
        bear_room()
    elif choice == "right":
        cthulhu_room()
    else:
        dead("You stumble around the room until you starve.")

start() 
```

## 你看到的结果

这是我玩这个游戏的过程：

```py
$ python ex35.py
You are in a dark room.
There is a door to your right and left.
Which one do you take?
>  left
There is a bear here.
The bear has a bunch of honey.
The fat bear is in front of another door.
How are you going to move the bear?
>  taunt bear
The bear has moved from the door. You can go through it now.
>  open door
This room is full of gold.  How much do you take?
>  1000
You greedy bastard! Good job! 
```

## 附加题

> 1.  把这个游戏的地图画出来，把自己的路线也画出来。
> 2.  改正你所有的错误，包括拼写错误。
> 3.  为你不懂的函数写注释。
> 4.  为游戏添加更多元素。通过怎样的方式可以简化并且扩展游戏的功能呢？
> 5.  这个`gold_room`游戏使用了奇怪的方式让你键入数字。这种方式会导致什么样的 bug？ 你可以用比检查 0、1 更好的方式判断输入是否是数字吗？`int()` 这个函数可以给你一些头绪。

## 常见问题

### Q: 求助！这个程序是怎样运行的？

> 当你理解一段代码遇到困难的时候，可以给每一行代码加上一段简单的注释用来解释每一句实现什么功能。尽量使你的注释短小且与代码近似.然后用图解或者写一段描述来弄懂代码是如何工作的。如果你这么做了，你就能弄明白这段代码是如何工作的。

### Q: 你为什么用了`while True`?

> 这么写可以创建一个无限循环

### Q: `exit()`是干什么的？

> 在许多操作系统中可以使用`exit(0)`来中止程序，传递的数字参数表示是否遇到异常。如果使用`exit(1)`退出将会出现一个错误，但是用`exit(0)`就是正常的退出。参数部分和正常的布尔逻辑正好是相反的 (正常的布尔逻辑中 0==False) 您可以使用不同的数字来表示不同的错误结果。你也可以用`exit(100)`来表示一个不同于`exit(2)`和 `exit(1)`的错误信息.

### Q: 为什么有时候把`raw_input` 写成`raw_input('&gt;')`

> `raw_input`的参数只是一个字符串，会打印显示在要求用户输入之前。