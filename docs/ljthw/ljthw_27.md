## 练习 26：使用`while`循环重复自己

这是我最喜欢的练习之一，因为你将学会如何使代码块*重复*。如果你能做到这一点，你就能写出各种有趣的东西。

```java
 1 import java.util.Scanner;
 2 
 3 public class EnterPIN
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8         int pin, entry;
 9 
10         pin = 12345;
11 
12         System.out.println("WELCOME TO THE BANK OF JAVA.");
13         System.out.print("ENTER YOUR PIN: ");
14         entry = keyboard.nextInt();
15 
16         while ( entry != pin )
17         {
18             System.out.println("\nINCORRECT PIN. TRY AGAIN.");
19             System.out.print("ENTER YOUR PIN: ");
20             entry = keyboard.nextInt();
21         }
22 
23         System.out.println("\nPIN ACCEPTED. YOU NOW HAVE ACCESS TO YOUR 
ACCOUNT.");
24     }
25 }
```

### 你应该看到什么

```java

WELCOME TO THE BANK OF JAVA. ENTER YOUR PIN: 123

INCORRECT PIN. TRY AGAIN. ENTER YOUR PIN: 1234

INCORRECT PIN. TRY AGAIN. ENTER YOUR PIN: 12345

PIN ACCEPTED. YOU NOW HAVE ACCESS TO YOUR ACCOUNT.
```

在第 16 行，您首次看到`while`循环。`while`循环类似于`if`语句。它们都有括号中的条件，用于检查其真假。如果条件为假，则`while`循环和`if`语句都将跳过主体中的所有代码。当条件为真时，`while`循环和`if`语句都将执行其主体中的所有代码一次。

唯一的区别是，`if`语句为真时将执行大括号中的所有代码一次。`while`循环为真时将执行大括号中的所有代码一次，然后返回并再次检查条件。如果条件仍然为真，则再次执行主体中的所有代码。然后再次检查条件，如果条件仍然为真，则再次运行主体。

实际上，你可以说`while`循环会执行其主体中的所有代码，只要在检查时条件为真。

最终，当检查条件时，条件将为假。然后`while`循环将跳过其主体中的所有代码，程序的其余部分将继续。一旦`while`循环的条件为假，它就不会再次被检查。

循环是如此伟大，因为我们终于可以做一些事情不止一次，而不必多次输入代码！事实上，程序员有时会说“保持你的代码 DRY：不要重复自己。”一旦你学会了编程并完成了本书中的所有练习，如果你发现自己在程序中多次输入（或复制粘贴）完全相同的代码，你会开始怀疑。

