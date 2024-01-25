    ## 练习 39：使用 Javadoc 重新审视三十天

    在上一个练习中，我们写了一些可能更好被省略的函数。在今天的练习中，我们将重新做一个之前的练习，使用函数使其更好。

    而且，因为我总是不断努力，我在类的上方和每个函数的上方添加了称为“Javadoc 注释”的特殊注释。

    ```java

    1 import java.util.Scanner; 2
    3 /**
    4 * Contains functions that make it easier to work with months. 5 */
    6 public class ThirtyDaysFunctions 7 {
    8   public static void main( String[] args ) 9   {
    10    Scanner kb = new Scanner(System.in); 11
    ```

    1.  ```java
        System.out.print( "Which month? (1­12) " );
        ```

    1.  ```java
        int month = kb.nextInt(); 14
        ```

    ```java
    15    System.out.println( monthDays(month) + " days hath " + monthName(month) );
    16
    17  }
    18
    19  /**
    20   * Returns the name for the given month number (1­12).
    21  *
    ```

    1.  ```java
        * @author Graham Mitchell
        ```

    1.  ```java
        * @param month the month number (1­12)
        ```

    1.  ```java
        * @return    a String containing the English name for the given month, or "error" if month out of range
        ```

    ```java
    25  */
    26   public static String monthName( int month ) 27   {
    28    String monthName = "error"; 29
    ```

    1.  ```java
        if ( month == 1 )
        ```

    1.  ```java
        monthName = "January";
        ```

    1.  ```java
        else if ( month == 2 )
        ```

    1.  ```java
        monthName = "February";
        ```

    1.  ```java
        else if ( month == 3 )
        ```

    1.  ```java
        monthName = "March";
        ```

    1.  ```java
        else if ( month == 4 )
        ```

    1.  ```java
        monthName = "April";
        ```

    1.  ```java
        else if ( month == 5 )
        ```

    1.  ```java
        monthName = "May";
        ```

    1.  ```java
        else if ( month == 6 )
        ```

    1.  ```java
        monthName = "June";
        ```

    1.  ```java
        else if ( month == 7 )
        ```

    1.  ```java
        monthName = "July";
        ```

    1.  ```java
        else if ( month == 8 )
        ```

    1.  ```java
        monthName = "August";
        ```

    1.  ```java
        else if ( month == 9 )
        ```

    1.  ```java
        monthName = "September";
        ```

    1.  ```java
        else if ( month == 10 )
        ```

    1.  ```java
        monthName = "October";
        ```

    1.  ```java
        else if ( month == 11 )
        ```

    1.  ```java
        monthName = "November";
        ```

    1.  ```java
        else if ( month == 12 )
        ```

    1.  ```java
        monthName = "December";
        ```

    ```java

    54
    55
    56
    57
    58
    59
    60
    61
    62
    63
    ```

    ```java
    return monthName;
    ```

    ```java
    }
    ```

    ```java
    /**
    ```

    +   ```java
        Returns the number of days in a given month.
        *
        ```

    +   ```java
        @author Graham Mitchell
        ```

    +   ```java
        @param month the month number (1­12)
        ```

    ```java
    * @return
    ```

    ```java
    the number of days in a non­leap year for that month, or
    ```

    ```java
    64
    65
    66
    67
    68
    69
    70
    71
    72
    73
    74
    75
    76
    77
    78
    79
    80
    81
    82
    83
    84
    85
    86
    87
    88 }
    ```

    ```java
    31 if month out of range
    */
    public static int monthDays( int month )
    {
    int days;
    ```

    ```java
    /* Thirty days hath September April, June and November
    All the rest have thirty­one
    Except the second month alone.  */

    switch(month)
    {
    case  9:
    case  4:
    case  6:
    case 11: days = 30;
    break; case 2: days = 28;
    break; default: days = 31;
    }

    return days;
    ```

    ```java
    }
    ```

    ### 您应该看到的内容

    ```java

    Which month? (1­12) 9
    30 days hath September
    ```

    如果现在忽略 Javadoc 注释，希望您应该能够看到在这里使用函数实际上改进了代码。`main()`非常简短，因为大部分有趣的工作都是在函数中完成的。

    与月份名称相关的所有代码和变量都被隔离在`monthName()`函数中。查找月份天数的所有代码都包含在`monthDays()`函数中。

    像这样将变量和代码收集到函数中被称为“过程式编程”，这被认为是比将所有代码放在`main()`中更重要的进步。这使得您的代码更容易调试，因为如果您遇到月份名称的问题，您就知道它必须在`monthName()`函数中。

    好了，现在让我们谈谈 Javadoc 注释。

    `javadoc` 是随同 Java 编译器一起提供的自动生成文档的工具。您可以通过在类、函数或变量上方使用特殊类型的块注释来在代码中编写文档。

    注释以`/**`开头，以`*/`结尾，中间的每一行都以星号(`*`)开头

    就像您在练习中看到的那样排列。

    javadoc 注释的第一行是关于该事物（类或函数）的一句话摘要。然后有标签如`@author`或`@return`，提供了更多关于谁编写了代码，函数期望的参数或它将返回的值的详细信息。

    好了，现在是魔法部分。打开终端窗口，就像您要编译代码一样，然后输入以下命令：

    ```java

    $ javadoc ThirtyDaysFunctions.java
    Loading source file ThirtyDaysFunctions.java... Constructing Javadoc information...
    Standard Doclet version 1.7.0_21
    Building tree for all the packages and classes... Generating /ThirtyDaysFunctions.html...
    Generating /package­frame.html... Generating /package­summary.html... Generating /package­tree.html...
    Generating /constant­values.html...
    Building index for all the packages and classes... Generating /overview­tree.html...
    Generating /index­all.html... Generating /deprecated­list.html... Building index for all classes...
    Generating /allclasses­frame.html... Generating /allclasses­noframe.html... Generating /index.html...
    Generating /help­doc.html...
    $
    ```

    然后，如果您查看`ThirtyDaysFunctions.java`所在的文件夹，您将看到许多新文件。（也许我应该先警告您。）在您选择的 Web 浏览器中打开名为`index.html`的文件。

    这是 javadoc 文档，其中包含*大量*的信息。您可以在顶部附近找到您为类放置的注释，函数的注释在名为“Method Summary”的部分中。

    有关参数和返回类型的详细信息在名为“Method Detail”的部分下面。

    ### 学习练习

    1. 查看内置 Java 类 java.util.Scanner 的 javadoc 文档。注意它看起来与 javadoc 工具生成的文档有多相似？所有官方的 Java 文档都是使用 javadoc 工具创建的，因此学习如何阅读它将成为成为专业 Java 程序员的重要部分。不过现在不要太担心细节，只是试着感受一下它的外观。

    左上角是包含在 Java 中的所有代码包的列表，下面是左侧是您可以导入以避免编写代码的所有类/库的列表。专业的 Java 程序员的工作的一大部分是编写代码来粘合现有的 Java 库。

    现在这可能让您感到不知所措。这没关系，因为您刚刚开始。希望没有人期望您现在就了解太多。事实上，大多数程序员只了解 Java 的内置库的一小部分，并且当他们需要做一些新的事情时，他们会在互联网上搜索并阅读文档，就像您一样！

