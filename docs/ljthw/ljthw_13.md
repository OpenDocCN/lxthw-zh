## 练习 12：布尔表达式

到目前为止，我们只看到了三种类型的变量：

#### 整数

整数，不带小数部分的数字（正数或负数）

#### 双精度

“双精度浮点”数字（正数或负数），可能有小数部分

#### 字符串

一个字符串是字符，保存单词、短语、符号、句子，无论什么

但用 Yoda 的话来说：“还有另一个。”“布尔”变量（以数学家乔治·布尔命名）不能保存数字或单词。它只能存储两个值中的一个：`true`或`false`。就是这样。我们可以用它们来执行逻辑。来看代码吧！

```java
 1 import java.util.Scanner;
 2 
 3 public class BooleanExpressions
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         boolean a, b, c, d, e, f;
10         double x, y;
11 
12         System.out.print( "Give me two numbers. First: " );
13         x = keyboard.nextDouble();
14         System.out.print( "Second: " );
15         y = keyboard.nextDouble();
16 
17         a = (x <  y);
18         b = (x <= y);
19         c = (x == y);
20         d = (x != y);
21         e = (x >  y);
22         f = (x >= y);
23 
24         System.out.println( x + " is LESS THAN " + y + ": " + a );
25         System.out.println( x + " is LESS THAN or EQUAL TO " + y + ": " + b );
26         System.out.println( x + " is EQUAL TO " + y + ": " + c );
27         System.out.println( x + " is NOT EQUAL TO " + y + ": " + d );
28         System.out.println( x + " is GREATER THAN " + y + ": " + e );
29         System.out.println( x + " is GREATER THAN or EQUAL TO " + y + ": " + f
);
30         System.out.println();
31 
32         System.out.println( !(x < y) + " " + (x >= y) );
33         System.out.println( !(x <= y) + " " + (x > y) );
34         System.out.println( !(x == y) + " " + (x != y) );
35         System.out.println( !(x != y) + " " + (x == y) );
36         System.out.println( !(x > y) + " " + (x <= y) );
37         System.out.println( !(x >= y) + " " + (x < y) );
38 
39     }
40 }
```

### 你应该看到的内容

```java

Give me two numbers. First: 3 Second: 4
3.0 is LESS THAN 4.0: true
3.0 is LESS THAN or EQUAL TO 4.0: true
3.0 is EQUAL TO 4.0: false
3.0 is NOT EQUAL TO 4.0: true
3.0 is GREATER THAN 4.0: false
3.0 is GREATER THAN or EQUAL TO 4.0: false

false false false false true true false false true true true true
```

在第 17 行，布尔变量 a 被设置为一些奇怪的东西：比较的结果。变量 x 中的当前值与变量 y 的值进行比较。如果 x 小于 y，则比较为真，并且布尔值`true`存储在 a 中。如果 x 不小于 y，则比较为假，并且布尔值`false`存储在 a 中。（我认为这比写起来更容易理解。）

第 18 行类似，只是比较是“小于或等于”，布尔结果存储在*b*中。

第 19 行是“等于”：如果 x 持有与 y 相同的值，c 将被设置为值`true`。第 20 行的比较是“不等于”。第 21 行和第 22 行分别是“大于”和“大于或等于”。

在第 24 行到第 29 行，我们在屏幕上显示了所有这些布尔变量的值。

第 32 行到第 37 行介绍了“非”运算符，即感叹号（`!`）。它取逻辑相反。因此，在第 32 行，我们显示“x 是否小于 y”的逻辑否定，并打印出“x 是否大于或等于 y”的真值，它们是等价的。（“小于”的相反是“大于或等于”。）第 33 行到第 37 行显示了其余关系运算符的相反情况。

