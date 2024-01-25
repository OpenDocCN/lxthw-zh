## 练习 28：无限循环

有时让学生感到惊讶的是，制作一个重复“永远”的循环是多么容易。这些被称为“无限循环”，有时我们故意制造它们，但通常它们是逻辑错误的结果。这里有一个例子：


```java

 1 import java.util.Scanner;
 2 
 3 public class KeepGuessing
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8         int secret, guess;
 9 
10         secret = 1 + (int)(Math.random()*10);
11 
12         System.out.println( "I have chosen a number between 1 and 10. Try to 
guess it." );
13         System.out.print( "Your guess: " );
14         guess = keyboard.nextInt();
15 
16         while ( secret != guess )
17         {
18             System.out.println( "That is incorrect. Guess again." );
19             System.out.print( "Your guess: " );
20         }
21 
22         System.out.println( "That's right! You're a good guesser." );
23     }
24 }
```



### 你应该看到的是

```java

I have chosen a number between 1 and 10. Try to guess it.
Your guess: 4
That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: That is incorrect. Guess again.
Your guess: ^C
```

1.  例如，在大学时，我在网络协议课上的一个作业是写一个网络服务器。网络服务器监听网络以获取页面请求。然后它找到请求的页面并将其发送到请求的网络浏览器。然后它等待另一个请求。我在那个作业中故意使用了一个无限循环，因为网络服务器软件旨在在机器启动时自动启动，全天候运行，并且只在机器关闭时关闭。


程序实际上没有自行停止；在程序一遍又一遍地重复时，我不得不按下 CTRL-C 来停止它。

这段代码中有一个无限循环。第 16 行检查变量*secret*的值是否与变量*guess*的值不同。如果是，它执行循环体，如果不是，它跳过循环体到第 21 行。

问题是一旦*secret*和*guess*不同，程序就永远无法到达另一行代码来改变任一变量，所以循环将永远重复第 16 行到第 20 行。

所以当你写一个 while 循环的条件时，试着记住：“我需要确保这个条件最终会变成假”。

### 学习练习

1.  修复代码，使其不再产生无限循环。

