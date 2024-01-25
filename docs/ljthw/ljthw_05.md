    ## 练习 4：转义序列和注释

    您是否考虑过如果我们想在屏幕上显示引号会发生什么？由于我们想要显示的所有内容都包含在`println()`语句的引号之间，因此在引号内放置引号将是一个问题。

    大多数编程语言都允许“转义序列”，其中您使用某种转义字符来表示下一个字符不应以正常方式处理。

    以下（邪恶）代码演示了 Java 的许多转义序列。称之为

    `EscapeSequences.java`。

    1

    public class EscapeSequences

    2

    {

    3

    public static void main(String[] args)

    4

    {

    5

    //使用 FIGlet 创建的初始版本，字体为“Big Money”，向西南方向

    6

    7

    System.out.print("\t  \n\t / |\n\t JJJJJ |");

    8

    System.out.println("       ");

    9

    System.out.println("\t JJ | / \\ / \\ / |/ \\");

    10

    System.out.println("\t   JJ | aaaaaa |\"\" \\ /\"\"/ aaaaaa |");

    11

    System.out.println("\t/ | JJ | / aa | \"\" /\"\"/ / aa |");

    12

    System.out.println("\tJJ \\  JJ |/aaaaaaa | \"\" \"\"/ /aaaaaaa |");

    13

    System.out.println("\tJJ JJ/ aa aa | \"\"\"/ aa aa |");

    14

    System.out.println("\t JJJJJJ/ aaaaaaa/ \"/ aaaaaaa/");

    15

    }

    16

    }

    ```java

    /
    ```

    ```java
    |
    ```

    JJJJJ |

    ```java
    JJ | /   \ / \  / |/   \
    ```

    JJ | aaaaaa |"" \ /""/ aaaaaa |

    ```java
    / | JJ | /  aa | "" /""/ /  aa | JJ \  JJ |/aaaaaaa | "" ""/ /aaaaaaa | JJ  JJ/ aa  aa | """/ aa  aa | JJJJJJ/  aaaaaaa/   "/   aaaaaaa/
    ```

    当您运行它时，您应该看到的是这样的。

    Java 的转义字符是反斜杠（`\`），这与您按下以使管道（`|`）显示出来的相同键，但不需要按住 Shift。 Java 中的所有转义序列都必须在一组引号内。

    `\"`代表引号。

    `\t`是一个制表符；这就像您在键入代码时按 Tab 键一样。现在它可能看起来更复杂，因为您以前从未见过它，但是当您阅读别人的代码时

    引号内的`\t`不如一堆可能是空格或制表符的空格不明确。

    `\n`是一个换行符。在打印时，它将导致输出移到下一行的开头，然后继续打印。

    `\\`是显示反斜杠的方法。

    在第 5 行，您会注意到该行以两个斜杠（或“正斜杠”，如果您坚持的话）开头。这标记了该行为“注释”，这是程序员的人为利益。计算机完全忽略注释。

    实际上，用两个斜杠标记注释的行不一定要在行的开头；我们可以写这样的东西：

    ```java

    System.out.println( "A" ); // prints an 'A' on the screen
    ```

    ...它完全有效。从两个斜杠到该行末尾的所有内容都将被编译器忽略。

    （尽管这不是一个很好的评论；但是，任何了解 Java 的程序员都已经知道该行代码的作用。通常，您应该放置解释代码存在的原因的注释，而不是代码的作用。随着您在编码方面的技能提高，您将更擅长编写良好的注释。）

    无论如何，这个练习很难，所以这次没有学习任务。下一个练习将介绍一些新内容，并恢复正常难度。

