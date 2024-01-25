## 练习 37：从函数返回一个值

有些函数有参数，有些没有。参数是将值*传递*到函数的唯一方法。也只有一种方法可以从函数中得到一个值：返回值。

这个练习给出了一个具有三个参数（三角形的边长）和一个输出（使用海伦公式计算三角形的面积）的函数的例子。

```java
 1 public class HeronsFormula
 2 {
 3     public static void main( String[] args )
 4     {
 5         double a;
 6 
 7         a = triangleArea(3, 3, 3);
 8         System.out.println("A triangle with sides 3,3,3 has an area of " + a );
 9 
10         a = triangleArea(3, 4, 5);
11         System.out.println("A triangle with sides 3,4,5 has an area of " + a );
12 
13         a = triangleArea(7, 8, 9);
14         System.out.println("A triangle with sides 7,8,9 has an area of " + a );
15 
16         System.out.println("A triangle with sides 5,12,13 has an area of " + 
triangleArea(5, 12, 13) );
17         System.out.println("A triangle with sides 10,9,11 has an area of " + 
triangleArea(10, 9, 11) );
18         System.out.println("A triangle with sides 8,15,17 has an area of " + 
triangleArea(8, 15, 17) );
19     }
20 
21     public static double triangleArea( int a, int b, int c )
22     {
23         // the code in this function computes the area of a triangle whose sides have 
lengths a, b, and c
24         double s, A;
25 
26         s = (a+b+c) / 2;
27         A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
28 
29         return A;
30         // ^ after computing the area, "return" it
31     }
32 }
```

### 你应该看到什么

```java

A triangle with sides 3,3,3 has an area of 2.0 A triangle with sides 3,4,5 has an area of 6.0
A triangle with sides 7,8,9 has an area of 26.832815729997478 A triangle with sides 5,12,13 has an area of 30.0
A triangle with sides 10,9,11 has an area of 42.42640687119285 A triangle with sides 8,15,17 has an area of 60.0
```

你可以看到函数`triangleArea`有三个参数。它们都是整数，它们的名字分别是 a、b 和 c。正如你已经知道的，这意味着我们不能在不提供三个整数值作为参数的情况下调用函数。

除此之外，`triangleArea`函数返回一个值。请注意，在第 21 行，它没有在`public static`和`triangleArea`之间说`void`。它说`double`。这意味着“这个函数返回一个值，它返回的值的类型是`double`。”

如果在这个位置上有关键字`void`，这意味着“这个函数不返回任何值。” 如果我们想让`triangleArea`返回不同类型的值：

```java
public static int     triangleArea( int a, int b, int c ) // this would return an
int
public static String  triangleArea( int a, int b, int c ) // this would return a 
String
public static boolean triangleArea( int a, int b, int c ) // this would return 
either true or false
public static void    triangleArea( int a, int b, int c ) // this cannot return 
any value of any type
```

有时我的学生会对返回值和不返回值的函数感到困惑。类比是有帮助的。

假设我们坐在我的学校教室里。我们听到雷声，我记得我把车窗开着。我不想让雨水把车里弄湿，所以我让你出去停车场。

“学生，请出去停车场，把我的车窗摇上。” “好的，先生，”你说。

如果你需要我关于我的车是什么样子的信息，那么这些就是参数。如果你已经知道哪辆是我的，你就不需要参数。

最终你返回并说“我完成了任务。”这种类型的函数不返回值。

```java

rollUpWindows(); // if you don't need parameters

rollUpWindows("Toyota", "Corolla", 2008, "blue"); // if you do need parameters
```

无论哪种情况，函数都会被执行并完成其任务，但不返回任何值。现在，例子#2：

我们再次在我的教室里。我正在网上更新我的汽车保险，网页要求我输入我的车牌号。我不记得了，所以我让你去停车场帮我拿。

最终你返回并*告诉我车牌号*。也许你把它写在一张纸上，也许你记住了。当你给我时，我自己抄下来。这种类型的函数返回一个值。

```java

String plate;

plate = retrieveLicensePlate(); // if you don't need parameters

plate = retrieveLicensePlate("Toyota", "Corolla", 2008, "blue"); // if you do need them
```

