## 练习 45：凯撒密码（遍历字符串）

凯撒密码是一种非常简单的密码学形式，以朱利叶斯·凯撒命名，他用它来保护他的私人信件。在密码中，每个字母都会按照字母表中的某个数量上下移动。例如，如果移位是`2`，那么消息中的所有`A`都会被替换为`C`，`B`被替换为`D`，依此类推。

```java
 1 import java.util.Scanner;
 2 
 3 public class CaesarCipher
 4 {
 5     /**
 6      * Returns the character shifted by the given number of letters.
 7      */
 8     public static char shiftLetter( char c, int n )
 9     {
10         int ch = c;
11 
12         if ( ! Character.isLetter(c) )
13             return c;
14 
15         ch = ch + n;
16         if ( Character.isUpperCase(c) && ch > 'Z' || Character.isLowerCase(c) && ch > 'z' )
17             ch ­= 26;
18         if ( Character.isUpperCase(c) && ch < 'A' || Character.isLowerCase(c) && ch < 'a' )
19             ch += 26;
20 
21         return (char)ch;
22     }
23 
24     public static void main( String[] args )
25     {
26         Scanner keyboard = new Scanner(System.in);
27         String plaintext, cipher = "";
28         int shift;
29 
30         System.out.print("Message: ");
31         plaintext = keyboard.nextLine();
32         System.out.print("Shift (0­26): ");
33         shift = keyboard.nextInt();
34 
35         for ( int i=0; i<plaintext.length(); i++ )
36         {
37             cipher += shiftLetter( plaintext.charAt(i), shift );
38         }
39         System.out.println( cipher );
40 
41     }
42 }
```

### 你应该看到什么

```java

Message: This is a test. XyZaBcDeF Shift (0­26): 2
Vjku ku c vguv. ZaBcDeFgH
```

你知道`main()`不一定要是类中的第一个函数吗？好吧，它不是。函数可以以任何顺序出现。

除了`int`，`double`，`String`和`boolean`之外，还有一种基本的变量类型我没有提到：`char`。`char`变量可以像`String`一样保存字符，但一次只能保存一个字符。代码中的字符串文字用双引号括起来，如`"Axe"`，而代码中的`char`文字用单引号括起来，如`'A'`。

从第 8 行开始有一个名为`shiftLetter()`的函数。它有两个参数：`c`是要移动的字符，`n`是要移动的空格数。这个函数返回一个`char`。所以`shiftLetter('A', 2)`将返回字符`'C'`。

我们不想尝试移动任何不是字母的东西，所以在第 10 行我们使用内置的 `Character`类

告诉我们。

然后我们将对字符进行一些简单的数学运算，所以我们在第 13 行将字符的 Unicode 值存储到一个`int`中，以便更容易进行操作。然后在第 15 行，我们将所需的偏移量添加到字符上。

这就是它，除了我们希望偏移“环绕”，所以第 16 到 19 行确保最终值仍然是一个字母。最后在第 21 行，我们取 `ch`的值，将其转换为`char`，并返回它。

在`main()`中，第 27 到 34 行非常无聊。在我解释`for`循环之前，我需要解释两个`String`类方法：`charAt()`和`length()`。

如果你有一个`String`，你可以使用`charAt()`方法从中获取一个单独的`char`。就像这样：

```java

String s = "Howdy"; char c = s.charAt(2);
// Now c == 'w'
// s.length() is 5
```

`charAt()`是从零开始的，所以`s.charAt(0)`从字符串 `s`中获取第一个字符。如果`s.length()`告诉你 `s`中有多少个字符，那么`s.charAt(s.length()­1)`获取最后一个字符。

现在我们可以理解第 36 行的`for`循环了。初始化表达式声明并设置了一个循环控制变量 `i`，将其设置为`0`。条件是只要 `i`小于消息中的字符数。更新表达式将每次将`1`添加到 `i`。

在第 38 行，发生了很多事情。我们使用`charAt`方法只提取消息的第 `i`个字符。该字符和移位值作为参数传递给`shiftLetter()`函数，该函数返回移位后的字母。最后，该移位后的字母被添加到 `String cipher`的末尾。

当循环结束时，它已经逐个遍历了消息的每个字母，并从字母的移位版本中构建了一个新的消息。

也许这一次太多了。让我知道。

### 学习演练

1.  制作这个练习的新版本，从文本文件中获取消息，并创建一个“加密”文件，而不仅仅是在屏幕上打印它。

