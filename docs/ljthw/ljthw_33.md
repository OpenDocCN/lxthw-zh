## 练习 32：为骰子游戏添加值

Pig 是一个简单的骰子游戏，适用于两个或更多玩家。（如果您想了解更多信息，可以阅读维基百科关于 Pig 的条目。）基本思想是成为第一个“存入”100 分的人。当您掷出 1 时，您的回合结束，这一回合您不会获得任何分数。任何其他掷骰都会增加您这一回合的分数，但只有在您决定“保留”时才能保留这些分数。如果在保留之前掷出 1，那么您这一回合的所有分数都将丢失。


您已经掌握了整个 Pig 游戏的代码，但与您之前看到的较小程序相比，这是一次性的*很多*，所以我将把它分成两节课。今天我们只会为计算机玩家编写人工智能（A.I.）代码。这个计算机玩家将使用“在 20 时保留”策略，这意味着计算机会继续掷骰，直到他们这一回合的分数达到 20 或更多，然后无论如何都会保留。这实际上并不是一个糟糕的策略，而且编码起来也很容易。

```java
 1 import java.util.Scanner;
 2 
 3 public class PigDiceComputer
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         int roll, total;
10 
11         total = 0;
12 
13         do
14         {
15             roll = 1 + (int)(Math.random()*6);
16             System.out.println( "Computer rolled a " + roll + "." );
17             if ( roll == 1 )
18             {
19                 System.out.println( "\tThat ends its turn." );
20                 total = 0;
21             }
22             else
23             {
24                 total += roll;
25                 System.out.println( "\tComputer has " + total + " points so far this 
round." );
26                 if ( total < 20 )
27                 {
28                     System.out.println( "\tComputer chooses to roll again." );
29                 }
30             }
31         } while ( roll != 1 && total < 20 );
32 
33         System.out.println( "Computer ends the round with " + total + " points." );
34 
35     }
36 }
```

### 预期输出

```java

Computer rolled a 2.
Computer has 2 points so far this round. Computer chooses to roll again.
Computer rolled a 3.
Computer has 5 points so far this round. Computer chooses to roll again.
Computer rolled a 1.
That ends its turn.
Computer ends the round with 0 points.
```

基本上整个程序都在一个大的`do-while`循环体中，告诉计算机何时停止：要么掷出 1，要么总数达到 20 或更多。只要掷骰不是 1 *并且*总数小于 20，条件就会成立，循环将从开始重新开始（在第 13 行）。我们选择`do-while`循环是因为我们希望计算机无论如何都至少掷一次骰子。

掷骰发生在第 15 行：从 1 到 6 的随机数字是掷骰的良好替代品。

在第 17 行，我们检查是否掷出了 1。如果是，所有分数都将丢失。如果不是（`else`），我们将此次掷骰的分数加到总分上。请注意我们使用了“加等于”，这是我们以前见过的。

第 26 行的`if`语句只是为了得到一个漂亮的消息，即计算机将再次掷骰。不错，对吧？所以下一课我们将回来玩完整的游戏！

### 学习演练

1. 找到一个骰子（技术上应该是“骰子”，因为“骰子”是复数形式，而您只需要一个）或找到一个模拟掷骰子的应用程序或网站。拿出一张纸和一支笔。在纸张中间画一条线并制作两列。在左列上标注“掷骰”，在右列上标注“总数”。在总数列中放入`0`，并一开始将另一列留空。

然后掷骰子，并将您掷出的数字写在掷骰列的顶部。由于骰子掷出的行号是代码中的第 15 行，所以在掷骰值旁边用括号括起数字`(15)`。

然后逐行执行代码，就像计算机一样。将掷骰的当前值与 1 进行比较。如果它们相等，则划掉总数列中的当前值，并在那里放入`0 (20)`，因为总数将在代码的第 20 行变为零。

继续进行，直到程序结束。以下是程序“预期输出”部分所示程序示例运行的表格样式示例。

| 掷骰 | 总数 |
| --- | --- |
| 0 (11) | |
| | 2 (15) |
| 2 (24) | |
| | 3 (15) |
| 5 (24) | |
| | 1 (15) |
| 0 (20) | |

