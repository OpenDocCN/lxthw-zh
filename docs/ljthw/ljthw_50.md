## 练习 49：在数组中查找东西

更多关于数组的内容！在这个练习中，我们将研究如何找到特定的值。我们在这里使用的技术有时被称为“线性搜索”，因为它从数组的第一个槽开始查找，然后移动到第二个槽，然后是第三个，依此类推。

```java

 1 import java.util.Scanner;
 2 
 3 public class ArrayLinearSearch
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         int[] orderNumbers = { 12345, 54321, 78753, 101010, 8675309, 31415, 
271828 };
10         int toFind;
11 
12         System.out.println("There are " + orderNumbers.length + " orders in 
the database.");
13 
14         System.out.print("Orders: ");
15         for ( int num : orderNumbers )
16         {
17             System.out.print( num + "  " );
18         }
19         System.out.println();
20 
21         System.out.print( "Which order to find? " );
22         toFind = keyboard.nextInt();
23 
24         for ( int num : orderNumbers )
25         {
26             if ( num == toFind )
27             {
28                 System.out.println( num + " found.");
29             }
30         }
31     }
32 }
```


### 你应该看到什么

```java

There are 7 orders in the database.
Orders: 12345 54321 78753 101010 8675309 31415 271828
Which order to find? 78753 78753 found.
```

这次数组的名称是 orderNumbers，它是一个整数数组。它有七个槽。`12345`是第一个槽，`271828`在数组的最后一个槽。这七个槽中的每一个都可以容纳一个整数。

当我们创建一个数组时，Java 会给我们一个内置变量，告诉我们数组的容量。这个变量是只读的（你可以检索它的值，但不能改变它），被称为`.length`。在这种情况下，由于数组 orderNumbers 有七个槽，变量`orderNumbers.length`等于`7`。这在第 12 行中使用。

在第 15 行，我们有一个 foreach 循环，以在屏幕上显示所有订单号。 “对于数组`orderNumbers`中的每个整数`num`...”。因此，在此循环的主体中，`num`将逐个接受数组中的每个值，并将它们全部显示出来。

在第 22 行，我们让人类输入订单号。然后我们使用循环让`num`逐个接受每个

订单号并将它们与`toFind`逐个比较。当我们找到匹配时，我们会这样说。

（你必须想象我们的数据库中有数百或数千个订单，而不仅仅是七个，当我们找到匹配时，我们会打印出更多内容。我们很快就会到那里。）

### 学习演练

1.  我们在两个 foreach 循环中都创建了一个名为 num 的`int`。我们是否可以只在第 10 行声明变量一次，然后从两个循环中删除`int`？试一试看看。

1.  尝试更改代码，以便如果未找到订单号，则打印出一条单一消息。这很棘手。即使您没有成功，也要努力尝试，然后再进行下一个练习。

