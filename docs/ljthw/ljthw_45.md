        ## 练习 44：使用 for 循环计数

        正如您在以前的练习中看到的，`while`循环和 do-while 循环可以用来多次执行某些操作。

        ```java

        1 import java.util.Scanner; 2
        3 public class CountingFor 4 {
        ```

        ```java
        5
        6
        7
        8
        9
        10
        11
        12
        ```

        ```java
        public static void main( String[] args )
        {
        Scanner keyboard = new Scanner(System.in);
        ```

        ```java
        int n;
        String message;

        System.out.println( "Type in a message, and I'll display it five
        ```

        ```java
        times." ); 13
        14
        15
        16
        17
        18
        19
        20
        21
        ); 22
        23
        24
        25
        26
        27
        28
        29
        30
        31
        32
        ```

        ```java
        System.out.print( "Message: " ); message = keyboard.nextLine();
        ```

        ```java
        for ( n = 1 ; n <= 5 ; n++ )
        {
        System.out.println( n + ". " + message );
        }
        System.out.println( "\nNow I'll display it ten times and count by 5s." for ( n = 5 ; n <= 50 ; n += 5 )
        {
        System.out.println( n + ". " + message );
        }

        System.out.println( "\nFinally, three times counting backward." ); for ( n = 3 ; n > 0 ; n ­= 1 )
        {
        System.out.println( n + ". " + message );
        }
        ```

        ```java
        33 }
        34 }
        ```

        但是，这两种循环都设计成只要条件为真就继续进行。如果我们事先知道要做某事的次数，Java 有一种专门设计用于改变变量值的循环：`for`循环。

        ### 您应该看到的内容

        ```java

        Type in a message, and I'll display it five times. Message: Howdy, y'all!
        ```

        1.  ```java
            Howdy, y'all!
            ```

        1.  ```java
            Howdy, y'all!
            ```

        1.  ```java
            Howdy, y'all!
            ```

        1.  ```java
            Howdy, y'all!
            ```

        1.  ```java
            Howdy, y'all!
            ```

        ```java

        Now I'll display it ten times and count by 5s.
        5\. Howdy, y'all!
        10\. Howdy, y'all!
        15\. Howdy, y'all!
        20\. Howdy, y'all!
        25\. Howdy, y'all!
        ```

        ```java
        30\. Howdy, y'all!
        35\. Howdy, y'all!
        40\. Howdy, y'all!
        45\. Howdy, y'all!
        50\. Howdy, y'all!

        Finally, three times counting backward.
        3\. Howdy, y'all!
        2\. Howdy, y'all!
        1\. Howdy, y'all!
        ```

        第 16 行演示了一个非常基本的`for`循环。每个`for`循环都有三个部分，它们之间用分号分隔。

        第一部分（`n=1`）无论循环重复多少次，都只会发生一次。它发生在循环的最开始，并且通常为将要用于控制循环的某个变量设置一个起始值。在这种情况下，我们的“循环控制变量”是 n，它将以`1`的值开始。

        第二部分（`n <= 5`）是一个条件，就像`while`或 do-while 循环的条件一样。`for`循环是一个前测试循环，就像`while`循环一样，这意味着在循环开始之前会测试这个条件。如果条件为真，循环体将执行一次。如果条件为假，循环体将被跳过，循环结束。

        第三部分（`n++`）在每次循环迭代之后运行，就在再次检查条件之前。请记住，`++`会将变量加一。

        因此，如果我们*展开*这个循环，这些语句将会发生并按顺序执行：

        ```java

        n = 1;
        // check if ( n <= 5 ), which is true System.out.println( 1 + "." + message ); n++; // so now n is 2
        // check if ( n <= 5 ), which is true System.out.println( 2 + "." + message ); n++; // so now n is 3
        // check if ( n <= 5 ), which is true System.out.println( 3 + "." + message ); n++; // so now n is 4
        // check if ( n <= 5 ), which is true System.out.println( 4 + "." + message ); n++; // so now n is 5
        // check if ( n <= 5 ), which is true System.out.println( 5 + "." + message ); n++; // so now n is 6
        // check if ( n <= 6 ), which is false. The loop stops
        ```

        注意，第一部分只发生了一次，第三部分发生的次数正好与循环体发生的次数一样多。

        在第 22 行有另一个`for`循环。循环控制变量仍然是 n。（请注意，循环控制变量出现在循环的所有三个部分中。这几乎总是这种情况。）

        第一部分（“初始化表达式”）将循环控制变量设置为`5`。然后第二部分检查 n 是否小于或等于`50`。如果是，循环体将执行一次，然后执行第三部分。第三部分将`5`添加到循环控制变量中，然后再次检查条件。如果条件仍然为真，循环将重复。一旦条件为假，循环停止。

        在第 28 行有一个最后的`for`循环。这次循环控制变量从`3`开始，只要 n 大于零，循环就会重复。并且在循环体的每次迭代之后，第三部分（“更新表达式”）会从循环控制变量中减去`1`。

        那么何时应该使用`for`循环而不是`while`循环？

        当我们事先知道要做某事的次数时，最好使用`for`循环。

        +   做这件事十次。

        +   做这件事五次。

        +   选择一个随机数，并执行相应次数。

        +   拿这个物品清单，对列表中的每个物品执行一次。

            另一方面，`while`和 do-while 循环最适合在条件为真时重复执行：

        +   只要他们没有猜到，就继续进行。

        +   只要你没有得到对子，就继续进行。

        +   只要他们继续输入负数，就继续进行。

        +   只要他们没有输入零，就继续进行。

        ### 学习训练

        1. 从第三个循环中删除第一部分（“初始化表达式”）。如果您正确删除它，它仍将编译。当您运行它时会发生什么？