如果我粗鲁，你可以回到我的教室，把值给我，我可以把手指放在耳朵上，这样我就听不到你，或者拒绝自己写下来，这样我很快就会忘记它。如果你调用一个返回值的函数，你可以选择*不*将返回值存储到一个变量中，而是让这个值消失：

```java

retrieveLicensePlate("Toyota", "Corolla", 2008, "blue"); // returns a value which is lost

triangleArea(3, 3, 3); // returns the area but we refuse to store it into a variable
```

这通常是一个坏主意，但也许你有你的理由。

无论如何，在第 10 行我们调用`triangleArea`函数。我们传入`3`、`4`和`5`作为三个参数。`3`被存储为 a 的值（在第 21 行）。`4`被存储为 b，`5`被放入

c. 使用这些参数值运行第 23 到 28 行的所有代码。最后，变量 A 中存储了一个值。

在第 29 行，我们*返回*变量*A*中的值。这个值返回到第 10 行，存储到变量*a*中。

为了确保你能明白函数值得麻烦的原因，这里有一个例子，写出了同样的程序，但没有使用函数。

```java

 1 public class HeronsFormulaNoFunction
 2 {
 3     public static void main( String[] args )
 4     {
 5         int a, b, c;
 6         double s, A;
 7 
 8         a = 3;
 9         b = 3;
10         c = 3;
11         s = (a+b+c) / 2;
12         A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
13         System.out.println("A triangle with sides 3,3,3 has an area of " + 
A );
14 
15         a = 3;
16         b = 4;
17         c = 5;
18         s = (a+b+c) / 2;
19         A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
20         System.out.println("A triangle with sides 3,4,5 has an area of " + 
A );
21 
22         a = 7;
23         b = 8;
24         c = 9;
25         s = (a+b+c) / 2;
26         A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
27         System.out.println("A triangle with sides 7,8,9 has an area of " + 
A );
28 
29         a = 5;
30         b = 12;
31         c = 13;
32         s = (a+b+c) / 2;
33         A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
34         System.out.println("A triangle with sides 5,12,13 has an area of " + A
);
35 
36         a = 10;
37         b = 9;
38         c = 11;
39         s = (a+b+c) / 2;
40         A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
41         System.out.println("A triangle with sides 10,9,11 has an area of " + A
);
42 
43         a = 8;
44         b = 15;
45         c = 17;
46         s = (a+b+c) / 2;
47         A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
48         System.out.println("A triangle with sides 8,15,17 has an area of " + A
);
49     }
50 }
```

1.  （变量 A 本身并没有被返回，只有它的值。事实上，要记住变量的“作用域”仅限于它所定义的代码块内吗？（你在练习 21 中学到了这一点。）变量 a 只在函数 main 内部的作用域内，变量 s、A 和参数变量 a、b 和 c 只在函数 triangleArea 内部的作用域内。）

### 你应该看到什么

```java

A triangle with sides 3,3,3 has an area of 2.0 A triangle with sides 3,4,5 has an area of 6.0
A triangle with sides 7,8,9 has an area of 26.832815729997478 A triangle with sides 5,12,13 has an area of 30.0
A triangle with sides 10,9,11 has an area of 42.42640687119285 A triangle with sides 8,15,17 has an area of 60.0
```

### 学习演练

1.  哪一个更长，有函数的还是没有函数的？

1.  这两个文件的公式中有一个错误。当`(a+b+c)`是奇数时，除以`2`会丢失`.5`。将其修正为`(a+b+c)/2.0`。在没有使用函数的版本中修复会更难吗？

1.  再添加一个测试：找到一个边长为 9、9 和 9 的三角形的面积。添加起来难吗？如果在不使用函数的版本中添加测试会更难吗？

### 在完成了学习演练后，你应该看到的内容

```java

A triangle with sides 3,3,3 has an area of 3.897114317029974 A triangle with sides 3,4,5 has an area of 6.0
A triangle with sides 7,8,9 has an area of 26.832815729997478 A triangle with sides 5,12,13 has an area of 30.0
A triangle with sides 10,9,11 has an area of 42.42640687119285 A triangle with sides 8,15,17 has an area of 60.0
A triangle with sides 9,9,9 has an area of 35.074028853269766
```

这更好。

