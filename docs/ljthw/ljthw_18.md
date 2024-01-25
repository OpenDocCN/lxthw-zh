## 练习 17：否则（带 else 的 if 语句）

所以，`if` 语句非常棒。几乎每种编程语言都有它们，你一直都在使用它们。事实上，`if` 语句本身就足够功能强大，你可以只使用 `if` 语句做很多事情。

但有时，有其他东西可能会使事情变得更加方便。比如这个例子：快！以下表达式的逻辑相反是什么？

```java

if ( onGuestList || age >= 21 || ( gender.equals("F") && attractiveness >= 8 ) )
```

嗯？懂了吗？如果是的话

```java
if ( ! ( onGuestList || age >= 21 || ( gender.equals("F") && attractiveness >= 8 ) ) )
```

…然后你是对的，你是我的菜。聪明并且知道什么时候让机器为你工作。如果你说

```java
if ( ! onGuestList && age < 21 && ( ! gender.equals("F") || attractiveness < 8 ) )
```

…然后你是对的，干得好。这实际上是相当难以正确做到的。但是这个的逻辑相反又是什么呢：

```java

if ( expensiveDatabaseThatTakes45SecondsToLookup( userName, password ) == true )
```

我们真的想要写

```java

if ( expensiveDatabaseThatTakes45SecondsToLookup( userName, password ) == false )
```

```java
 1 import java.util.Scanner;
 2 
 3 public class ClubBouncer
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         int age = 22;
10         boolean onGuestList = false;
11         double attractiveness = 7.5;
12         String gender = "F";
13 
14         if ( onGuestList || age >= 21 || ( gender.equals("F") && 
attractiveness >= 8 ) )
15         {
16             System.out.println("You are allowed to enter the club.");
17         }
18         else
19         {
20             System.out.println("You are not allowed to enter the club.");
21         }
22     }
23 }
```

…因为现在我们不得不等待 90 秒来执行两个 `if` 语句，而不是 45 秒。所以幸运的是，编程语言给了我们一些 `else`。（是的，抱歉。忍不住。）

### 你应该看到的

```java

You are allowed to enter the club.
```

所以 `else` 关键字的意思是：看看前面的 `if` 语句。那个条件是

`if` 语句为真吗？如果是，跳过。如果之前的 `if` 语句没有运行，那么

否则语句将被执行。“如果 blah blah blah 为真，则运行这个代码块。否则（else），运行这个不同的代码块。”

否则非常方便，因为我们不必去计算一些复杂布尔表达式的逻辑相反。我们只需要说 `else`，让计算机处理它。

`else` 只有在 `if` 语句结束后立即合法。（严格来说，它只允许在 `if` 语句的主体代码块结束后。）

### 学习技巧

1\. 在第 17 行和第 18 行之间，添加一个 `println()` 语句来在屏幕上打印一些东西（不重要，但我放了 `"C­C­C­COMBO BREAKER"` 因为我很奇怪）。尝试编译程序。为什么不能编译？

