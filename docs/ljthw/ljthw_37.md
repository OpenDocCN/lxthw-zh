    ## 练习 36：使用函数显示骰子

    上一个练习在一个函数实际上使事情变得更糟的程序中使用了函数。所以今天我们准备看一个情况，使用函数实际上使程序变得更好。

    Yacht 是一个古老的骰子游戏，后来被修改为商业游戏 Yahtzee。它涉及一次掷五个骰子，并为各种组合赚取积分。最罕见的组合是“游艇”，当五个骰子都显示相同的数字时。

    这个程序不做任何其他的评分，它只是掷五个骰子，直到它们都相同。（计算机速度很快，所以即使这需要很多次尝试，也不会花费很长时间。）

    ```java

    1 public class YachtDice 2 {
    3   public static void main( String[] args ) 4   {
    ```

    1.  ```java
        int roll1, roll2, roll3, roll4, roll5;
        ```

    1.  ```java
        boolean allTheSame; 7
        ```

    ```java
    8    do
    9    {
    ```

    1.  ```java
        roll1 = 1 + (int)(Math.random()*6);
        ```

    1.  ```java
        roll2 = 1 + (int)(Math.random()*6);
        ```

    1.  ```java
        roll3 = 1 + (int)(Math.random()*6);
        ```

    1.  ```java
        roll4 = 1 + (int)(Math.random()*6);
        ```

    1.  ```java
        roll5 = 1 + (int)(Math.random()*6);
        ```

    1.  ```java
        System.out.println("\nYou rolled: " + roll1 + " " + roll2 + " " + roll3 + " " + roll4 + " " + roll5);
        ```

    1.  ```java
        showDice(roll1);
        ```

    1.  ```java
        showDice(roll2);
        ```

    1.  ```java
        showDice(roll3);
        ```

    1.  ```java
        showDice(roll4);
        ```

    1.  ```java
        showDice(roll5);
        ```

    1.  ```java
        allTheSame = ( roll1 == roll2 && roll2 == roll3 && roll3 == roll4 && roll4 == roll5 );
        ```

```java
22
```

1.  ```java
    } while ( ! allTheSame );
    ```

1.  ```java
    System.out.println("The Yacht!!"); 25  }
    ```

```java
26
27   public static void showDice( int roll ) 28   {
```

1.  ```java
    System.out.println("+­­­+");
    ```

1.  ```java
    if ( roll == 1 )
    ```

```java
31    {
```

1.  ```java
    System.out.println("| |");
    ```

1.  ```java
    System.out.println("| o |");
    ```

1.  ```java
    System.out.println("| |"); 35    }
    ```

```java
36    else if ( roll == 2 )
37    {
```

1.  ```java
    System.out.println("|o |");
    ```

1.  ```java
    System.out.println("| |");
    ```

1.  ```java
    System.out.println("| o|"); 41    }
    ```

```java
42    else if ( roll == 3 )
43    {
```

1.  ```java
    System.out.println("|o |");
    ```

1.  ```java
    System.out.println("| o |");
    ```

1.  ```java
    System.out.println("| o|"); 47    }
    ```

```java
48    else if ( roll == 4 )
49    {
50
System.out.println("|o
o|");
51
System.out.println("|
|");
52
System.out.println("|o
o|");
53
}

54
else if ( roll == 5 )

55
{

56
System.out.println("|o
o|");
57

System.out.println("| o |");
58

System.out.println("|o o|");
59

}
60

else if ( roll == 6 )
61

{
62

System.out.println("|o o|");
63

System.out.println("|o o|");
64

System.out.println("|o o|");
65

}
66

System.out.println("+­­­+");
67

}

68
}

```

### 你应该看到的

```java

You rolled:
+­­­+
|o o|
| |
|o o|
+­­­+
+­­­+
|o o|
|o o|
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
|o o|
|o o|
+­­­+
4
6
5
5
6
You rolled:
+­­­+
|o |
| |
| o|
+­­­+
+­­­+
|o |
| |
| o|
+­­­+
+­­­+
|o o|
| o |
|o o|
2
2
5
6
6
+­­­+
+­­­+
|o o|
|o o|
|o o|
+­­­+
+­­­+
|o o|
|o o|
|o o|
+­­­+

...etc

You rolled: 5 5 5 5 5
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| o |
|o o|
+­­­+
The Yacht!!
```

除了第 21 行的花哨的布尔表达式之外，这个练习中有一个名为`showDice`  的单个函数。

在 10 到 14 行，我们选择五个随机数（每个数从 1 到 6）并将结果存储到五个整数变量*roll1*到*roll5*中。

我们想要使用一些`if` 语句在屏幕上显示骰子的值，但我们不想写五次相同的`if` 语句（因为变量是不同的）。解决方案是创建一个带参数的函数。

在第 27 行，你看到了`showDice`  函数定义的开始。在名称（或“标识符”）`showDice`  后面，有一组括号，在它们之间声明了一个变量！这个变量叫做“参数”。`showDice`  函数有一个参数。这个参数是一个整数。它的名字叫 roll。

这意味着每当你为`showDice`写一个函数调用时，你不能只写函数的名称和括号，比如`showDice()`。它不会编译。你必须在括号中包含一个整数值（这称为“参数”），要么是一个变量，要么是一个简化为整数值的表达式。

这里有一些例子。

showDice;

//

