## 练习 13：比较字符串

在这个练习中，我们将看到一些让初学者学习 Java 时困扰的东西：常规的关系运算符不适用于字符串，只适用于数字。

```java

boolean a, b;
a = ("cat" < "dog");
b = ("horse" == "horse" );
```

第二行甚至无法编译！你不能在 Java 中使用`<`来查看一个单词是否在另一个单词之前。在第三行中，`b`确实在这里设置为值`true`，但如果你将值读入变量，就不会这样：

```java

String animal;
animal = keyboard.next(); // the user types in "horse" b = ( animal == "horse" );
```

无论人类是否输入`"horse"`，`b`都将始终被设置为值`false`！

我不想试图解释为什么会这样。Java 的创建者对此显然有充分的理由，但对初学者来说并不友好，解释可能只会让你更加困惑。

你还记得我警告过你 Java 不是初学者的语言吗？所以*有*一种比较字符串是否相等的方法，让我们来看看。

```java
 1 import java.util.Scanner;
 2 
 3 public class WeaselOrNot
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         String word;
10         boolean yep, nope;
11 
12         System.out.println( "Type the word \"weasel\", please." );
13         word = keyboard.next();
14 
15         yep  =   word.equals("weasel");
16         nope = ! word.equals("weasel");
17 
18         System.out.println( "You typed what was requested: " + yep );
19         System.out.println( "You ignored polite instructions: " + nope );
20     }
21 }
```

### 你应该看到什么

```java

Type the word "weasel", please. no
You typed what was requested: false You ignored polite instructions: true
```

因此，字符串有一个名为`.equals()`的内置方法（“点等于”），它将自己与另一个字符串进行比较，如果它们相等，则简化为值`true`，如果它们不相等，则简化为值`false`。你必须使用非运算符（`!`）与`.equals()`方法一起来判断两个字符串是否不同。

### 学习演练

1.  尝试在第 15 行改变比较，使得`"weasel"`在点的前面，变量`word`在括号内。确保`"weasel"`仍然被引号括起来，而`word`则没有。它有效吗？

