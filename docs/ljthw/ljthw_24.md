        ## 练习 23：更多字符串比较

        嗯，你已经学会了不能用`==`比较字符串；你必须使用`.equals()`

        方法。但我认为你终于准备好看看我们如何比较字符串的字母顺序了。

        ```java
        1 import java.util.Scanner; 2
        3 public class DictionaryOrder 4 {
        5   public static void main( String[] args ) 6   {
        7    Scanner keyboard = new Scanner(System.in); 8
        9    String name; 10
        ```

        1.  ```java
            System.out.print( "Give me the name of a made­up programming language: " );
            ```

        1.  ```java
            name = keyboard.nextLine(); 13
            ```

        1.  ```java
            if ( name.compareTo("c++") < 0 )
            ```

        1.  ```java
            System.out.println( name + " comes BEFORE c++" );
            ```

        1.  ```java
            if ( name.compareTo("c++") == 0 )
            ```

        1.  ```java
            System.out.println( "c++ isn't a made­up language!" );
            ```

        1.  ```java
            if ( name.compareTo("c++") > 0 )
            ```

        1.  ```java
            System.out.println( name + " comes AFTER c++" ); 20
            ```

        1.  ```java
            if ( name.compareTo("go") < 0 )
            ```

        1.  ```java
            System.out.println( name + " comes BEFORE go" );
            ```

        1.  ```java
            if ( name.compareTo("go") == 0 )
            ```

        1.  ```java
            System.out.println( "go isn't a made­up language!" );
            ```

        1.  ```java
            if ( name.compareTo("go") > 0 )
            ```

        1.  ```java
            System.out.println( name + " comes AFTER go" ); 27
            ```

        1.  ```java
            if ( name.compareTo("java") < 0 )
            ```

        1.  ```java
            System.out.println( name + " comes BEFORE java" );
            ```

        1.  ```java
            if ( name.compareTo("java") == 0 )
            ```

        1.  ```java
            System.out.println( "java isn't a made­up language!" );
            ```

        1.  ```java
            if ( name.compareTo("java") > 0 )
            ```

        1.  ```java
            System.out.println( name + " comes AFTER java" ); 34
            ```

        1.  ```java
            if ( name.compareTo("lisp") < 0 )
            ```

        1.  ```java
            System.out.println( name + " comes BEFORE lisp" );
            ```

        1.  ```java
            if ( name.compareTo("lisp") == 0 )
            ```

        1.  ```java
            System.out.println( "lisp isn't a made­up language!" );
            ```

        1.  ```java
            if ( name.compareTo("lisp") > 0 )
            ```

        1.  ```java
            System.out.println( name + " comes AFTER lisp" ); 41
            ```

        1.  ```java
            if ( name.compareTo("python") < 0 )
            ```

        1.  ```java
            System.out.println( name + " comes BEFORE python" );
            ```

        1.  ```java
            if ( name.compareTo("python") == 0 )
            ```

        1.  ```java
            System.out.println( "python isn't a made­up language!" );
            ```

        1.  ```java
            if ( name.compareTo("python") > 0 )
            ```

        1.  ```java
            System.out.println( name + " comes AFTER python" ); 48
            ```

        1.  ```java
            if ( name.compareTo("ruby") < 0 )
            ```

        1.  ```java
            System.out.println( name + " comes BEFORE ruby" );
            ```

        1.  ```java
            if ( name.compareTo("ruby") == 0 )
            ```

        1.  ```java
            System.out.println( "ruby isn't a made­up language!" );
            ```

        1.  ```java
            if ( name.compareTo("ruby") > 0 )
            ```

        1.  ```java
            System.out.println( name + " comes AFTER ruby" ); 55
            ```

        1.  ```java
            if ( name.compareTo("visualbasic") < 0 )
            ```

        1.  ```java
            System.out.println( name + " comes BEFORE visualbasic" );
            ```

        1.  ```java
            if ( name.compareTo("visualbasic") == 0 )
            ```

        ```java

        59
        60
        61
        62
        63 }
        ```

        ```java
        System.out.println( "visualbasic isn't a made­up language!" ); if ( name.compareTo("visualbasic") > 0 )
        System.out.println( name + " comes AFTER visualbasic" );
        ```

        ```java
        }
        ```

        ### 你应该看到什么

        ```java

        Give me the name of a made­up programming language: juniper juniper comes AFTER c++
        juniper comes AFTER go juniper comes AFTER java juniper comes BEFORE lisp juniper comes BEFORE python juniper comes BEFORE ruby
        juniper comes BEFORE visualbasic
        ```

        （当然，我忍不住在第 12 行插入了一些东西。而不是使用 Scanner 对象的

        `.next()`方法读取一个字符串，我使用 Scanner 对象的`.nextLine()`方法读取一个字符串。不同之处在于`.next()`会在你输入空格时停止读取，所以如果你输入`"visual` `basic"`，它只会读取`"visual"`，并留下其余的部分。当你使用`.nextLine()`时，它会读取你输入的所有内容，包括空格和制表符，直到你按下回车键，然后将所有内容放入一个长字符串中并将其存储到变量中。

        你可以使用 String 对象的`.compareTo()`方法将字符串相互比较。这个

        `.compareTo()`方法的工作方式并不是你可能期望的，但它的工作方式是有巧妙之处的。

        比较涉及两个字符串。第一个字符串是`.compareTo()`左侧的字符串。第二个字符串是括号内的字符串。比较简化为一个整数！如果我们称第一个为 self，第二个为 other，它会是这样的：

        ```java

        int n = self.compareTo(other);
        ```

        所以 self 将自己与 other 进行比较。如果 self 与 other 相同（长度相同，每个字符都相同），那么 n 将被设置为`0`。如果 self 在字母表中出现在 other 之前，那么 n 将被设置为负数（小于 0 的数）。如果 self 在字母表中出现在 other 之后，那么 n 将被设置为正数（大于 0 的数）。

        天才的部分在于：因为`.compareTo()`给我们的是一个整数，而不仅仅是一个布尔值 true 或 false，我们只需要这一个方法来进行所有的比较：小于、大于、小于或等于，等等。

        因为如果*self*等于*other*，我们会得到零，如果*self*小于*other*，我们会得到一个小于零的数字，所以我们可以写：

        ```java

        if ( self.compareTo(other) <= 0 )
        ```

        如果结果小于零，`if`语句将为真，如果结果等于零，`if`语句将为真。

        语句将为真。这有点像写

        ```java

        if ( self <= other )
        ```

        ...除了我刚刚写的那个实际上不会编译，而`.compareTo()`的技巧会。如果你问我，这很酷。

        ```java

        if ( self.compareTo(other) < 0 ) // true when self < other if ( self.compareTo(other) <= 0 ) // true when self <= other if ( self.compareTo(other) > 0 ) // true when self > other if ( self.compareTo(other) >= 0 ) // true when self >= other if ( self.compareTo(other) == 0 ) // true when self == other
        ```

        ```java
        if ( self.compareTo(other) != 0 ) // true when self != other
        ```

        这就是这个想法。对于初学者来说可能会有些困惑，使用起来稍微有些困难，但一旦你习惯了，就一点也不坏。

        这里的另一个困难（这不仅仅是一个`.compareTo()`的问题，在代码的任何地方都会发生，除非你写代码来解决它）是大小写的问题。`"Bob"`和`"bob"`不是相同的值。更糟糕的是，由于字母的 Unicode 值，`"Bob"`在字母表中出现在`"bob"`之前。如果你想避免这个问题，有很多方法，但我喜欢这两种方法中的一种：

        ```java

        if ( self.toLowerCase().compareTo( other.toLowerCase() ) < 0 ) // or if ( self.compareToIgnoreCase(other) < 0 )
        ```

        或者你可以让人类输入任何他们想要的东西，并立即将其转换为小写，然后只与你代码中的小写进行比较。

        ### 学习训练

        1. 使用你选择的方法，使这个程序即使在人类输入了“错误”的大写字母的单词时也能正确工作。

        ![image](img/Image_029.png)

1.  计算机只能在内部处理数字。字母不是数字，但有一个巨大的表，将每种语言中的每个字符映射到 1,112,063 个数字中的一个，唯一标识该字符。字母“B”的 UTF-8 Unicode 值是 66；字母“b”的值是 98。