不 (没有括号，这指的是变量而不是函数调用)

showDice();

//

不 (函数调用必须有一个参数，而不是零)

showDice(1);

//

是的（一个参数刚刚好）

showDice(4);

//

是的

showDice(1+2);

//

是的

showDice(roll2);

//

是的

showDice(roll5);

//

是的

showDice( (roll3+roll4) / 2

);

//

是的（奇怪但合法）

showDice(17);

//

是的（尽管它不会显示一个合适的骰子图片）

showDice(3, 4);

//

不 (函数调用必须有一个参数，而不是两个)

showDice(2.0);

//

不 (参数必须是整数，而不是双精度)

showDice("two");

//

不 (参数必须是整数，而不是字符串)

showDice(false);

//

不 (参数必须是整数，而不是布尔值)

在所有情况下，参数的值的副本都存储在参数中。因此，如果你这样调用函数 `showDice(3);`，那么函数被调用，值`3`被存储到参数 roll 中。所以到第 29 行，参数变量 roll 已经被声明并初始化为值`3`。

如果我们使用变量调用函数，比如 `showDice(roll2);` 那么在函数体执行之前，函数被调用并且当前在 roll2 中的任何值的副本将被存储到参数变量 roll 中。

因此，在第 16 行，`showDice`函数被执行，roll 将被设置为 roll1 中的任何值。

然后在第 17 行，`showDice`再次被调用，但这次 roll 将被设置为 roll1 中的任何值。

roll2。第 18 行调用`showDice`，同时将其参数设置为 roll3 的值。等等。

这样我们基本上运行了相同的代码块五次，但用不同的变量替换

每次掷骰子。这为我们节省了很多代码。

为了对比，我还写了一个简化的两个骰子版本的练习，而不使用函数。请注意，我必须重复完全相同的`if`语句序列两次：每个变量一次。

还要注意的是，虽然定义函数比只是复制和粘贴要多一点工作

```java

1 public class YachtDiceNoFunctions 2 {
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
14
15
16
17
18
19
20
21
22
23
24
25
26
27
```

```java
public static void main( String[] args )
{
int roll1, roll2;
```

```java
do
{
```

```java
roll1 = 1 + (int)(Math.random()*6); roll2 = 1 + (int)(Math.random()*6); int total = roll1 + roll2;
System.out.println("\nYou rolled a " + roll1 + " and a " + roll2); System.out.println("+­­­+");
if ( roll1 == 1 )
{
```

```java
System.out.println("|
```

```java
|");
```

```java
System.out.println("| o |"); System.out.println("| |");
}
else if ( roll1 == 2 )
{
System.out.println("|o |"); System.out.println("| |"); System.out.println("| o|");
}
else if ( roll1 == 3 )
{
```

`if`语句并更改变量，两个骰子版本比五个骰子版本更长。

```java

28
System.out.println("|o |");

29
System.out.println("| o |");

30
System.out.println("| o|");

31
}

32
else if ( roll1 == 4 )

33
{

34
System.out.println("|o o|");

35
System.out.println("| |");

36
System.out.println("|o o|");

37
}

38
else if ( roll1 == 5 )

39
{

40
System.out.println("|o o|");

41
System.out.println("| o |");

42
System.out.println("|o o|");

43
}

44
else if ( roll1 == 6 )

45
{

46
System.out.println("|o o|");

47
System.out.println("|o o|");

48
System.out.println("|o o|");

49
}

50
System.out.println("+­­­+");

51

52

53
System.out.println("+­­­+");

54
if ( roll2 == 1 )

55
{

56
System.out.println("| |");

57
System.out.println("| o |");

58
System.out.println("| |");

59
}

60
else if ( roll2 == 2 )

61
{

62
System.out.println("|o |");

63
System.out.println("| |");

64
System.out.println("| o|");

65
}

66
else if ( roll2 == 3 )

67
{

68
System.out.println("|o |");

69
System.out.println("| o |");

70
System.out.println("| o|");

71
}

72
else if ( roll2 == 4 )

73
{

74
System.out.println("|o o|");

75
System.out.println("| |");

76
System.out.println("|o o|");

77
}

78
else if ( roll2 == 5 )

79
{

80
System.out.println("|o o|");

81
System.out.println("| o |");

82
System.out.println("|o o|");

83
}

84
else if ( roll2 == 6 )

85
{

86
System.out.println("|o o|");

87
System.out.println("|o o|");

88
System.out.println("|o o|");

89
}

90
System.out.println("+­­­+");

91

92
System.out.println("The total is
" + total + "\n");

93
94
95
96
97 }
```

```java
} while ( roll1 != roll2 );

System.out.println("Doubles! Nice job.");
```

```java
}
```

### 你应该看到的

```java

You rolled a
+­­­+
|o o|
| o |
|o o|
+­­­+
+­­­+
|o o|
| |
|o o|
+­­­+
The total is
5

9
and
a
4

You rolled a
+­­­+
|o o|
|o o|
|o o|
+­­­+
+­­­+
|o |
| |
| o|
+­­­+
The total is

6

8

and

a

2

You rolled a
+­­­+
|o |
| |
| o|
+­­­+
+­­­+
|o |
| |
| o|
+­­­+
The total is

2

4

and

a

2
Doubles! Nice job.
```

### 学习技巧

1. 添加第六个骰子。注意，只需添加一个函数调用就可以轻松显示*roll6*。

