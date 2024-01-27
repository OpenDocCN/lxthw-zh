## 练习 36：使用函数显示骰子

上一个练习在一个函数实际上使事情变得更糟的程序中使用了函数。所以今天我们准备看一个情况，使用函数实际上使程序变得更好。

Yacht 是一个古老的骰子游戏，后来被修改为商业游戏 Yahtzee。它涉及一次掷五个骰子，并为各种组合赚取积分。最罕见的组合是“游艇”，当五个骰子都显示相同的数字时。

这个程序不做任何其他的评分，它只是掷五个骰子，直到它们都相同。（计算机速度很快，所以即使这需要很多次尝试，也不会花费很长时间。）

```java
 1 public class YachtDice
 2 {
 3     public static void main( String[] args )
 4     {
 5         int roll1, roll2, roll3, roll4, roll5;
 6         boolean allTheSame;
 7 
 8         do
 9         {
10             roll1 = 1 + (int)(Math.random()*6);
11             roll2 = 1 + (int)(Math.random()*6);
12             roll3 = 1 + (int)(Math.random()*6);
13             roll4 = 1 + (int)(Math.random()*6);
14             roll5 = 1 + (int)(Math.random()*6);
15             System.out.println("\nYou rolled: " + roll1 + " " + roll2 + " " + 
roll3 + " " + roll4 + " " + roll5);
16             showDice(roll1);
17             showDice(roll2);
18             showDice(roll3);
19             showDice(roll4);
20             showDice(roll5);
21             allTheSame = ( roll1 == roll2 && roll2 == roll3 && roll3 == roll4 
&& roll4 == roll5 );
22 
23         } while ( ! allTheSame );
24         System.out.println("The Yacht!!");
25     }
26 
27     public static void showDice( int roll )
28     {
29         System.out.println("+­­­+");
30         if ( roll == 1 )
31         {
32             System.out.println("|   |");
33             System.out.println("| o |");
34             System.out.println("|   |");
35         }
36         else if ( roll == 2 )
37         {
38             System.out.println("|o  |");
39             System.out.println("|   |");
40             System.out.println("|  o|");
41         }
42         else if ( roll == 3 )
43         {
44             System.out.println("|o  |");
45             System.out.println("| o |");
46             System.out.println("|  o|");
47         }
48         else if ( roll == 4 )
49         {
50             System.out.println("|o o|");
51             System.out.println("|   |");
52             System.out.println("|o o|");
53         }
54         else if ( roll == 5 )
55         {
56             System.out.println("|o o|");
57             System.out.println("| o |");
58             System.out.println("|o o|");
59         }
60         else if ( roll == 6 )
61         {
62             System.out.println("|o o|");
63             System.out.println("|o o|");
64             System.out.println("|o o|");
65         }
66         System.out.println("+­­­+");
67     }
68 }
```

### 你应该看到什么

```java

You rolled:
+­­­+
|o o|
| |
|o o|
+­­­+
+­­­+
|o o|
|o o|
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
|o o|
|o o|
+­­­+
4
6
5
5
6
You rolled:
+­­­+
|o |
| |
| o|
+­­­+
+­­­+
|o |
| |
| o|
+­­­+
+­­­+
|o o|
| o |
|o o|
2
2
5
6
6
+­­­+
+­­­+
|o o|
|o o|
|o o|
+­­­+
+­­­+
|o o|
|o o|
|o o|
+­­­+

...etc

You rolled: 5 5 5 5 5
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
The Yacht!!
```

除了第 21 行的花哨的布尔表达式之外，这个练习中有一个名为`showDice`  的单个函数。

在 10 到 14 行，我们选择五个随机数（每个数从 1 到 6）并将结果存储到五个整数变量`roll1`到`roll5`中。

我们想要使用一些`if`语句在屏幕上显示骰子的值，但我们不想写五次相同的`if`语句（因为变量是不同的）。解决方案是创建一个带参数的函数。

在第 27 行，你看到了`showDice`  函数定义的开始。在名称（或“标识符”）`showDice`  后面，有一组括号，在它们之间声明了一个变量！这个变量叫做“参数”。`showDice`  函数有一个参数。这个参数是一个整数。它的名字叫`roll`。

这意味着每当你为`showDice`写一个函数调用时，你不能只写函数的名称和括号，比如`showDice()`。它不会编译。你必须在括号中包含一个整数值（这称为“参数”），要么是一个变量，要么是一个简化为整数值的表达式。

这里有一些例子。

```java
showDice;                       // NO  (without parens this refers to a variable not a function call)
showDice();                     // NO  (function call must have one argument, not zero)
showDice(1);                    // YES (one argument is just right)
showDice(4);                    // YES
showDice(1+2);                  // YES
showDice(roll2);                // YES
showDice(roll5);                // YES
showDice( (roll3+roll4) / 2 );  // YES (strange but legal)
showDice(17);                   // YES (although it won't show a proper dice picture)
showDice(3, 4);                 // NO  (function call must have one argument, not two)
showDice(2.0);                  // NO  (argument must be an integer, not a double)
showDice("two");                // NO  (argument must be an integer, not a String)
showDice(false);                // NO  (argument must be an integer, not a Boolean)
```

