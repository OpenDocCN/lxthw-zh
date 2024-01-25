## 练习 40：导入标准库

在上一个练习中，您看到了 Java 中可用的所有内置模块，这可能让您感到恐慌。今天我们将看一个“简单”的程序，我花了大约半个小时的时间编写，因为我花了很多时间在互联网上搜索和导入东西，尝试了一些不起作用的东西。

这段代码有效。它允许用户输入密码（或任何内容），然后打印出该密码的 SHA-256 消息摘要。

当您在编写此代码时，不要忘记在第 7 行的末尾加上`throws Exception`。

```java
 1 import java.util.Scanner;
 2 import java.security.MessageDigest;
 3 import javax.xml.bind.DatatypeConverter;
 4 
 5 public class PasswordDigest
 6 {
 7     public static void main( String[] args ) throws Exception
 8     {
 9         Scanner keyboard = new Scanner(System.in);
10 
11         String pw, hash;
12 
13         MessageDigest digest = MessageDigest.getInstance("SHA­256");
14 
15         System.out.print("Password: ");
16         pw = keyboard.nextLine();
17 
18         digest.update( pw.getBytes("UTF­8") );
19         hash = DatatypeConverter.printHexBinary( digest.digest() );
20 
21         System.out.println( hash );
22     }
23 }
```

### 您应该看到的内容

```java

Password: password 
5E884898DA28047151D0E56F8DC6292773603D0D6AABBDD62A11EF721D1542D8
```

那个 64 个字符长的字符串是字符串`password`的 SHA­256 摘要。该消息摘要对于该输入始终是相同的。

如果您输入不同的密码，当然会得到不同的摘要：

```java

Password: This is a really long password and no one will ever guess it. 
A113B65D8BA8DB72D631D97B7A3698E82CDB9D1F52456C8957312CB91EC02B10
```

在编程的早期，当机器开始拥有用户名和密码时，很明显您不希望直接在数据库中存储密码本身。相反，他们会存储密码的某种加密哈希。

加密哈希具有两个有用的属性：

1.  它们是一致的。给定的输入将始终产生完全相同的输出。

1.  它们是单向的。您可以轻松计算给定输入的输出，但找出给您某个输出的输入是非常困难或不可能的。

SHA­256 是一个非常好的加密哈希函数，它始终产生一个给定输入（或“消息”）的“摘要”，长度恰好为 256 位。在这里，我们没有尝试处理位，而是打印出了这些位的 base­64 表示，最终是 64 个字符长，其中每个字符都是十六进制数字。

回到 20 世纪 70 年代，要在某台机器上更改密码，您需要输入密码，然后机器会将您的用户名和新密码的哈希存储在文件中。

然后，当您以后想要登录到机器时，它会让您输入用户名和密码。它会在密码数据库文件中找到用户名，并找到您密码的存储哈希值。然后它会找到您刚刚输入的密码的哈希值。如果存储的哈希值和计算的哈希值匹配，那么您必须输入了正确的密码，您将被允许访问该机器。

这是一个聪明的方案。这也比直接在数据库中存储密码要好得多。然而，现在计算机速度太快，存储空间太大，这已经不足以提供足够的安全性。由于机器可以非常快速地计算密码的 SHA­256，一个决心的黑客不需要很长时间就能够弄清楚您的密码是什么。

（如果您真的想要在数据库中安全存储密码，您应该使用`bcrypt`，它专门用于此类事情。不幸的是，bcrypt 并没有内置到 Java 中，因此您需要下载其他人制作的 bcrypt 库。）

好了，关于安全密码就说这么多，让我们走一遍这段代码。您可能希望打开这两个库的 javadoc 文档。

+   java.security.MessageDigest

+   javax.xml.bind.DatatypeConverter

在第 2 和 3 行，我们导入了两个库，这两个库将用于执行此练习的难点。

在第 13 行，我们创建了一个`MessageDigest`类型的变量（现在存在，因为我们导入了`java.security.MessageDigest`）。我们的变量名为 digest，尽管我也可以叫它其他名字。变量的值来自于`MessageDigest.getInstance()`方法的返回值。我们将一个字符串作为该方法的参数传递，这是我们想要的摘要。在这种情况下，我们使用了`"SHA­256"`，但`"SHA­1"`和`"MD5"`也可以工作。您可以在 javadoc 文档中阅读有关此内容的信息。

第 15 和 16 行希望是无聊的。请注意，我使用`nextLine()`而不是`next()`来读取密码，这允许用户输入多个单词。

在第 18 行，我们调用了 String 类的`getBytes()`方法，参数为`"UTF­8"`。这将把字符串值转换为 UTF­8 格式的原始字节列表，然后将其直接作为参数传递给名为 digest 的 MessageDigest 对象的`update()`方法。我通过阅读 String 类的 javadoc 文档了解了`getBytes()`方法！

+   java.lang.String

第 19 行我们调用了名为 digest 的 MessageDigest 对象的`digest()`方法。这给了我们一个原始的字节列表，不适合在屏幕上打印，所以我们直接将这个原始的字节列表作为参数传递给 DatatypeConverter 类的`printHexBinary()`方法。这将返回一个字符串，我们将其存储到变量 hash 中。

然后我们在屏幕上显示哈希值。哇！

如果这个练习让你有点紧张，别担心。如果你能完成本书的前 39 个练习，那么你也可以学会做这种事情。你必须学会阅读 javadoc 文档，了解其他人已经为你写好了什么样的工具，以及如何将它们连接在一起以获得你想要的东西。这只是需要大量的练习！记住，第一次写这个练习花了我半个多小时，而我从上世纪 80 年代开始编程，1996 年开始编写 Java 代码！

### 学习 Drill

1.  查看本练习中使用的所有方法的 javadoc 文档：getInstance、getBytes、update、digest 和 printHexBinary。查看它们期望的参数和它们将返回的值的类型。

1.  从第 7 行的末尾删除`throws Exception`。尝试编译它。（然后再放回去。）你将在下一个练习中学到一点关于异常。

