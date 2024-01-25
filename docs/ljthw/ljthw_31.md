## 练习 30：Do-While 循环

在这个练习中，我要做一些我通常不做的事情。我要向你展示在 Java 中制作循环的另一种方法。因为你只看了四个练习的`while`循环，向你展示一种不同类型的循环可能会让你感到困惑。通常我喜欢等到学生做了很长时间的事情后再向他们展示做同样事情的新方法。

所以如果你认为你会感到困惑，随时可以跳过这个练习。这几乎不会伤害你，你可以在更有信心的时候再回来。

无论如何，在 Java 中有几种制作循环的方法。除了`while`循环之外，还有 do-while 循环。它们几乎相同，因为它们都在括号中检查条件。如果条件为真，则执行循环体。如果条件为假，则跳过循环体（或停止循环）。

那么有什么区别呢？输入代码，然后我们再谈论它。

```java

1 import java.util.Scanner; 2
3 public class CoinFlip
4 {
5

public static void main( String[] args )
6

{
7

Scanner keyboard = new Scanner(System.in);
8

9

String coin, again;
10

int flip, streak = 0;
11

12

do
13

{
14

flip = 1 + (int)(Math.random()*2);
15

16

if ( flip == 1 )
17

coin = "HEADS";
18

else
19

coin = "TAILS";
20

21

System.out.println( "You flip a coin and it is... " + coin );
22

23

if ( flip == 1 )
24

{
25

streak++;
26

System.out.println( "\tThat's " + streak + " in a row...." );
27

System.out.print( "\tWould you like to flip again (y/n)? " );
28

again = keyboard.next();
29

}
30

else
31

{
32

streak = 0;
33

again = "n";
34

}
35

} while ( again.equals("y") );
36

37

System.out.println( "Final score: " + streak );
38

}
39
}

```

### 你应该看到什么

```java
You flip a coin and it is... HEADS That's 1 in a row....
Would you like to flip again (y/n)? y You flip a coin and it is.  HEADS
That's 2 in a row....
Would you like to flip again (y/n)? y You flip a coin and it is.  HEADS
That's 3 in a row....
Would you like to flip again (y/n)? n Final score: 3
```

`while`循环和 do-while 循环之间只有两个区别。

1.  `while`循环的条件在循环体之前，但是 do-while 循环在循环体之前有关键字`do`，条件在循环体结束后，紧跟着右花括号。 （并且在循环条件的右括号后有一个分号，而`while`循环没有。）

1.  `while`循环在进入循环体之前检查它们的条件，但是 do-while 循环无论如何都会运行一次循环体，并且只在第一次通过后检查条件。

在计算机科学领域，`while`循环被称为“前测试”循环（因为它首先检查条件），而 do-while 被称为“后测试”循环（因为它在之后检查条件）。

如果`while`循环的条件在第一次检查时为真，那么使用`while`循环的代码和使用 do-while 循环的等效代码将表现完全相同。任何你可以用`while`循环做的事情，你也可以用 do-while 循环（和稍微不同的代码）做，反之亦然。

那么为什么 Java 的开发者要费心制作 do-while 循环呢？因为有时你在条件中检查的是一些在至少执行一次循环体后才知道的东西。

在这种情况下，我们通过选择 1-2 之间的随机数来抛硬币，并使用`if`语句。然后我们问他们是否想再抛一次或停止。如果他们说想再抛一次，我们的循环条件会重复。

如果我们用`while`循环来做这个，条件会是这样的：

```java

while ( again.equals("y") )
{
```

这是可以的，也可以工作，但是变量*again*直到第 28 行才得到一个值。所以我们的代码不会编译，因为*again*（用 Java 编译器的话）“可能尚未初始化”。所以我们必须在循环之前给它一个没有意义的值，只是为了取悦编译器。

这很烦人，所以 do-while 循环允许我们保持条件不变，但等到最后再检查它。这很方便。

### 学习训练

1.  更改代码，使用`while`循环代替 do-while 循环。确保它能编译并且运行结果相同。

1.  将它改回 do-while 循环。（当你忘记如何编写 do-while 循环时，你可能会回头看这段代码，我们不希望你唯一的例子被改成`while`循环。）

