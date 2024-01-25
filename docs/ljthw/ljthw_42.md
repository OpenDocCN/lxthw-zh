## 练习 41：写入文件的程序

我们现在要暂时停下来专注于函数，学习一些简单的东西。我们要创建一个程序，可以将信息放入文本文件，而不仅仅是在屏幕上打印东西。

当你在输入这段代码时，不要错过第 6 行末尾的`throws Exception`。（在这个练习中，我会解释这意味着什么。）

```java
 1 import java.io.FileWriter;
 2 import java.io.PrintWriter;
 3 
 4 public class LetterRevisited
 5 {
 6     public static void main( String[] args ) throws Exception
 7     {
 8         PrintWriter fileout;
 9 
10         fileout = new PrintWriter( new FileWriter("letter.txt") );
11 
12         fileout.println( "+­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­+" );
13         fileout.println( "|                                                    #### |" );
14         fileout.println( "|                                                    #### |" );
15         fileout.println( "|                                                    #### |" );
16         fileout.println( "|                                                         |" );
17         fileout.println( "|                                                         |" );
18         fileout.println( "|                              Bill Gates                 |" );
19         fileout.println( "|                              1 Microsoft Way            |" );
20         fileout.println( "|                              Redmond, WA 98104          |" );
21         fileout.println( "|                                                         |" );
22         fileout.println( "+­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­+" );
23         fileout.close();
24     }
25 }
```

### 你应该看到什么

没错。当你运行你的程序时，它似乎什么都没做。但如果你写得正确，它应该在与你的代码相同的文件夹中创建一个名为`letter.txt`的文件。你可以使用与写代码相同的文本编辑器查看这个文件。

如果由于某种原因你正在使用随 Windows 95 一起提供的版本的记事本，它看起来可能会像这样：

（那个截图是很久以前做的，好吧？记住我做这个已经很长时间了。当我第一次

当我把这个作业给学生时，Windows 95 是最新版本的 Windows……实际上，我猜邮政编码在某个时候改变了。）

在第 1 行和第 2 行有两个新的`import`语句，分别是用于这两个 Java 类的。

在第 8 行，我们声明了一个变量。这个变量的类型是`PrintWriter`，我选择将它命名为 fileout（尽管变量的名称并不重要）。

fileout（尽管变量的名称并不重要）。

在第 10 行，我们给 PrintWriter 变量赋了一个值：一个新的 PrintWriter 对象的引用。创建 PrintWriter 对象需要一个参数。我们给它的参数是一个新的`FileWriter`对象，它本身是用文件名作为参数创建的。

可以只使用`FileWriter`对象而不使用任何 PrintWriter 来写入文本文件。然而，PrintWriters 更容易使用，你可以通过查看代码的其余部分来看出来。所以我们不直接使用 FileWriter 对象，而是用 PrintWriter 对象“包装”FileWriter 对象，然后通过 PrintWriter 对象进行操作。

（如果你不理解最后两段，没关系。你不需要理解它们来写文件。）

好消息是，一旦 PrintWriter 对象设置好了，其他的事情就很容易了。因为你从一开始就在秘密地使用 PrintWriters！这是因为`System.out`是一个 PrintWriter！

因此，在第 12 行，您可以看到写入文件看起来与在屏幕上打印非常相似。但是字符串（`+­­­­­`）不会被打印在屏幕上。它将被存储为文件`letter.txt`的第一行！

如果该文件夹中已经存在名为`letter.txt`的文件，则其内容将被覆盖而不会有警告。如果文件不存在，则将创建该文件。

练习中的另一个重要行是第 23 行。这实际上保存了文件的内容并关闭了它，因此您的程序无法再对其进行写入。如果删除此行，您的程序很可能会创建一个名为`letter.txt`的文件，但该文件将为空。

好的，在结束练习之前，我想简要讨论一下`throws Exception`。这在真正的编程中并不常见，并且适当地解释它超出了本书的范围，但我确实想谈一下。

在练习的原始版本中，当您在函数的第一行之后放置`throws Exception`时，它的意思是“我已经在这个函数中编写了可能不起作用的代码，如果失败，它将会失败（通过抛出异常）。”

在这种情况下，可能不起作用的是`new FileWriter（“letter.txt”）`这一行，因为它试图在当前文件夹中打开一个文件进行写入。如果已经有一个名为“letter.txt”的文件并且该文件是只读的，这可能会失败。或者整个文件夹是只读的。或者有其他原因导致程序无法获得对文件的写入权限。

因此，我们不是简单地使程序崩溃，而是应该检测异常并处理它。就像这样：

`try`块的意思是“这段代码可能会抛出异常，但尝试执行它。”如果一切顺利（如果没有抛出异常），那么`catch`块将被跳过。如果抛出异常，则会执行`catch`块，并将抛出的异常作为参数传递进去。（我已经将异常参数命名为 err，尽管它可以被命名为任何东西。）

在`catch`块中，我打印出一个合适的错误消息，然后通过调用内置函数`System.exit()`来结束程序。如果向`System.exit()`传递参数`0`，程序将结束，但零表示“一切正常”。参数`1`表示“程序正在结束，因为出了问题”。

所以我不会在这本书中再使用`try`和`catch`了，但至少现在你知道通过使用`throws Exception`来避免什么了。

