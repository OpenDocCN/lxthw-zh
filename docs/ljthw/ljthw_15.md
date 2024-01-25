## 练习 14：复合布尔表达式



有时我们想使用比“小于”或“等于”更复杂的逻辑。想象一下，只有在 25 岁以上*并且*40 岁以下*并且*要么富有要么长得很好看时，祖母才会同意你约会她的孙子。如果那位祖母是一名程序员，并且能说服申请者诚实回答，她的程序可能会像这样：

```java
 1 import java.util.Scanner;
 2 
 3 public class ShallowGrandmother
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         int age;
10         double income, attractiveness;
11         boolean allowed;
12 
13         System.out.print( "Enter your age: " );
14         age = keyboard.nextInt();
15 
16         System.out.print( "Enter your yearly income: " );
17         income = keyboard.nextDouble();
18 
19         System.out.print( "How attractive are you, on a scale from 0.0 to 10.0? " );
20         attractiveness = keyboard.nextDouble();
21 
22         allowed = ( age > 25 && age < 40 && ( income > 50000 || attractiveness >= 8.5 ));
23 
24         System.out.println( "You are allowed to date my grandchild: " + allowed );
25     }
26 }
```

### 你应该看到什么

```java

Enter your age: 39
Enter your yearly income: 49000
How attractive are you, on a scale from 0.0 to 10.0? 7.5 You are allowed to date my grandchild: false
```

所以我们可以看到，对于复杂的布尔表达式，您可以使用括号来分组，使用符号`&&`表示“AND”，使用符号`||`表示“OR”。

我知道你在想什么：使用`&`（“和符号”）表示“AND”有点说得通，但为什么要两个？谁想到使用`||`（“管道管道”）表示“OR”？！？

嗯，肯·汤普森的想法，可能是。Java 语法是模仿 C++的语法，而 C++的语法基本上是从 C 的语法复制过来的，而 C 的语法是从 B 的语法修改而来的，而 B 的语法是由丹尼斯·里奇和肯·汤普森发明的。

编程语言 B 使用`&`表示“AND”，`|`表示“OR”，但它们是“按位的”：它们只对两个整数起作用，并且它们会逐位地遍历整数，对每一对比特进行按位 AND 或 OR 运算，在每次比较中放置`1`或`0`在输出中。（`|`可能被使用是因为它看起来像数学符号，并且是 PDP-7 计算机键盘上的一个关键，B 最初是为其开发的。）

当肯恩和丹尼斯开始开发编程语言*C*来取代*B*时，他们决定需要一个*逻辑*的“AND”和“OR”，而单个符号已经被使用了，所以他们使用两个和符号来表示逻辑“AND”，两个竖线或“管道”来表示逻辑“OR”。哇。

幸运的是，你不需要知道任何这些。你只需要记住要输入什么并且输入正确。

接下来的一点有点奇怪，因为我将向您展示 AND 和 OR 的“真值表”，您将不得不将“AND”视为对两个值执行的*操作*，而不是一个连接词。

以下是 AND 的真值表：

| 输入 |  | 输出 | 
| --- | --- | --- |
| A | B | A && B |
| 真 | 真 | 真 |
| 真 | 假 | 假 |
| 假 | 真 | 假 |
| 假 | 假 | 假 |

您可以这样读表：假设我们的肤浅的祖母已经决定，只有在巡航便宜并且酒精包含在价格中时，她才会去乘船。所以我们假设陈述 A 是“巡航很便宜”，陈述 B 是“酒精包括在内”。表中的每一行都是一个可能的巡航航线。

第 1 行是两个语句都为真的情况。祖母会对第 1 条巡航感到兴奋吗？是的！“巡航很便宜”是真的，“酒精包括在内”也是真的，所以“祖母会去”（A && B）也是真的。

巡航#2 很便宜，但酒精*不*包括在内（陈述 B 是假的）。所以祖母不感兴趣：（A && B）是假的，当 A 为真时，B 为假。

清楚吗？现在这是 OR 的真值表：

| 输入 |  | 输出 | 
| --- | --- | --- |
| A | B | A \|\| B |
| 真 | 真 | 真 |
| 真 | 假 | 真 |
| 假 | 真 | 真假 |
| 假 | 假 | 假 |

假设祖母会购买某辆二手车，如果它看起来真的很酷，或者它的油耗很好。陈述 A 是“车看起来很酷”，B 是“每加仑好里程”，结果 A 或 B 决定了祖母是否想要这辆车。

汽车＃1 看起来很棒，而且一箱油可以走很远。祖母感兴趣吗？当然！我们可以说值`true`与值`true`进行 OR 运算的结果是`true`。

事实上，祖母不喜欢的唯一一辆车是两者都是假的时候。涉及 OR 的表达式只有在其两个组成部分都为假时才为假。

### 学习演练

1.  你知道 Java 也有位运算符吗？调查一下数字是如何用二进制表示的，看看你能否弄清楚为什么以下代码将 x 设置为值`7`，将 y 设置为值`1`。

    ```java
    int x = 3 | 5;
    int y = 3 & 5;
    ```

