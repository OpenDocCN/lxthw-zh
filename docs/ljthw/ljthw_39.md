## 练习 38：形状的面积

今天的练习没有什么新东西。这只是对函数的额外练习。这个程序有三个函数（如果算上`main`就有四个），它们都有参数，三个都有返回值。

```java

 1 import java.util.Scanner;
 2 
 3 public class ShapeArea
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         int choice;
10         double area = 0;
11 
12         System.out.println("Shape Area Calculator version 0.1 (c) 2013 
Mitchell Sample Output, Inc.");
13 
14         do
15         {
16             System.out.println("\n­=­=­=­=­=­=­=­=­=­=­=­=­=­=­\n");
17             System.out.println("1) Triangle");
18             System.out.println("2) Circle");
19             System.out.println("3) Rectangle");
20             System.out.println("4) Quit");
21             System.out.print("> ");
22             choice = keyboard.nextInt();
23 
24             if ( choice == 1 )
25             {
26                 System.out.print("\nBase: ");
27                 int b = keyboard.nextInt();
28                 System.out.print("Height: ");
29                 int h = keyboard.nextInt();
30                 area = computeTriangleArea(b, h);
31                 System.out.println("The area is " + area);
32             }
33             else if ( choice == 2 )
34             {
35                 System.out.print("\nRadius: ");
36                 int r = keyboard.nextInt();
37                 area = computeCircleArea(r);
38                 System.out.println("The area is " + area);
39             }
40             else if ( choice == 3 )
41             {
42                 System.out.print("\nLength: ");
43                 int length = keyboard.nextInt();
44                 System.out.print("Width: ");
45                 int width = keyboard.nextInt();
46                 System.out.println("The area is " + 
computeRectangleArea(length, width) );
47             }
48             else if ( choice != 4 )
49             {
50                 System.out.println("ERROR.");
51             }
52 
53         } while ( choice != 4 );
54 
55     }
56 
57     public static double computeTriangleArea( int base, int height )
58     {
59         double A;
60         A = 0.5 * base * height;
61         return A;
62     }
63 
64     public static double computeCircleArea( int radius )
65     {
66         double A;
67         A = Math.PI * radius * radius;
68         return A;
69     }
70 
71     public static int computeRectangleArea( int length, int width )
72     {
73         return (length * width);
74     }
75 }
```

### 你应该看到什么

```java
Shape Area Calculator version 0.1 (c) 2013 Mitchell Sample Output, Inc.
­=­=­=­=­=­=­=­=­=­=­=­=­=­=­
1) Triangle
2) Circle
3) Rectangle
4) Quit
> 1
Base: 3
Height: 5
The area is 7.5
­=­=­=­=­=­=­=­=­=­=­=­=­=­=­
1) Triangle
2) Circle
3) Rectangle
4) Quit
> 2
Radius: 3
The area is 28.274333882308138
­=­=­=­=­=­=­=­=­=­=­=­=­=­=­
1) Triangle
2) Circle
3) Rectangle
4) Quit
> 4
```

在第 57 行，我们定义了一个计算三角形面积的函数（这次只使用底边和高）。它需要两个参数，并将返回一个`double`值。在第 59 行，我们声明了一个名为 A 的变量。这个变量是函数“局部”的。尽管在第 66 行声明了一个名为 A 的变量，但它们并不是同一个变量。（就像有两个名叫“迈克尔”的朋友。只是因为他们有相同的名字并不意味着他们是同一个人。）

变量`b`（在第 27 行定义）的值作为函数调用中参数`base`的初始值传入。`b`被存储到`base`中，因为`b`是首先出现的，而不是因为`base`以`b`开头。

计算机对此并不在乎。只有顺序才重要。

在第 61 行，A 的值返回到`main`，最终被存储在名为 area 的变量中。在矩形面积函数的定义开始于第 71 行时，我做了三件奇怪的事情。

首先，形式参数与实际参数具有相同的名称。（记住，参数是函数定义中声明的变量，位于第 71 行，参数是函数调用中括号中的变量。）这是一个巧合，但并不意味着什么。这就像一个名叫“史蒂文”的演员扮演一个名叫“史蒂文”的角色。`main`版本的 length 的值被存储到`computeRectangleArea`的 length 变量中，因为它们都在括号中首先列出，没有其他原因。

其次，我没有费心为函数将要返回的值创建一个变量。我只是返回了表达式`length*width`的值。函数会计算出值并立即返回，而不会将其存储到变量中。

第三，矩形面积值在第 46 行返回到`main`，但我没有费心将返回值存储到变量中：我直接在屏幕上打印出来。(我在`HeronsFormula`中也这样做了，但我没有特别指出。)这是完全可以的，实际上非常常见。我们经常调用函数，几乎总是使用函数的返回值，但我们并不总是需要将返回值存储到自己的变量中。

最后，在我们转到另一个话题之前，我应该提到，在 Java 中，函数只能返回一个值。在其他一些编程语言中，函数可以返回多个值。但在 Java 中，函数可以返回一个值或没有值（如果函数是`void`），但绝不会超过一个。

P.S.这些函数有点傻。如果我*真的*需要一个形状面积计算器，我不确定是否值得为一个只有一行代码的方程创建一个完整的函数。但是这个例子用来解释是很好的。

### 学习演练

1. 添加一个计算正方形面积的函数。也将其添加到菜单中。

