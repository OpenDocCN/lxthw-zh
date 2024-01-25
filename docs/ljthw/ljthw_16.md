## 练习 15：使用 if 语句做决定

嘿！我真的很喜欢这个练习。你在那里经历了一些相当无聊的练习，所以现在是时候学习一些有用而不是超级困难的东西了。

```java
 1 import java.util.Scanner;
 2 
 3 public class AgeMessages
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         int age;
10 
11         System.out.print( "How old are you? " );
12         age = keyboard.nextInt();
13 
14         if ( age < 13 )
15         {
16             System.out.println( "You are too young to create a Facebook 
account." );
17         }
18         if ( age < 16 )
19         {
20             System.out.println( "You are too young to get a driver's license."
);
21         }
22         if ( age < 18 )
23         {
24             System.out.println( "You are too young to get a tattoo." );
25         }
26         if ( age < 21 )
27         {
28             System.out.println( "You are too young to drink alcohol." );
29         }
30         if ( age < 35 )
31         {
32             System.out.println( "You are too young to run for President of the
United States." );
33             System.out.println( "How sad!" );
34         }
35     }
36 }
```

我们将学习如何编写具有决策的代码，以便输出不总是相同的。执行的代码会根据人输入的内容而改变。

### 你应该看到什么

```java

How old are you? 17
You are too young to get a tattoo. You are too young to drink alcohol.
You are too young to run for President of the United States. How sad!
```

好的，这就是所谓的“if 语句”。if 语句以关键字`if`开头，后面跟着括号中的“条件”。条件必须是一个布尔表达式，其值为`true`或`false`。在下面开始了由大括号包围的一块代码，大括号里面的东西缩进了一层。这段代码被称为 if 语句的“主体”。

当 if 语句的条件为真时，if 语句的主体中的所有代码都会被执行。

当 if 语句的条件为假时，主体中的所有代码都会被跳过。你可以在 if 语句的主体中有任意多行代码；它们将作为一组被执行或跳过。

注意，当我运行代码时，我输入了`17`作为我的年龄。因为 17 不小于 13，所以第 14 行的条件是假的，所以第一个 if 语句的主体中的代码（第 15 到 17 行）被跳过了。

第二个 if 语句也是假的，因为 17 不小于 16，所以它的主体中的代码（第 19 到 21 行）也被跳过了。

第三个 if 语句的条件是真的：17 确实小于 18，所以第三个 if 语句的主体不会被跳过；它被执行了，屏幕上打印出了“你太年轻了，不能纹身”的短语。练习中剩下的 if 语句都是真的。

最后的 if 语句包含两行代码在它的主体中，只是为了向你展示它会是什么样子。

### 学习演习

1.  如果你输入一个大于 35 的年龄，会打印出什么？为什么？

1.  再添加一个 if 语句，将他们的年龄与 65 进行比较。如果他们的年龄大于或等于 65 岁，就说“你已经足够老了，可以退休了！”。

1.  对于每个 if 语句，添加另一个说相反的 if 语句。例如，如果他们的年龄大于或等于 13 岁，就说“你已经足够大了，可以创建一个 Facebook 账户。”完成后，无论输入什么年龄，你的程序每次都应该显示六条消息。

