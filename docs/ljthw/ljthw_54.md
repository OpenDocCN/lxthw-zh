## 练习 53：邮寄地址（记录）

今天的练习是关于我所谓的“记录”。在 C 和 C++编程语言中，它们被称为“结构”。数组是一个变量中的许多不同值，其中值都是*相同类型*的，并且它们由*索引*（槽号）区分。记录是一个变量中的几个不同值，但值可以是不同类型的，并且它们由*名称*（通常称为“字段”）区分。

将以下代码输入到一个名为`MailingAddresses.java`的单个文件中。（第一行说

`class Address`是正确的，但你不能把你的文件命名为`Address.java`，否则它就不会工作。

```java
 1 class Address
 2 {
 3     String street;
 4     String city;
 5     String state;
 6     int zip;
 7 }
 8 
 9 public class MailingAddresses
10 {
11     public static void main(String[] args)
12     {
13         Address uno, dos, tres;
14 
15         uno = new Address();
16         uno.street = "191 Marigold Lane";
17         uno.city   = "Miami";
18         uno.state  = "FL";
19         uno.zip    = 33179;
20 
21         dos = new Address();
22         dos.street = "3029 Losh Lane";
23         dos.city   = "Crafton";
24         dos.state  = "PA";
25         dos.zip    = 15205;
26 
27         tres = new Address();
28         tres.street = "2693 Hannah Street";
29         tres.city   = "Hickory";
30         tres.state  = "NC";
31         tres.zip    = 28601;
32 
33         System.out.println(uno.street + "\n" + uno.city + ", " + uno.state + "
" + uno.zip + "\n");
34         System.out.println(dos.street + "\n" + dos.city + ", " + dos.state + "
" + dos.zip + "\n");
35         System.out.println(tres.street + "\n" + tres.city + ", " + tres.state 
+ "  " + tres.zip + "\n");
36     }
37 }
```


### 你应该看到什么

```java

191 Marigold Lane
```

1.  这一切只有一个问题：Java 实际上并没有记录。事实证明，如果你创建一个没有方法，只有公共变量的嵌套类，它就像一个结构一样工作，即使它不是 Java 的方式。

我不在乎这是否是 Java 的方式。我已经教了很多学生，我坚信如果你不先理解记录，就很难理解面向对象的编程。

如果你不先理解记录，就很难理解面向对象的编程。所以我要以一种完全正常的方式伪造它们，这在许多不同的编程语言中都是非常好的代码。

一些顽固的面向对象的 Java 爱好者会偶然发现这个练习，并给我发送一封恶毒的电子邮件，说我做错了，为什么我要用谎言来填充这些可怜的孩子的头脑？哦，好吧。

```java
Miami, FL 33179

3029 Losh Lane
Crafton, PA 15205

2693 Hannah Street
Hickory, NC 28601
```

因此，在第 1 到 7 行，我们定义了一个名为`Address`的记录。

（我知道它说`class`，而不是`record`。如果我能做点什么，我发誓我会。无论如何，您应该将其称为`record`，或者如果您真的想要的话，称为`struct`。如果您将其称为`class`，它将使任何热爱面向对象编程的 Java 程序员感到困惑，如果您将其称为`struct`，至少 C 和 C++程序员会理解您。）

我们的记录有四个字段。 第一个字段是名为`street`的字符串。 第二个字段是称为

城市。等等。

然后在第 9 行开始我们的“真正”类。

在第 13 行，我们声明了三个名为`uno`，`dos`和`tres`的变量。 这些变量不是整数或字符串； 它们是记录。 类型为`Address`。 每个记录中都有四个字段。

在第 15 行，我们必须将一个`Address`对象存储在变量中，因为请记住，我们只声明了变量，它们还没有被初始化。

一旦处理好这些，您将看到我们可以将字符串`"191 Marigold Lane"`存储到

`Address`记录名为`uno`的`street`字段，这正是我们在第 16 行所做的。 第 17 行将字符串`"Miami"`存储到记录`uno`的`city`字段中。

我不打算解释程序的其余部分发生了什么，因为我认为这是

非常清楚。 我想值得一提的是，尽管记录中的三个字段都是字符串，但`zip`字段是整数。 记录的字段可以是您想要的任何类型。

### 学习演练

1.  在第 13 行创建第四个`Address`变量，并更改代码以将*您的*邮寄地址放入其中。不要忘记在底部打印出来。

### 常见问题

+   你从哪里得到这些地址的？

我编造了它们。 我相当肯定这些街道在这些城市中并不存在。 如果我奇迹般地编造了一个真实地址，请告诉我，我会更改它。

