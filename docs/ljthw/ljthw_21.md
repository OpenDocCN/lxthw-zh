## 练习 20：更多的`else`和`if`链。

好的，让我们更仔细地看一下使用`else`和`if`构建条件链。


坦白说：尽管我确实参加了德克萨斯大学奥斯汀分校，但我认为这不是他们真正的录取标准。在决定是否申请备用学校时，不要依赖这个程序的输出。

```java
 1 import java.util.Scanner;
 2 import static java.lang.System.*;
 3 
 4 public class CollegeAdmission
 5 {
 6     public static void main( String[] args )
 7     {
 8         Scanner keyboard = new Scanner(System.in);
 9         int math;
10 
11         out.println( "Welcome to the UT Austin College Admissions 
Interface!" );
12         out.print( "Please enter your SAT math score (200­800): " );
13         math = keyboard.nextInt();
14 
15         out.print( "Admittance status: " );
16 
17         if ( math >= 790 )
18             out.print( "CERTAIN " );
19         else if ( math >= 710 )
20             out.print( "SAFE " );
21         else if ( math >= 580 )
22             out.print( "PROBABLE " );
23         else if ( math >= 500 )
24             out.print( "UNCERTAIN " );
25         else if ( math >= 390 )
26             out.print( "UNLIKELY " );
27         else // below 390
28             out.print( "DENIED " );
29 
30         out.println();
31     }
32 }
```

### 你应该看到什么

```java

Welcome to the UT Austin College Admissions Interface! Please enter your SAT math score (200­800): 730 Admittance status: SAFE
```

现在，在我进入这个练习的新内容之前，我应该解释一下我在这个程序中采取的一个快捷方式。你有没有注意到顶部有第二个`import`语句？如果没有，那么你的代码没有编译，或者你认为我在所有地方都写错了，应该是`out.println`而不是`System.out.println`。

好吧，我不想在这本书中过多地谈论面向对象的代码，因为那对初学者来说太复杂了，但是可以这样想。在 Java 中有一个内置对象叫做`System`。在该对象内部还有另一个名为`out`的对象。名为`out`的对象包含一个名为`print()`和一个名为`println()`的方法。

所以当你写`System.out.println`时，你是在要求计算机运行名为`out`的对象内部的名为`println`的方法（它本身是内置导入库`java.lang.System`的一部分）。

因此，我可以创建一个名为`out`的变量，这不会有问题：

```java

String out;
```

尽管有一个名为`out`的对象存在，但它在`System`对象内部，所以名称不会冲突。

如果我懒惰并且没有任何愿望拥有自己命名为`out`的变量，那么我可以要求计算机“将类`java.lang.System`中的所有静态项目导入当前命名空间”：

```java

import static java.lang.System.*;
```

所以现在我可以只输入`out.println`而不是`System.out.println`。哇！

在这个练习中，我还省略了界定每个`if`语句主体中代码块的所有花括号。因为我只想在每个`if`语句的主体中有一个语句，所以这是可以的。如果我想要有多于一行的代码，那么我就必须把花括号放回去。

无论如何，在之前的练习中，我写了如何将`else`放在`if`语句前面使其延迟到前一个`if`语句。当前一个为真并执行其主体中的代码时，当前一个会自动跳过（链中的所有其他`else if`语句也会跳过）。这会使得只有第一个为真的值会触发`if`语句，其他所有的都不会运行。我们有时会说`if`语句是“互斥的”：只有一个会执行。不会少于一个，也不会多于一个。

今天的练习是另一个例子。但是这次我想指出，互斥只能正常工作是因为我按正确的顺序放置了`if`语句。

因为第一个为真的将会执行，而其他的不会，所以你需要确保链中的第一个`if`语句是最难实现的。然后是下一个最难的，以此类推，最容易的放在最后。在学习演练中，我会让你改变`if`语句的顺序，你会看到这样会搞乱事情。

此外，从技术上讲，`else`语句应该有花括号，就像`if`语句一样，通过将`else if`之间什么都不放置来利用花括号是可选的事实。这使得代码更加紧凑。如果按计算机解释的方式排列，先前的代码将是这样的。也许这会帮助你理解`else`在`if`前面的“延迟”行为；也许这只会让你困惑。希望它会有所帮助。

```java
 1 import java.util.Scanner;
 2 import static java.lang.System.*;
 3 
 4 public class CollegeAdmissionExpanded
 5 {
 6     public static void main( String[] args )
 7     {
 8         Scanner keyboard = new Scanner(System.in);
 9         int math;
10 
11         out.println( "Welcome to the UT Austin College Admissions 
Interface!" );
12         out.print( "Please enter your SAT math score (200­800): " );
13         math = keyboard.nextInt();
14 
15         out.print( "Admittance status: " );
16 
17         if ( math >= 790 )
18         {
19             out.print( "CERTAIN " );
20         }
21         else
22         {
23             if ( math >= 710 )
24             {
25                 out.print( "SAFE " );
26             }
27             else
28             {
29                 if ( math >= 580 )
30                 {
31                     out.print( "PROBABLE " );
32                 }
33                 else
34                 {
35                     if ( math >= 500 )
36                     {
37                         out.print( "UNCERTAIN " );
38                     }
39                     else
40                     {
41                         if ( math >= 390 )
42                         {
43                             out.print( "UNLIKELY " );
44                         }
45                         else // below 390
46                         {
47                             out.print( "DENIED " );
48                         }
49                     }
50                 }
51             }
52         }
53         out.println();
54     }
55 }
```

是的。所以你可以看到为什么我们通常只是使用`else if`。

### 学习演练

1.  在原始的代码文件（`CollegeAdmission.java`）中，除了最后一个之外，删除所有的`else`。

    最后一个。运行它并注意它如何打印所有的消息。然后把`else`放回去。

1.  将第 25 行和第 26 行移动到第 18 行和第 19 行之间。编译并运行它，注意程序几乎总是只说`"UNLIKELY"`，因为大多数 SAT 分数都超过 390，而且`if`语句在列表中的位置很高，大部分时间都会占据主导地位。

1.  如果愿意，可以输入`CollegeAdmissionExpanded.java`的代码，并确认它与非扩展版本的功能相同。

