## 练习 42：从文件中获取数据

能够将信息放入文件的程序只是故事的一部分。因此，在这个练习中，您将学习如何读取已经存在于文本文件中的信息。

如果你输入这段代码并编译并运行，它会崩溃。这是因为它试图从一个名为`name-and-numbers.txt`的文本文件中读取，这个文件必须与你的代码在同一个文件夹中。你可能没有这样的文件！

因此，在你写代码之前，让我们创建一个包含一个字符串和三个整数的文本文件。我的文件看起来像这样：

（这是一个稍微更新的记事本版本。现在开心了吗？）好了，来看代码吧！

```java
 1 import java.util.Scanner;
 2 import java.io.File;
 3 
 4 public class GettingFromFile
 5 {
 6     public static void main( String[] args ) throws Exception
 7     {
 8         Scanner fileIn = new Scanner(new File("name­and­numbers.txt"));
 9 
10         int a, b, c, sum;
11         String name;
12 
13         System.out.print("Getting name and three numbers from file...");
14         name = fileIn.nextLine();
15         a = fileIn.nextInt();
16         b = fileIn.nextInt();
17         c = fileIn.nextInt();
18         fileIn.close();
19 
20         System.out.println("done.");
21         System.out.println("Your name is " + name);
22         sum = a + b + c;
23         System.out.println( a + "+" + b + "+" + c + " = " + sum );
24     }
25 }
```

### 你应该看到什么

```java

Getting name and three numbers from file...done. Your name is Samantha Showalter
5+6+7 = 18
```

你知道 Scanner 对象不一定要从键盘上的人那里获取输入吗？它也可以从文本文件中读取数据！

我们只是稍微不同地创建了 Scanner 对象：不再使用`System.in`作为参数，而是使用`new File("blah.txt")`。这将以只读方式打开文本文件。我选择称之为 fileIn 的 Scanner 对象将附加到文件上，就像吸管插入果汁盒一样。（果汁盒就是文本文件，Scanner 对象就是吸管。）

第 14 行看起来相当无聊。它“暂停”程序并从 Scanner 对象中读取一个字符串，这个字符串来自文件。这个来自文件的字符串被存储到变量中。

第 15 到 17 行也很简单。除了从文件中读取的内容在放入变量之前被转换为整数。

如果文件中的下一个内容不是整数会怎样？那么你的程序将崩溃。现在你不能再责怪人类了：你创建了这个文件。你的工作是确保你知道里面有什么值，以及顺序是什么。

在第 18 行，文件被关闭，这意味着你的 Scanner 对象不再与它连接。这比你预期的要容易吗？希望是这样。

### 学习训练

1.  打开文本文件并更改名称或数字。保存它。然后再次运行程序（您不必重新编译它；代码没有更改，直到运行程序时它才会打开文件）。

