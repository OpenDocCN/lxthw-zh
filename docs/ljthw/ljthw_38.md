## 练习 37：从函数返回一个值

有些函数有参数，有些没有。参数是将值*传递*到函数的唯一方法。也只有一种方法可以从函数中得到一个值：返回值。

1 public class HeronsFormula 2 {

3

4

5

6

7

8

9

10

11

12

13

14

15

16

public static void main( String[] args )

{

double a;

a = triangleArea(3, 3, 3);

System.out.println("一个边长为 3,3,3 的三角形的面积为" + a );

a = triangleArea(3, 4, 5);

System.out.println("一个边长为 3,4,5 的三角形的面积为" + a );

a = triangleArea(7, 8, 9);

System.out.println("一个边长为 7,8,9 的三角形的面积为" + a );

System.out.println("一个边长为 5,12,13 的三角形的面积为" + triangleArea(5, 12, 13) );

1.  System.out.println("一个边长为 10,9,11 的三角形的面积为" + triangleArea(10, 9, 11) );

1.  System.out.println("一个边长为 8,15,17 的三角形的面积为" + triangleArea(8, 15, 17) );

19

20

21

22

}

public static double triangleArea( int a, int b, int c )

{

23 // 此函数中的代码计算具有长度 a、b 和 c 的三角形的面积

24

25

26

27

28

29

30

31

32 }

double s, A;

s = (a+b+c) / 2;

A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );

返回 A;

// ^ 计算面积后，“返回”它

}

这个练习给出了一个具有三个参数（三角形的边长）和一个输出（使用海伦公式计算三角形的面积）的函数的例子。

### 你应该看到的

```java

A triangle with sides 3,3,3 has an area of 2.0 A triangle with sides 3,4,5 has an area of 6.0
A triangle with sides 7,8,9 has an area of 26.832815729997478 A triangle with sides 5,12,13 has an area of 30.0
A triangle with sides 10,9,11 has an area of 42.42640687119285 A triangle with sides 8,15,17 has an area of 60.0
```

你可以看到函数`triangleArea`有三个参数。它们都是整数，它们的名字分别是 a、b 和 c。正如你已经知道的，这意味着我们不能在不提供三个整数值作为参数的情况下调用函数。

除此之外，`triangleArea`函数返回一个值。请注意，在第 21 行，它没有在`public static`和`triangleArea`之间说`void`。它说`double`。这意味着“这个函数返回一个值，它返回的值的类型是`double`。”

如果在这个位置上有关键字`void`，这意味着“这个函数不返回任何值。” 如果我们想让`triangleArea`返回不同类型的值：

```java

public static int int
```

```java
triangleArea( int a, int b, int c ) // this would return an
```

```java
public static String triangleArea( int a, int b, int c ) // this would return a String

public static boolean triangleArea( int a, int b, int c ) // this would return either true or false

public static void  triangleArea( int a, int b, int c ) // this cannot return any value of any type
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

```java

1 public class HeronsFormulaNoFunction 2 {
```

```java
3
4
5
6
7
8
9
10
11
12
13
A ); 14
15
16
17
18
19
20
A ); 21
22
23
24
25
26
27
A ); 28
29
30
31
32
33
34
); 35
36
37
38
39
40
41
); 42
43
```

```java
public static void main( String[] args )
{
int a, b, c; double s, A;
```

```java
a = 3;
b = 3;
c = 3;
s = (a+b+c) / 2;
A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
System.out.println("A triangle with sides 3,3,3 has an area of " +

a = 3;
b = 4;
c = 5;
s = (a+b+c) / 2;
A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
System.out.println("A triangle with sides 3,4,5 has an area of " +

a = 7;
b = 8;
c = 9;
s = (a+b+c) / 2;
A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
System.out.println("A triangle with sides 7,8,9 has an area of " +

a = 5;
b = 12;
c = 13;
s = (a+b+c) / 2;
A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
System.out.println("A triangle with sides 5,12,13 has an area of " + A

a = 10;
b = 9;
c = 11;
s = (a+b+c) / 2;
A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
System.out.println("A triangle with sides 10,9,11 has an area of " + A

a = 8;
```

为了确保你能明白函数值得麻烦的原因，这里有一个例子，写出了同样的程序，但没有使用函数。

![image](img/Image_052.png)

1.  （变量 A 本身并没有被返回，只有它的值。事实上，要记住变量的“作用域”仅限于它所定义的代码块内吗？（你在练习 21 中学到了这一点。）变量 a 只在函数 main 内部的作用域内，变量 s、A 和参数变量 a、b 和 c 只在函数 triangleArea 内部的作用域内。）

    ```java
    44

    b = 15;
    45

    c = 17;
    46

    s = (a+b+c) / 2;
    47

    A = Math.sqrt( s*(s­a)*(s­b)*(s­c) );
    48

    System.out.println("A triangle with sides 8,15,17 has an area of " + A
    );

    49

    }

    50
    }

    ```

    ### 你应该看到的

    ```java

    A triangle with sides 3,3,3 has an area of 2.0 A triangle with sides 3,4,5 has an area of 6.0
    A triangle with sides 7,8,9 has an area of 26.832815729997478 A triangle with sides 5,12,13 has an area of 30.0
    A triangle with sides 10,9,11 has an area of 42.42640687119285 A triangle with sides 8,15,17 has an area of 60.0
    ```

    ### 学习训练

    1.  哪一个更长，有函数的还是没有函数的？

    1.  这两个文件的公式中有一个错误。当`(a+b+c)`是奇数时，除以`2`会丢失`.5`。将其修正为`(a+b+c)/2.0`。在没有使用函数的版本中修复会更难吗？

    1.  再添加一个测试：找到一个边长为 9、9 和 9 的三角形的面积。添加起来难吗？如果在不使用函数的版本中添加测试会更难吗？

    ### 在完成了学习练习后，你应该看到的内容

    ```java

    A triangle with sides 3,3,3 has an area of 3.897114317029974 A triangle with sides 3,4,5 has an area of 6.0
    A triangle with sides 7,8,9 has an area of 26.832815729997478 A triangle with sides 5,12,13 has an area of 30.0
    A triangle with sides 10,9,11 has an area of 42.42640687119285 A triangle with sides 8,15,17 has an area of 60.0
    A triangle with sides 9,9,9 has an area of 35.074028853269766
    ```

    这更好。

