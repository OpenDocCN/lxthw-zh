## 练习 35：调用函数绘制旗帜

现在你已经了解了如何定义函数和调用函数的绝对基础知识，让我们通过定义*十一个*函数来进行一些练习！

这个程序中没有零（`0`）。所有看起来像`O`的东西都是大写字母 O。还要注意，第 45 行和第 50 行使用的是`print()`而不是`println()`。

```java
 1 import static java.lang.System.*;
 2 
 3 public class OverlyComplexFlag
 4 {
 5     public static void main( String[] args )
 6     {
 7         printTopHalf();
 8 
 9         print48Colons();
10         print48Ohs();
11         print48Colons();
12         print48Ohs();
13         print48Colons();
14         print48Ohs();
15     }
16 
17     public static void print48Colons()
18     {
19         out.println( "|::::::::::::::::::::::::::::::::::::::::::::::::|" );
20     }
21 
22     public static void print48Ohs()
23     {
24         out.println( "|OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO|" );
25     }
26 
27     public static void print29Colons()
28     {
29         out.println( "|:::::::::::::::::::::::::::::|" );
30     }
31 
32     public static void printPledge()
33     {
34         out.println( "I pledge allegiance to the flag." );
35     }
36 
37     public static void print29Ohs()
38     {
39         out.println( "|OOOOOOOOOOOOOOOOOOOOOOOOOOOOO|" );
40     }
41 
42     public static void print6Stars()
43     {
44         out.print( "| *  *  *  *  *  * " );
45     }
46 
47     public static void print5Stars()
48     {
49         out.print( "|   *  *  *  *  *  " );
50     }
51 
52     public static void printSixStarLine()
53     {
54         print6Stars();
55         print29Ohs();
56     }
57 
58     public static void printFiveStarLine()
59     {
60         print5Stars();
61         print29Colons();
62     }
63 
64     public static void printTopHalf()
65     {
66         out.println( " ________________________________________________" ); //
1 space then 48 underscores
67         printSixStarLine();
68         printFiveStarLine();
69         printSixStarLine();
70         printFiveStarLine();
71         printSixStarLine();
72         printFiveStarLine();
73         printSixStarLine();
74     }
75 
76 }
```


### 你应该看到什么

```java

| * * * * * * |OOOOOOOOOOOOOOOOOOOOOOOOOOOOO|
|  * * * * * |:::::::::::::::::::::::::::::|
| * * * * * * |OOOOOOOOOOOOOOOOOOOOOOOOOOOOO|
|  * * * * * |:::::::::::::::::::::::::::::|
| * * * * * * |OOOOOOOOOOOOOOOOOOOOOOOOOOOOO|
|  * * * * * |:::::::::::::::::::::::::::::|
| * * * * * * |OOOOOOOOOOOOOOOOOOOOOOOOOOOOO|
|::::::::::::::::::::::::::::::::::::::::::::::::|
|OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO|
|::::::::::::::::::::::::::::::::::::::::::::::::|
|OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO|
|::::::::::::::::::::::::::::::::::::::::::::::::|
|OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO|
```

这个练习很荒谬。没有任何值得尊重的程序员会以这种方式在屏幕上绘制旗帜。如果编写这个程序感觉有点傻，那没关系。但是函数很重要，我更喜欢从你实际能理解的愚蠢例子开始，而不是从太难跟随的现实例子开始。

那么我们如何追踪执行这样的程序呢？我们从开始开始：`main()`的第一行。在第 7 行，`main`做的第一件事是调用函数`printTopHalf()`。所以`main`被暂停，执行跳到`printTopHalf()`函数的第一行，即第 66 行。

`printTopHalf` 的第一件事是在屏幕上打印一堆下划线，这将是我们旗帜的顶部。之后，执行移动到第 67 行，这是另一个函数调用！所以`main()`  仍然在暂停之前，等待`printTopHalf()`  完成，现在`printTopHalf()`  本身也在暂停，等待`printSixStarLine()`  完成并返回控制权到这里。

`printSixStarLine()` 从第 54 行开始，它调用`print6Stars()`  函数。那个函数（幸运的是）只在屏幕上显示一些东西，所以当`print6Stars()`  的右大括号出现在第 45 行时，它将控制权返回到`printSixStarLine()`  的第二行（第 55 行），然后又有一个函数调用。这通过`print29Ohs()`  函数的主体运行，并返回到第 56 行。然后`printSixStarLine()`  结束，将控制权返回到第 67 行的末尾。

在这一点上，我认为解释所有的函数调用会比跟随执行路径更加混乱，所以在这里我将按顺序打印所有执行的行号。调用一个函数会增加缩进级别，从该函数返回会减少缩进级别。

