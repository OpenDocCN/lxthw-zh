## 练习 16：更多的 if 语句



这个练习几乎没有什么新东西。这只是对 if 语句的更多练习，因为它们非常重要。这也会帮助你记住关系运算符。

```java
 1 import java.util.Scanner;
 2 
 3 public class ComparingNumbers
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8         double first, second;
 9 
10         System.out.print( "Give me two numbers. First: " );
11         first = keyboard.nextDouble();
12         System.out.print( "Second: " );
13         second = keyboard.nextDouble();
14 
15         if ( first < second )
16         {
17             System.out.println( first + " is LESS THAN " + second );
18         }
19         if ( first <= second )
20         {
21             System.out.println( first + " is LESS THAN or EQUAL TO " + second );
22         }
23         if ( first == second )
24         {
25             System.out.println( first + " is EQUAL TO " + second );
26         }
27         if ( first >= second )
28         {
29             System.out.println( first + " is GREATER THAN or EQUAL TO "+second);
30         }
31         if ( first > second )
32         {
33             System.out.println( first + " is GREATER THAN " + second );
34         }
35 
36         if ( first != second )
37             System.out.println( first + " is NOT EQUAL TO " + second );
38 
39     }
40 }
```

### 你应该看到什么

```java

Give me two numbers. First: 3 Second: 4
3.0 is LESS THAN 4.0
3.0 is LESS THAN or EQUAL TO 4.0
3.0 is NOT EQUAL TO 4.0
```

在第 37 行，你会看到我做了一些有问题的事情：最后一个 if 语句的主体没有任何大括号围绕它。这样可以吗？

实际上是。当 `if` 语句的主体没有花括号时，那么在条件之后的代码的第一行将被包括在主体中。因此，由于这整个练习中的所有 `if` 语句的主体只有一行代码，所以这个练习中的所有 `if` 语句的花括号都是可选的。你可以删除并且程序会正常工作。不过，包括它们永远不会错，有些程序员总是无论如何都会加上花括号。

### 学习演练

1\. 在第 37 行之后添加另一行代码，写上 `System.out.println( "Hey." );`。缩进它，使其与上面的 `println()` 语句对齐，就像这样：

```java
if ( first != second )
System.out.println( first + " is NOT EQUAL TO " + second ); 
System.out.println( "Hey." );
```

运行程序，看看会发生什么。 “嘿” 部分是否属于 if 语句主体？也就是说，当 if 语句被跳过时，“嘿”也被跳过了，还是无论如何都会运行？你觉得呢？

1\. 在最后一个 if 语句的主体周围添加花括号，以便“嘿”行是主体的一部分。然后删除所有*其他* if 语句主体的花括号，以便程序中只有最后一个 if 语句有它们。确认一切都按预期工作。

