## 练习 33：名为“Pig”的骰子游戏

在上一课中，我们为骰子游戏*Pig*编写了计算机 A.I.（记住，如果你想要更多关于这个游戏的信息，你可以阅读维基百科关于 Pig 的条目。）在这一课中，我们将有整个游戏的代码，有一个人类玩家和一个计算机玩家轮流进行。

你上次写的整个程序大致对应于这个程序中的第 43 到 67 行。唯一的主要区别是，我们将有一个*turnTotal*变量来保存一个回合的点数，而*total2*变量则保存计算机从一轮到另一轮的总点数。

1 import java.util.Scanner; 2

3 public class PigDice 4 {

5 public static void main( String[] args ) 6 {

7 Scanner keyboard = new Scanner(System.in); 8

1.  int roll, total1, total2, turnTotal;

1.  String choice = ""; 11

1.  total1 = 0;

1.  total2 = 0; 14

15 do

16 {

1.  turnTotal = 0;

1.  System.out.println( "你有 " + total1 + " 点。" ); 19

20 do

21 {

1.  roll = 1 + (int)(Math.random()*6);

1.  System.out.println( "\t 你掷出了 " + roll + "。" );

1.  if ( roll == 1 )

25 {

1.  System.out.println( "\t 这结束了你的回合。" );

1.  turnTotal = 0;

28 }

29 else

30 {

1.  turnTotal += roll;

1.  System.out.println( "\t 你这一轮到目前为止有 " + turnTotal + " 点。" );

1.  System.out.print( "\t 你想再“roll”一次还是“hold”？ " );

1.  choice = keyboard.next(); 35 }

36 } while ( roll != 1 && choice.equals("roll") ); 37

1.  total1 += turnTotal;

1.  System.out.println( "\t 你以 " + total1 + " 点结束这一轮。" ); 40

41 if ( total1 < 100 )

42 {

1.  turnTotal = 0;

1.  System.out.println( "计算机有 " + total2 + " 点。" ); 45

46 do

47 {

1.  roll = 1 + (int)(Math.random()*6);

1.  System.out.println( "\t 计算机掷出了 " + roll + "。" );

1.  if ( roll == 1 )

51 {

1.  System.out.println( "\t 这结束了它的回合。" );

1.  turnTotal = 0;

54 }

55 else

56 {

1.  turnTotal += roll;

1.  System.out.println( "\t 计算机到目前为止这一轮有 " + turnTotal + " 点。" );

1.  if ( turnTotal < 20 )

60 {

61 System.out.println( "\t 计算机选择再次掷骰子。" ); 62 }

63 }

64

65

66

67

68

69

70

71

72

73

74

75

76

77

78

79

80

81

82 }

} while ( roll != 1 && turnTotal < 20 );

total2 += turnTotal;

System.out.println( "\t 计算机以 " + total2 + " 点结束这一轮。" );

}

} while ( total1 < 100 && total2 < 100 );

if ( total1 > total2 )

{

System.out.println( "人类获胜！" );

}

else

{

System.out.println( "计算机获胜。" );

}

}

### 你应该看到的是

```java

You have 0 points.
You rolled a 2.
You have 2 points so far this round.
Would you like to "roll" again or "hold"? roll You rolled a 1.
That ends your turn.
You end the round with 0 points.
Computer has 0 points.
Computer rolled a 6.
Computer has 6 points so far this round. Computer chooses to roll again.
Computer rolled a 6.
Computer has 12 points so far this round. Computer chooses to roll again.
Computer rolled a 1\. That ends its turn.
Computer ends the round with 0 points.
You have 0 points.
You rolled a 3.
You have 3 points so far this round.
Would you like to "roll" again or "hold"? roll You rolled a 5.
You have 8 points so far this round.
Would you like to "roll" again or "hold"? roll You rolled a 2.
You have 10 points so far this round.
Would you like to "roll" again or "hold"? roll You rolled a 2.
You have 12 points so far this round.
Would you like to "roll" again or "hold"? hold You end the round with 12 points.
Computer has 0 points.
Computer rolled a 5.
Computer has 5 points so far this round. Computer chooses to roll again.
Computer rolled a 4.
Computer has 9 points so far this round. Computer chooses to roll again.
Computer rolled a 4.
Computer has 13 points so far this round. Computer chooses to roll again.
Computer rolled a 3.
Computer has 16 points so far this round. Computer chooses to roll again.
Computer rolled a 5.
Computer has 21 points so far this round.
```

```java
Computer ends the round with 21 points.
You have 12 points.
You rolled a 2.
You have 2 points so far this round.
Would you like to "roll" again or "hold"? roll

...etc

Computer has 20 points so far this round. Computer ends the round with 102 points.
The computer wins.
```

我们从两个变量开始程序：*total1*保存人类的总点数，*total2*保存计算机的总点数。两者都从 0 开始。

然后在第 15 行开始一个非常庞大的 do-while 循环，基本上包含了整个游戏，直到第 70 行才结束。向下滚动，你会看到这个循环会重复，只要*total1*和*total2*都小于 100。当任一玩家达到 100 或更多时，条件不再成立，do-while 循环不会再重复。

然后在那个 do-while 循环结束之后（从第 72 行开始），有一个`if`语句和一个`else`来确定赢家。

让我们往上滚动一下，看看人类的回合，从第 17 行开始。*turnTotal*是人类到目前为止在这一轮中赚得的点数。由于这是一轮的开始，我们应该从 0 开始。

第 20 行是一个包含人类回合的 do-while 循环的开始。它在第 36 行结束，所有在第 20 行和第 36 行之间的代码都会重复，只要人类没有掷出 1，只要人类继续选择再次掷骰子。

人类的每次掷骰子都和计算机一样开始：选择一个从 1 到 6 的随机数。我们在第 22 行打印出来。

现在可能发生两件事：要么掷骰子是 1——人类失去本轮获得的所有分数——要么掷骰子是 2-6，然后将掷骰子的点数加到他们的*turnTotal*上。我们显示适当的消息，在第 33 和 34 行，我们给人类选择再次掷骰的机会，或者通过保持来安全地玩。然后在第 36 行，do-while 循环的条件将检查并在适当的情况下重复回到第 20 行。

一旦玩家的回合结束，我们将*turnTotal*（可能为 0）加到玩家的总分上，并显示他们当前的分数。

在第 41 行，计算机的回合开始了。然而，如果人类已经达到了 100 分，计算机就不会轮到了：在这种情况下游戏结束。因此，为了防止计算机玩游戏，我们必须将整个计算机的回合包装在一个大的`if`语句中，以便在人类的总分（total1）大于或等于 100 时跳过。这个`if`语句从第 41 行开始，到第 68 行结束。

所以在第 43 行，计算机的回合真正开始了。这基本上与上一个练习相同，所以我不会再解释一遍。请注意，计算机正在根据其回合总数决定是否继续掷骰子。

第 70 行结束了包含整个游戏的 do-while 循环，第 72 到 79 行确定并显示赢家。

希望你能够很好地跟上游戏的流程。这相当复杂。

我还要指出，对于这样一个程序来说，每次你放一个左大括号，将其后的所有内容缩进一级是*非常重要*的。如果你可以从第 47 行的左大括号直观地扫描你的眼睛到第 64 行的右大括号，看看 do-while 循环中有什么，没有什么，这将为你节省很多烦恼。

