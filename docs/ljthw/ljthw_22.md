        ## 练习 21：嵌套 if 语句

        你在上一个练习中已经看到了这一点，但你可以在`if`语句的主体中放入任何你喜欢的东西，包括其他`if`语句。这被称为“嵌套”，在另一个`if`语句内部的`if`语句称为“嵌套 if”。

        ```java

        1 import java.util.Scanner; 2
        3 public class GenderTitles 4 {
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
        28
        29
        30
        31
        32
        33
        34
        35
        36
        37
        38
        39
        40
        41
        42
        43
        44
        45
        46
        47
        48 }
        ```

        ```java
        public static void main( String[] args )
        {
        Scanner keyboard = new Scanner(System.in);
        ```

        ```java
        String title;

        System.out.print( "First name: " ); String first = keyboard.next(); System.out.print( "Last name: " ); String last = keyboard.next(); System.out.print( "Gender (M/F): " ); String gender = keyboard.next(); System.out.print( "Age: " );
        int age = keyboard.nextInt();

        if ( age < 20 )
        {
        title = first;
        }
        else
        {
        if ( gender.equals("F") )
        {
        System.out.print( "Are you married, "+first+"? (Y/N): " ); String married = keyboard.next();
        if ( married.equals("Y") )
        {
        title = "Mrs.";
        }
        else
        {
        title = "Ms.";
        }
        }
        else
        {
        title = "Mr.";
        }
        }

        System.out.println( "\n" + title + " " + last );
        ```

        ```java
        }
        ```

        这是使用它做一些有用的事情的一个例子。

        ### 你应该看到的

        ```java

        First name: Graham
        ```

        ```java
        Last name: Mitchell Gender (M/F): M Age: 39

        Mr. Mitchell
        ```

        你可能已经发现我喜欢稍微混合一下，让你保持警惕。你注意到我这次做了什么不同吗？

        通常我会在程序的顶部声明所有变量，并在稍后给它们赋值（或“初始化”）。但实际上，你不必在准备使用变量之前声明它。所以这一次，我声明了所有变量（除了*title*）在我第一次为它们赋值的同一行。

        那么为什么我不在第 22 行声明*title*呢？因为那样它以后就不在“范围”内了。*范围*指的是程序中变量可见的位置。一般规则是，一旦声明变量，从那时起在代码中的后续部分直到声明的块结束，变量就在范围内。然后变量就超出范围，不能再使用了。

        让我们看一个例子：在第 29 行，我定义（声明和初始化）了一个名为 married 的字符串变量。它是在女性性别`if`语句的主体内声明的。这个变量存在于第 29 行到第 38 行，在该`if`语句的主体块的右花括号处。married 变量在程序的其他任何地方都不在范围内；在第 1 到第 28 行或第 39 到第 48 行引用它会导致编译错误。

        这就是为什么我必须在程序的开始处声明*title*。如果我在第 22 行声明它，那么当年龄小于 20 的代码块的右花括号出现时，变量将会超出范围。因为我需要*title*一直可见，直到第 45 行，所以我需要确保我在代码块内声明它，该代码块在第 47 行结束。

        不过，我本来可以等到第 19 行再声明它。

        无论如何，关于这个练习没有太多有趣的事情要说，除了它演示了嵌套。

        `if`语句和其他`else`语句。不过，我在学习演习中有一个小惊喜。

        ### 学习演习

        1. 将第 39 行的`else`更改为合适的`if`语句，例如：

        ```java
        if ( gender.equals("M") )
        ```

        注意，程序不再编译。你能想出原因吗？

        这是因为变量*title*在第 9 行声明，但没有立即赋值。然后在第 45 行，*title*的值被打印在屏幕上。此时变量*必须*有一个值，否则我们将尝试显示一个未定义的变量的值：它*没有*值。编译器希望防止这种情况发生。

        当第 39 行是`else`时，编译器可以保证无论通过嵌套的`if`语句的哪条路径，*title*总是会得到一个值。一旦我们将其更改为常规的`if`语句，现在有一种方法，人类可以输入一些内容，使其通过所有嵌套的`if`语句，而不给*title*一个值。你能想到一个吗？

        （当提示输入性别时，他们可以输入年龄 20 或更大，以及不同于`"M"`或`"F"`的字母。

        然后，没有一个性别的`if`语句会为真。）

        我们可以通过将第 39 行的`else`语句更改为合适的`if`语句来解决这个问题（可能是个好主意），或者通过初始化

        在我们声明*title*的时候（可能是个好主意）：

        ```java

        String title = "error";
        ```

        ……或者类似的东西。现在*title*有一个值，无论如何，编译器都很高兴。

