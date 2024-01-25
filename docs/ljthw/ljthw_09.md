## 练习 8：存储人类的回答


在上一个练习中，你学会了如何暂停程序并允许人类输入一些东西。但是输入的内容发生了什么？当你为第一个问题输入“巴黎”时，答案去哪了？嗯，它在输入后立即被丢弃了，因为我们没有放置任何指令告诉 Scanner 对象在哪里存储它。所以这就是今天课程的主题。

```java
 1 import java.util.Scanner;
 2 
 3 public class RudeQuestions
 4 {
 5     public static void main( String[] args )
 6     {
 7         String name;
 8         int age;
 9         double weight, income;
10 
11         Scanner keyboard = new Scanner(System.in);
12 
13         System.out.print( "Hello. What is your name? " );
14         name = keyboard.next();
15 
16         System.out.print( "Hi, " + name + "! How old are you? " );
17         age = keyboard.nextInt();
18 
19         System.out.println( "So you're " + age + ", eh? That's not old at all." );
20         System.out.print( "How much do you weigh, " + name + "? " );
21         weight = keyboard.nextDouble();
22 
23         System.out.print( weight + "! Better keep that quiet. Finally, what's your income, " + 
name + "? " );
24         income = keyboard.nextDouble();
25 
26         System.out.println( "Hopefully that is " + income + " per hour and not per year!" );
27         System.out.println( "Well, thanks for answering my rude questions, " + name + "." );
28     }
29 }
```

（抱歉，第 23 行像那样换行了。我不想因为那一行而使字体变得微小。就像平常一样，把它都写在一行上。）

就像上一个练习一样，当你第一次运行这个程序时，它只会显示第一个问题，然后暂停，等待回答。

```java

Hello. What is your name?
```

请注意，因为第 13 行的第一个打印语句是`print()`而不是`println()`，光标会留在问题所在行的末尾闪烁。如果你使用了`println()`，光标会在下一行的开头闪烁。

### 你应该看到什么

```java

Hello. What is your name? Brick Hi, Brick! How old are you? 25
So you're 25, eh? That's not old at all. How much do you weigh, Brick? 192
192.0! Better keep that quiet. Finally, what's your income, Brick? 8.75 Hopefully that is 8.75 per hour and not per year!
Well, thanks for answering my rude questions, Brick.
```

在程序的顶部，我们声明了四个变量：一个名为*name*的字符串变量，一个名为*age*的整数变量，以及两个名为*weight*和*income*的双精度变量。

在第 14 行，我们看到了`keyboard.next()`，我们知道它来自上一个练习，它会暂停程序并让人类输入一些东西，然后将其打包成一个字符串。那么他们输入的字符串去哪了呢？在这种情况下，我们将该值存储到名为“name”的字符串变量中。字符串值被存储到了一个字符串变量中。不错。

所以，假设你在第 14 行为你的名字输入了`Brick`，字符串值`"Brick"`就会被存储到第 14 行的变量名中。这意味着在第 16 行，我们可以在屏幕上显示该值！如果你问我，这相当酷。

在第 17 行，我们要求 Scanner 对象让人类输入一些东西，它将尝试将其格式化为整数，然后该值将被存储到名为*age*的整数变量中。我们在第 19 行将该值显示在屏幕上。

第 21 行读取一个双精度值并将其存储到*weight*中，第 24 行读取另一个双精度值并将其存储到*income*中。

这是一件非常强大的事情。有了一些变量和 Scanner 对象的帮助，我们现在可以让人类输入信息，并且可以在程序中稍后使用变量来记住它！

在我结束之前，注意例如变量*income*在第 9 行上被声明（我们选择了它的名称和类型），但直到第 24 行之前它都是未定义的（它没有值）。在第 24 行*income*最终被初始化（给出了程序的第一个值）。如果你在第 24 行之前尝试打印*income*的值，程序将无法编译。

无论如何，尝试输入不同的答案来回答问题，并看看你是否能在每个问题后让程序崩溃。

