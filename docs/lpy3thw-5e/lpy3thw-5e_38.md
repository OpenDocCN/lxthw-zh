## 练习 35. 分支和函数

你已经学会了`if 语句`、函数和列表。现在是时候挑战你的思维了。把这个输入进去，看看你能否弄清楚它在做什么：

列表 35.1: ex35.py

```py
 1   **from** sys **import** exit
 2
 3   **def** gold_room**()**:
 4       **print(**"This room is full of gold. How much do you take?"**)**
 5
 6       choice = **input(**"> "**)**
 7       **if** "0" **in** choice **or** "1" **in** choice:
 8           how_much = **int(**choice**)**
 9       **else**:
10           dead**(**"Man, learn to type a number."**)**
11
12       **if** how_much < 50:
13           **print(**"Nice, you're not greedy, you win!"**)**
14           exit**(**0**)**
15       **else**:
16           dead**(**"You greedy bastard!"**)**
17
18
19   **def** bear_room**()**:
20       **print(**"There is a bear here."**)**
21       **print(**"The bear has a bunch of honey."**)**
22       **print(**"The fat bear is in front of another door."**)**
23       **print(**"How are you going to move the bear?"**)**
24       bear_moved = False
25
26       **while** True:
27           choice = **input(**"> "**)**
28
29           **if** choice == "take honey":
30               dead**(**"The bear looks at you then slaps your face off."**)**
31           **elif** choice == "taunt bear" **and not** bear_moved:
32               **print(**"The bear has moved from the door."**)**
33               **print(**"You can go through it now."**)**
34               bear_moved = True
35           **elif** choice == "taunt bear" **and** bear_moved:
36               dead**(**"The bear gets pissed off and chews your leg off."**)**
37           **elif** choice == "open door" **and** bear_moved:
38               gold_room**()**
39           **else**:
40               **print(**"I got no idea what that means."**)**
41
42
43   **def** cthulhu_room**()**:
44       **print(**"Here you see the great evil Cthulhu."**)**
45       **print(**"He, it, whatever stares at you and you go insane."**)**
46       **print(**"Do you flee for your life or eat your head?"**)**
47
48       choice = **input(**"> "**)**
49
50       **if** "flee" **in** choice:
51           start**()**
52       **elif** "head" **in** choice:
53           dead**(**"Well that was tasty!"**)**
54       **else**:
55           cthulhu_room**()**
56
57
58   **def** dead**(**why**)**:
59       **print(**why, "Good job!"**)**
60       exit**(**0**)**
61
62   **def** start**()**:
63       **print(**"You are in a dark room."**)**
64       **print(**"There is a door to your right and left."**)**
65       **print(**"Which one do you take?"**)**
66
67       choice = **input(**"> "**)**
68
69       **if** choice == "left":
70           bear_room**()**
71       **elif** choice == "right":
72           cthulhu_room**()**
73       **else**:
74           dead**(**"You stumble around the room until you starve."**)**
75
76
77   start**()**
```

### 你应该看到什么

这是我玩游戏的样子：

```py
 1   You are in a dark room.
 2   There is a door to your right and left.
 3   Which one do you take?
 4   > left
 5    There is a bear here.
 6   The bear has a bunch of honey.
 7   The fat bear is in front of another door.
 8   How are you going to move the bear?
 9   > taunt bear
10   The bear has moved from the door.
11   You can go through it now.
12   > open door
13   This room is full of gold. How much do you take?
14   > 1000
15   You greedy bastard! Good job!
```

### 学习练习

1\. 绘制游戏地图以及你如何在其中流动。

2\. 修复所有错误，包括拼写错误。

3\. 为你不理解的函数写注释。

4\. 添加更多内容到游戏中。你能做些什么来简化和扩展它？

5\. `gold_room` 有一种奇怪的方式让你输入一个数字。这种方式存在哪些错误？你能比我写的更好吗？看看 `int()` 的工作原理会有提示。

### 常见学生问题

**救命！这个程序怎么运行的！？** 当你在理解一段代码时遇到困难时，只需在*每一行*上面写一个英文注释，解释该行的作用。保持你的评论简短并与代码相似。然后要么画出代码的工作原理，要么写一段描述它的段落。如果你这样做，你就会理解它。

**为什么你写了** `while True`**？** 这会造成一个无限循环。

**`exit(0)` 的作用是什么？** 在许多操作系统上，一个程序可以通过 `exit(0)` 中止，传入的数字将指示是否有错误。如果你使用 `exit(1)`，那么就会有一个错误，但 `exit(0)` 将是一个良好的退出。它与正常的布尔逻辑相反（`0==False`）的原因是你可以使用不同的数字来指示不同的错误结果。你可以使用 `exit(100)` 来表示不同的错误结果，而不同于 `exit(2)` 或 `exit(1)`。

**为什么** `input()` **有时写成** `input('> ')`**？** `input` 的参数是一个字符串，它应该在获取用户输入之前打印作为提示。
