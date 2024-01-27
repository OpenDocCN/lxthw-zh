## 练习 22：使用大开关做决定

`if`语句并不是在 Java 中比较变量值的唯一方法。还有一种叫做`switch`的东西。我并不经常使用它们，但无论如何你都应该熟悉它们，以防你读到别人使用它的代码。

```java
 1 import java.util.Scanner;
 2 
 3 public class ThirtyDays
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         int month, days;
10         String monthName;
11 
12         System.out.print( "Which month? (1­12) " );
13         month = keyboard.nextInt();
14 
15         switch(month)
16         {
17             case  1: monthName = "January";
18                      break;
19             case  2: monthName = "February";
20                      break;
21             case  3: monthName = "March";
22                      break;
23             case  4: monthName = "April";
24                      break;
25             case  5: monthName = "May";
26                      break;
27             case  6: monthName = "June";
28                      break;
29             case  7: monthName = "July";
30                      break;
31             case  8: monthName = "August";
32                      break;
33             case  9: monthName = "September";
34                      break;
35             case 10: monthName = "October";
36                      break;
37             case 11: monthName = "November";
38                      break;
39             case 12: monthName = "December";
40                      break;
41             default: monthName = "error";
42         }
43 
44         /* Thirty days hath September
45            April, June and November
46            All the rest have thirty­one
47            Except the second month alone....
48         */
49 
50         switch(month)
51         {
52             case  9:
53             case  4:
54             case  6:
55             case 11: days = 30;
56                      break;
57             case  2: days = 28;
58                      break;
59             default: days = 31;
60         }
61 
62         System.out.println( days + " days hath " + monthName );
63 
64     }
65 }
```

### 你应该看到什么

```java

Which month? (1­12) 4
30 days hath April
```

`switch`语句以关键字`switch`开始，然后是一些括号。括号内是一个单一的变量（或者简化为单一值的表达式）。然后是一个开放的大括号。

在`switch`语句的主体内部有几个以关键字`case`开头的`case`语句，然后是括号中的变量可能相等的值。然后是一个冒号（`:`）。在 Java 中很少看到冒号。

在`case`之后，是值和冒号，然后是一些代码。它可以是任意行的代码，除了你不允许在`switch`语句内部声明任何变量。然后在所有代码之后是关键字`break`。`break`标志着`case`的结束。

当`switch`语句运行时，计算机会找出括号内变量的当前值。然后它逐个查看`case`列表，寻找匹配项。当它找到匹配项时，它会从`case`所在的左侧移动到右侧，并开始运行代码，直到被`break`停止。

如果没有`case`匹配，且有一个`default`情况（可选），那么`default`中的代码将被运行。

情况将被运行。

第二个例子从第 50 行开始，演示了一旦`switch`语句找到与之匹配的情况，它确实会运行右侧的代码，直到遇到`break`语句。它甚至会从一个`case`穿过到另一个。

我们可以利用这种穿透行为，有时做一些聪明的事情，比如计算一个月中的天数的代码。由于 9 月、4 月、6 月和 11 月都有 30 天，我们可以将它们的所有情况放在一起，让它们穿过任何一个运行相同的事情。

无论如何，我不会在这本书中再使用`switch`语句，因为我几乎从来没有找到过它的好用处，但它确实存在，至少我可以说你看到了它。

### 学习演练

1.  在第一个`switch`中删除一些`break`语句，并添加一些`println()`语句来确认它会将`monthName`设置为一个值，然后又一个值，直到最后被`break`停止。