在所有情况下，参数的值的副本都存储在参数中。因此，如果你这样调用函数`showDice(3);`，那么函数被调用，值`3`被存储到参数`roll`中。所以到第 29 行，参数变量`roll`已经被声明并初始化为值`3`。

如果我们使用变量调用函数，比如`showDice(roll2);`那么在函数体执行之前，函数被调用并且当前在`roll2`中的任何值的副本将被存储到参数变量`roll`中。

因此，在第 16 行，`showDice`函数被执行，`roll`将被设置为`roll1`中的任何值。

然后在第 17 行，`showDice`再次被调用，但这次`roll`将被设置为`roll1`中的任何值。

`roll2`。第 18 行调用`showDice`，同时将其参数设置为`roll2`的值。等等。

这样我们基本上运行了相同的代码块五次，但用不同的变量替换

每次掷骰子。这为我们节省了很多代码。

为了对比，我还写了一个简化的两个骰子版本的练习，而不使用函数。请注意，我必须重复完全相同的`if`语句序列两次：每个变量一次。

还要注意的是，虽然定义函数比只是复制和粘贴要多一点工作

```java

 1 public class YachtDiceNoFunctions
 2 {
 3     public static void main( String[] args )
 4     {
 5         int roll1, roll2;
 6 
 7         do
 8         {
 9             roll1 = 1 + (int)(Math.random()*6);
10             roll2 = 1 + (int)(Math.random()*6);
11             int total = roll1 + roll2;
12             System.out.println("\nYou rolled a " + roll1 + " and a " + roll2);
13             System.out.println("+­­­+");
14             if ( roll1 == 1 )
15             {
16                 System.out.println("|   |");
17                 System.out.println("| o |");
18                 System.out.println("|   |");
19             }
20             else if ( roll1 == 2 )
21             {
22                 System.out.println("|o  |");
23                 System.out.println("|   |");
24                 System.out.println("|  o|");
25             }
26             else if ( roll1 == 3 )
27             {
28                 System.out.println("|o  |");
29                 System.out.println("| o |");
30                 System.out.println("|  o|");
31             }
32             else if ( roll1 == 4 )
33             {
34                 System.out.println("|o o|");
35                 System.out.println("|   |");
36                 System.out.println("|o o|");
37             }
38             else if ( roll1 == 5 )
39             {
40                 System.out.println("|o o|");
41                 System.out.println("| o |");
42                 System.out.println("|o o|");
43             }
44             else if ( roll1 == 6 )
45             {
46                 System.out.println("|o o|");
47                 System.out.println("|o o|");
48                 System.out.println("|o o|");
49             }
50             System.out.println("+­­­+");
51 
52 
53             System.out.println("+­­­+");
54             if ( roll2 == 1 )
55             {
56                 System.out.println("|   |");
57                 System.out.println("| o |");
58                 System.out.println("|   |");
59             }
60             else if ( roll2 == 2 )
61             {
62                 System.out.println("|o  |");
63                 System.out.println("|   |");
64                 System.out.println("|  o|");
65             }
66             else if ( roll2 == 3 )
67             {
68                 System.out.println("|o  |");
69                 System.out.println("| o |");
70                 System.out.println("|  o|");
71             }
72             else if ( roll2 == 4 )
73             {
74                 System.out.println("|o o|");
75                 System.out.println("|   |");
76                 System.out.println("|o o|");
77             }
78             else if ( roll2 == 5 )
79             {
80                 System.out.println("|o o|");
81                 System.out.println("| o |");
82                 System.out.println("|o o|");
83             }
84             else if ( roll2 == 6 )
85             {
86                 System.out.println("|o o|");
87                 System.out.println("|o o|");
88                 System.out.println("|o o|");
89             }
90             System.out.println("+­­­+");
91 
92             System.out.println("The total is " + total + "\n");
93         } while ( roll1 != roll2 );
94 
95         System.out.println("Doubles!  Nice job.");
96     }
97 }
```

### 你应该看到什么

```java
You rolled a 5 and a 4
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
|   |
|o o|
+­­­+
The total is 9
You rolled a 6 and a 2
+­­­+
|o o|
|o o|
|o o|
+­­­+
+­­­+
|o  |
|   |
|  o|
+­­­+
The total is 8
You rolled a 2 and a 2
+­­­+
|o  |
|   |
|  o|
+­­­+
+­­­+
|o  |
|   |
|  o|
+­­­+
The total is 4
Doubles!  Nice job.

```

### 学习演练

1. 添加第六个骰子。注意，只需添加一个函数调用就可以轻松显示`roll6`。