```java
5 ­ begin main
6
7 ­ call printTopHalf
    64 ­ begin printTopHalf
        65
        66
        67 ­ call printSixStarLine
            52 ­ begin printSixStarLine
                53
                54 ­ call print6Stars
                    42 ­ begin print6Stars
                        43
                        44
                        45 ­ end print6Stars
                54 ­ resume printSixStarLine
                55 ­ call print29Ohs
                    37 ­ begin print29Ohs
                        38
                        39
                        40 ­ end print29Ohs
                55 ­ resume printSixStarLine
                56 ­ end printSixStarLine
         67 ­ resume printTopHalf
             68 ­ call printFiveStarLine
                 58 ­ begin printFiveStarLine
                     59
                     60 ­ call print5Stars
                         47 ­ begin print5Stars
                             48
                             49
                             50 ­ end print5Stars
                     60 ­ resume printFiveStarLine
                     61 ­ call print29Colons
                         27 ­ begin print29Colons
                             28
                             29
                             30 ­ end print29Colons
                     61 ­ resume printFiveStarLine
                     62 ­ end printFiveStarLine
             68 ­ resume printTopHalf
             69 ­ call printSixStarLine
            52 ­ begin printSixStarLine
                53
                54 ­ call print6Stars
                    42 ­ begin print6Stars
                        43
                        44
                        45 ­ end print6Stars
                54 ­ resume printSixStarLine
                55 ­ call print29Ohs
                    37 ­ begin print29Ohs
                        38
                        39
                        40 ­ end print29Ohs
                55 ­ resume printSixStarLine
                56 ­ end printSixStarLine
         69 ­ resume printTopHalf
             70 ­ call printFiveStarLine
                 58 ­ begin printFiveStarLine
                     59
                     60 ­ call print5Stars
                         47 ­ begin print5Stars
                             48
                             49
                             50 ­ end print5Stars
                     60 ­ resume printFiveStarLine
                     61 ­ call print29Colons
                         27 ­ begin print29Colons
                             28
                             29
                             30 ­ end print29Colons
                     61 ­ resume printFiveStarLine
                     62 ­ end printFiveStarLine
         70 ­ resume printTopHalf
             71 ­ call printSixStarLine
            52 ­ begin printSixStarLine
                53
                54 ­ call print6Stars
                    42 ­ begin print6Stars
                        43
                        44
                        45 ­ end print6Stars
                54 ­ resume printSixStarLine
                55 ­ call print29Ohs
                    37 ­ begin print29Ohs
                        38
                        39
                        40 ­ end print29Ohs
                55 ­ resume printSixStarLine
                56 ­ end printSixStarLine
         71 ­ resume printTopHalf
             72 ­ call printFiveStarLine
                 58 ­ begin printFiveStarLine
                     59
                     60 ­ call print5Stars
                         47 ­ begin print5Stars
                             48
                             49
                             50 ­ end print5Stars
                     60 ­ resume printFiveStarLine
                     61 ­ call print29Colons
                         27 ­ begin print29Colons
                             28
                             29
                             30 ­ end print29Colons
                     61 ­ resume printFiveStarLine
                     62 ­ end printFiveStarLine
         72 ­ resume printTopHalf
             73 ­ call printSixStarLine
            52 ­ begin printSixStarLine
                53
                54 ­ call print6Stars
                    42 ­ begin print6Stars
                        43
                        44
                        45 ­ end print6Stars
                54 ­ resume printSixStarLine
                55 ­ call print29Ohs
                    37 ­ begin print29Ohs
                        38
                        39
                        40 ­ end print29Ohs
                55 ­ resume printSixStarLine
                56 ­ end printSixStarLine
         73 ­ resume printTopHalf
             74 ­ end printTopHalf
     7 ­ resume main
     8
     9 ­ call print48Colons
         17 ­ begin print48Colons
             18
             19
             20 ­ end print48Colons
     9 ­ resume main
     10 ­ call print48Ohs
         22 ­ begin print48Ohs
             23
             24
             25 ­ end print48Ohs
     10 ­ resume main
     11 ­ call print48Colons
         17 ­ begin print48Colons
             18
             19
             20 ­ end print48Colons
     11 ­ resume main
     12 ­ call print48Ohs
         22 ­ begin print48Ohs
             23
             24
             25 ­ end print48Ohs
     12 ­ resume main
     13 ­ call print48Colons
         17 ­ begin print48Colons
             18
             19
             20 ­ end print48Colons
     13 ­ resume main
     14 ­ call print48Ohs
         22 ­ begin print48Ohs
             23
             24
             25 ­ end print48Ohs
     14 ­ resume main
```

天哪！如果你能成功地追踪到这一点，那么你就已经在成为一个称职的程序员的路上了。

### 学习演练

1.  你真的没有完全追踪整个程序，是吗？好吧，回去做吧。这本书不叫“学习 Java 的一半”，对吧？打印出代码，拿起一支铅笔，在一个函数调用其他地方时画一条线，当函数返回时画一条线。完成后，它应该看起来有点像一盘石墨意面！

1.  在 32 到 35 行，你会找到一个名为`printPledge()`  的函数的定义。但是这个函数的输出从来没有出现过。为什么？在`main()`  的末尾添加一个函数调用来运行这个函数，以便它出现在旗帜下面。

    （尽管这个程序很邪恶，但我对那面旗帜感到非常自豪。如果你用尺子测量一切的尺寸，你会发现我的旗帜与真正的美国国旗的尺寸几乎一样。我实际上花了很长时间测量和调整一切。）

