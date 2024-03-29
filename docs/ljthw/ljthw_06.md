## 练习 5：在变量中保存信息

如果程序只能在屏幕上打印东西，那就太无聊了。我们希望我们的程序是互动的。

不幸的是，互动需要几个不同的概念共同工作，一次解释所有这些可能会令人困惑。所以我会一个一个地介绍它们。

首先是：变量！如果你上过代数课，你就会熟悉数学中的变量概念。编程语言也有变量，基本概念是一样的：

“变量是指向保存值的位置的名称。” Java 中的变量与数学变量有四个主要区别：

1.  变量名可以超过一个字母长。

1.  变量不仅可以保存数字，还可以保存单词。

1.  当变量首次创建时，你必须选择变量将保存的值的类型。

1.  变量的值（但不是它的类型）可以在程序中改变。变量`score`可能一开始的值是`0`，但到程序结束时，`score`可能保存的值是`413500`。

好了，讨论够了。让我们开始写代码吧！我不会告诉你文件的名字应该是什么。你得自己弄清楚。

```java
 1 public class CreatingVariables
 2 {
 3     public static void main( String[] args )
 4     {
 5         int x, y, age;
 6         double seconds, e, checking;
 7         String firstName, last_name, title;
 8 
 9         x = 10;
10         y = 400;
11         age = 39;
12 
13         seconds = 4.71;
14         e = 2.71828182845904523536;
15         checking = 1.89;
16 
17         firstName = "Graham";
18         last_name = "Mitchell";
19         title = "Mr.";
20 
21         System.out.println( "The variable x contains " + x );
22         System.out.println( "The value " + y + " is stored in the variable y." );
23         System.out.println( "The experiment completed in " + seconds + " seconds." );
24         System.out.println( "My favorite irrational number is Euler's constant: " + e );
25         System.out.println( "Hopefully your balance is more than $" + checking + "!" );
26         System.out.println( "My full name is " + title + " " + firstName + last_name );
27     }
28 }
```


### 你应该看到什么

```java

The variable x contains 10
The value 400 is stored in the variable y. The experiment completed in 4.71 seconds.
My favorite irrational number is Euler's constant: 2.718281828459045 Hopefully your balance is more than $1.89!
My full name is Mr. GrahamMitchell
```

在第 5 到 7 行，我们声明了九个变量。前三个分别命名为`x`，`y`和`age`。这三个变量都是“整数”，这是一种可以保存正负两十亿之间的值的变量类型。

一个整数变量可以保存值`10`。它可以保存值`­8192`。一个整数变量可以保存`123456789`。它不能保存值`3.14`，因为这有小数部分。一个整数变量也不能保存值`10000000000`，因为一百亿太大了。

在第 6 行，我们声明了变量`seconds`，`e`和`checking`。这三个变量都是`double`，这是一种可以保存可能有小数部分的数字的变量类型。

一个双精度变量可以保存值`4.71`。它可以保存值`­8192`。（它可能有小数部分，但不一定有。）它几乎可以保存`±1.79769 × 10308`和`4.94065 × 10­324`之间的任何值。

然而，双精度有限的精度。请注意，在第 14 行，我将值`2.71828182845904523536`存储到名为`e`的变量中，但当我在第 24 行打印出该值时，只有`2.718281828459045`出现。双精度没有足够的有效数字来精确保存值`2.71828182845904523536`。整数具有完美的精度，但只能保存整数，不能保存巨大的值。

我们在这个练习中要看的最后一种变量类型是`String`。在第 7 行，我们声明了三个`String`变量：`firstName`，`last_name`和`title`。`String`变量可以保存单词和短语；名称缩写为“字符串”。

在第 9 到 11 行，我们初始化 4 三个整数值。值`10`被存储到`x`中。在此之前，变量`x`存在，但其值未定义。`400`被存储到`y`中，`39`被存储到变量`age`中。

第 13 到 15 行给三个双精度变量赋初始值，第 17 到 19 行初始化了三个字符串变量。然后第 21 到 26 行在屏幕上显示了这些变量的值。请注意，变量名没有用引号括起来。

我知道对于这样的程序使用变量是没有意义的，但很快一切都会变得清晰起来。

1.  声明-告诉程序变量的名称（或“标识符”）和类型。‌

1.  初始化-给变量赋予其第一个（或“初始”）值。

