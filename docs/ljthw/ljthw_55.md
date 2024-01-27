## 练习 54：从文件中读取记录

这个练习将向您展示如何从文本文件中读取记录的值。 还有一个示例，演示了一个循环，该循环会读取整个文件，无论文件有多长。

如果你在一个没有连接到互联网的机器上运行这个程序，这段代码将无法正常工作，尽管更改非常小。 该代码访问此文件，如果需要，您可以下载该文件。

+   http://learnjavathehardway.org/txt/s01e01­cast.txt

将以下代码键入名为`ActorList.java`的单个文件中。（说`class` `Actor`的行是正确的，但您不能将文件命名为`Actor.java`，否则它将无法工作。）

```java

 1 import java.util.Scanner;
 2 
 3 class Actor
 4 {
 5     String name;
 6     String role;
 7     String birthdate;
 8 }
 9 
10 public class ActorList
11 {
12     public static void main(String[] args) throws Exception
13     {
14         String url = "http://learnjavathehardway.org/txt/s01e01­cast.txt";
15         // Scanner inFile = new Scanner(new java.io.File("s01e01­cast.txt"));
16         Scanner inFile = new Scanner((new java.net.URL(url)).openStream());
17 
18         while ( inFile.hasNext() )
19         {
20             Actor a = getActor(inFile);
21             System.out.print(a.name + " was born on " + a.birthdate);
22             System.out.println(" and played the role of " + a.role);
23         }
24         inFile.close();
25     }
26 
27     public static Actor getActor( Scanner input )
28     {
29         Actor a = new Actor();
30         a.name = input.nextLine();
31         a.role = input.nextLine();
32         a.birthdate = input.nextLine();
33 
34         return a;
35     }
36 }
```



### 你应该看到什么

```java

Sean Bean was born on 1959­04­17 and played the role of Eddard 'Ned' Stark
Mark Addy was born on 1964­01­14 and played the role of Robert Baratheon
Nikolaj Coster­Waldau was born on 1970­07­27 and played the role of Jaime 
Lannister
Michelle Fairley was born on 1964 and played the role of Catelyn Stark

```

这次我们的记录称为`Actor`，有三个字段，所有字段都是字符串。

在第 16 行，我们创建了一个与输入文本文件的互联网地址连接的`Scanner`对象。 您注意到我在顶部没有导入`java.net.URL`吗？ 只有在您想要能够输入类名的简短版本时，才需要导入类。

在这种情况下，如果我在代码顶部导入了`java.net.URL`，我可以直接写：

```java

Scanner inFile = new Scanner((new URL(url)).openStream());
// instead of
Scanner inFile = new Scanner((new java.net.URL(url)).openStream());
```

有时，如果我只打算使用一个类一次，我宁愿在我的代码中使用完整的名称，而不是导入它。 我在第 15 行也使用了同样的技巧； 而不是导入`java.io.File`，我只是在这里使用了完整的类名。

（如果您的机器没有互联网访问权限，请删除第 15 行开头的两个斜杠，这样它就不再是注释，然后在第 16 行开头*添加*两个斜杠*使*它成为注释。

然后程序将在本地读取文件，而不是通过互联网读取。）

无论您是从互联网还是从您自己的计算机打开文件，在第 17 行之后，我们都有一个名为`inFile`的`Scanner`对象，它连接到一个文本文件。

当我们从文本文件中读取数据时，很多时候我们事先不知道它的长度。在最低温度练习中，我向你展示了一个处理这个问题的技巧：将项目数量存储为文件的第一行。但更常见的技术是我在这里使用的：只需使用一个循环，直到我们到达文件的末尾。

`Scanner`对象的`.hasNext()`方法将在尚未读取的数据时返回`true`。如果没有更多数据，则返回`false`。因此，在第 18 行，我们创建一个`while`循环，只要`.hasNext()`继续返回`true`，就会重复。

在我们查看第 20 行之前，让我们跳到第 27 到 35 行，我在那里创建了一个函数，该函数将从文件中读取单个演员记录的所有数据。

该函数名为`getActor`。它有一个参数：一个`Scanner`对象！没错，你将一个已经打开的`Scanner`对象传递给函数，它会从中读取。`getActor`函数返回一个`Actor`。它返回整个记录。

如果我们要从函数中返回一个`Actor`对象，我们需要一个`Actor`类型的变量来返回，因此我们在第 29 行定义了一个。我只是称它为 `a`，因为在函数内部我们对这个变量的目的一无所知。您应该为变量提供良好的名称，但在这种情况下，像 `a` 这样的简短、无意义的名称是完全可以的。

第 30 到 32 行读取文本文件中的三行并将它们存储到记录的三个字段中。然后函数完成了它的工作，我们将记录返回到`main()`中的第 20 行。

为什么我们在`main()`中和函数中都要创建一个名为 `a` 的`Actor`变量？因为变量作用域。变量只在其所在的块中（也就是“可见”）。

声明。不管变量是否从函数中“返回”，因为请记住，返回的不是变量本身，而是变量的*值*的副本。

在`main()`的第 20 行声明（和定义）了一个名为 `a` 的`Actor`变量，但当第 23 行的闭合大括号出现时，该变量就超出了作用域。在`getActor()`函数的第 29 行声明（和定义）了另一个名为 `a` 的`Actor`变量，但当第 35 行的闭合大括号出现时，该变量也超出了作用域。

好的，回到第 20 行。变量 `a` 的值来自函数`getActor()`的返回值。我们将打开的`Scanner`对象 `inFile` 作为函数的参数传递给它，它会返回一个填充了所有字段的`Actor`对象。

（为什么参数称为`inFile`，而参数称为`input`？因为它们不是同一个变量。参数`input`在第 27 行声明，并从参数`inFile`获取值的副本。它们是两个具有相同值的不同变量。）

经过所有这些，第 21 和 22 行非常无聊：它们只是显示记录的所有字段的值。在第 23 行，循环会再次重复检查条件：现在我们从文件中读取了另一条记录，文件是否仍然有更多？如果是，继续循环。如果不是，跳到第 24 行，关闭文件。

请注意，在函数和`main()`中的`while`循环中，变量 `a` 一次只保存一个记录。我们从文件中读取所有记录并将它们全部打印在屏幕上，但当程序最后一次通过循环时，变量 `a` 只保存最近的记录。所有其他记录仍然在文件中，并且已经显示在屏幕上，但它们的值目前没有保存在任何变量中。

我们可以修复这个问题，但要等到下一个练习。

