## 练习 6：数学运算


现在我们知道如何在 Java 中声明和初始化变量，我们可以用这些变量进行一些数学运算。

```java
 1 public class MathOperations
 2 {
 3     public static void main( String[] args )
 4     {
 5         int a, b, c, d, e, f, g;
 6         double x, y, z;
 7         String one, two, both;
 8 
 9         a = 10;
10         b = 27;
11         System.out.println( "a is " + a + ", b is " + b );
12 
13         c = a + b;
14         System.out.println( "a+b is " + c );
15         d = a ­ b;
16         System.out.println( "a­b is " + d );
17         e = a+b*3;
18         System.out.println( "a+b*3 is " + e );
19         f = b / 2;
20         System.out.println( "b/2 is " + f );
21         g = b % 10;
22         System.out.println( "b%10 is " + g );
23 
24         x = 1.1;
25         System.out.println( "\nx is " + x );
26         y = x*x;
27         System.out.println( "x*x is " + y );
28         z = b / 2;
29         System.out.println( "b/2 is " + z );
30         System.out.println();
31 
32         one = "dog";
33         two = "house";
34         both = one + two;
35         System.out.println( both );
36     }
37 }
```

### 你应该看到什么

```java

a is 10, b is 27
a+b is 37
a­b is ­17
a+b*3 is 91
b/2 is 13
b%10 is 7

x is 1.1
x*x is 1.2100000000000002
b/2 is 13.0

doghouse
```

加号（`+`）将两个整数或两个双精度数相加，或一个整数和一个双精度数（顺序不限）。对于两个字符串（就像在第 34 行），它将把这两个字符串连接在一起。

1.  “连接”-将字符字符串端对端连接。

减号（`-`）将一个数字减去另一个数字。就像加法一样，它适用于两个整数、两个双精度数，或一个整数和一个双精度数（顺序不限）。

星号（`*`）用于表示乘法。您还可以在第 17 行看到 Java 知道正确的运算顺序。`b` 乘以 3 得到`81`，然后加上 `a`。

斜杠（`/`）用于除法。请注意，当一个整数被另一个整数除（就像在第 19 行），结果也是一个整数而不是一个双精度数。

百分号（`%`）用于表示“模数”，本质上是除法后剩下的余数。在第 21 行，b 被`10`除，余数（`7`）被存储到变量 `g` 中。

### 常见学生问题

+   为什么`1.1`乘以`1.1`等于`1.2100000000000002`而不是`1.21`？为什么 0.333333 + 0.666666 等于 0.999999 而不是 1.0？有时候在数学中我们会得到重复的小数，大多数计算机在处理它们之前会将数字转换为二进制。结果是`1.1`在二进制中是一个重复的小数。

记住我在上一个练习中说的：双精度的问题在于有限的精度。在本书中，你大多数时候可以忽略这个事实，但我希望你能记住双精度变量有时会给出*略微*不同于你期望的值。

