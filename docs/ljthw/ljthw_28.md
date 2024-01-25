## 练习 27：一个猜数字游戏

现在你知道如何使用`while`循环重复某些内容，我们将编写一个实际上另一个人可能会喜欢运行的程序？你对此和我一样兴奋吗？

```java
 1 import java.util.Scanner;
 2 
 3 public class HighLow
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8         int secret, guess;
 9 
10         secret = 1 + (int)(Math.random()*100);
11 
12         System.out.println( "I'm thinking of a number between 1­100. Try to 
guess it." );
13         System.out.print( "> " );
14         guess = keyboard.nextInt();
15 
16         while ( secret != guess )
17         {
18             if ( guess < secret )
19             {
20                 System.out.println( "Sorry, your guess is too low. Try again."
);
21             }
22             if ( guess > secret )
23             {
24                 System.out.println( "Sorry, your guess is too high. Try 
again." );
25             }
26             System.out.print( "> " );
27             guess = keyboard.nextInt();
28         }
29 
30         System.out.println( "You guessed it! What are the odds?!?" );
31     }
32 }
```


### 你应该看到的是

```java

I'm thinking of a number between 1­100\. Try to guess it.
> 50
Sorry, your guess is too high. Try again.
> 25
Sorry, your guess is too high. Try again.
> 13
Sorry, your guess is too low. Try again.
> 20
Sorry, your guess is too high. Try again.
> 16
Sorry, your guess is too high. Try again.
> 18
Sorry, your guess is too high. Try again.
> 14
Sorry, your guess is too low. Try again.
> 15
You guessed it! What are the odds?!?
```

所以在第 10 行，计算机从 1 到 100 中选择一个随机数，并将其存储到变量*secret*中。我们让人类猜测。

第 16 行有一个`while`循环。它说“只要变量 secret 的值与变量 guess 的值不同...运行以下代码块。”第 17 行到第 28 行是循环的主体。每当条件为真时，这十二行代码都会被执行。

在循环体内，我们有几个`if`语句。我们已经知道人类的猜测与秘密数字不同，否则我们就不会一开始就进入`while`循环！但我们不知道猜测是错误是因为它太低还是因为它太高，所以这些`if`语句找出来并显示适当的错误消息。

然后在显示错误消息后，第 27 行我们允许他们再次猜测。人类（希望）输入一个数字，然后存储到变量*guess*中，覆盖该变量中的先前猜测。

然后程序循环回到第 16 行并再次检查条件。如果条件仍然为真（他们的猜测仍然不等于秘密数字），则整个循环体将再次执行。如果条件现在为假（他们猜中了），则整个循环体将被跳过，程序将跳到第 29 行。

如果循环结束，我们知道条件为假。所以我们不需要在这里加一个新的`if`语句；安全地打印“你猜对了”。

