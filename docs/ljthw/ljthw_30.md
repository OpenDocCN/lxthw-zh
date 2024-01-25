## 练习 29：使用循环进行错误检查

到目前为止，在这本书中，我们大多数时间都在忽略错误检查。我们假设人类会遵循指示，如果他们的缺乏方向性导致我们的程序出错，我们只是责怪用户，不予理会。

当你只是在学习时，这是完全可以的。错误检查很难，这就是为什么大多数大型程序都有错误，并且需要一整群人非常努力地工作，以确保软件尽可能少地出现错误。

但是你终于到了能够编写一点错误检查的程度。

```java
 1 import java.util.Scanner;
 2 
 3 public class SafeSquareRoot
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8         double x, y;
 9 
10         System.out.print("Give me a number, and I shall find the square root 
of it. ");
11         System.out.print("(No negatives, please.) ");
12         x = keyboard.nextDouble();
13 
14         while ( x < 0 )
15         {
16             System.out.print("Sorry, I won't take the square root of a 
negative.\nNew number: ");
17             x = keyboard.nextDouble();
18         }
19 
20         y = Math.sqrt(x);
21 
22         System.out.println("The square root of "+x+" is "+y);
23     }
24 }
```


### 你应该看到的

```java

Give me a number, and I shall find the square root of it. (No negatives, please.)
­8
Sorry, I won't take the square root of a negative. New number: ­7
Sorry, I won't take the square root of a negative. New number: ­200
Sorry, I won't take the square root of a negative. New number: 5
The square root of 5.0 is 2.23606797749979
```

从第 14 行开始是我所说的“输入保护循环”的一个例子。在第 20 行，我们将对变量 x 中的任何值取平方根，并且在这样做之前，我们希望确保它包含一个正数。（Java 没有内置支持虚数。）我们可以使用内置的绝对值函数`Math.abs()`，但我想演示错误检查，好吗？

在第 12 行，我们让人类输入一个数字。我们已经很客气地要求他们只输入一个正数，但他们可以输入任何他们喜欢的东西。（他们甚至可以输入“Mister Mxyzptlk”，但我们的错误检查技能还不够先进，无法幸存下来。）

所以在第 14 行，我们检查他们是否遵守了指示。如果*x*中的值为负数（小于零），我们会打印出一个错误消息，让他们再试一次。然后，在他们输入新数字之后，我们*回到*第 14 行，检查条件是否仍然为真。他们是否仍然没有遵循指示？如果是，再次显示错误消息并给他们另一个机会。

计算机不会不耐烦或无聊，所以人类**被困**在这个循环中，直到他们遵守。他们可以输入负数两十亿次，每次计算机都会礼貌地抱怨并让他们重新输入。

最终，人类会变得聪明，输入一个非负数。然后`while`循环的条件将为假（终于），循环的主体将被跳过（终于），执行将在第 20 行继续，我们可以安全地计算一个我们知道是正数的数的平方根。

真正的程序到处都有这样的东西。你必须这样做，因为人类不可靠，经常做出意想不到的事情。当你的孩子在程序运行时拉起笔记本电脑并开始乱按键时会发生什么？我们希望程序不会崩溃。

哦，你有没有注意到？我在这个程序中改变了一些东西。到目前为止，我在这本书中每次在屏幕上打印东西时，我都在括号和引号之间放了一个空格，就像这样：

```java

System.out.println( "This is a test." );
```

我这样做是因为我想要清楚地表明引号内的东西（技术上称为“字符串文字”）是一回事，而括号是另一回事。但是 Java 实际上并不在乎这些空格。（记住我充满了谎言。）如果你去掉空格，你的程序仍然会编译并且工作得和原来一样：

```java

System.out.println("This is a test.");
```

你可能已经注意到，在第 22 行，我甚至省略了字符串文字和加号之间的空格。这样的间距不会影响 Java 程序的语法，尽管许多公司和其他软件编写团体都有“样式指南”，告诉你如果你想让团体的其他成员满意，应该以什么样的方式格式化你的代码。

有些人对此非常激动。他们认为你应该始终使用空格来缩进你的代码，或者始终将代码块的开放大括号放在上一行的末尾：

```java

if ( age < 16 ) { 
    allowed = false;
}
```

…就像那样。我认为对于你自己的代码，你应该尝试其他风格，并做让你快乐的事情。当你和其他人一起工作时，你应该以让他们满意的方式格式化代码。

甚至有一些工具可以自动更改代码的格式以适应特定的风格！（搜索“源代码美化器”或“Java 代码美化器”来看一些例子。）

### 学习方法

1. 不要使用输入保护循环，使用`if`语句和`Math.abs()`来处理负数的平方根。当数字为负时，取正数的平方根，并在答案旁边打印一个小的`"i"`。

