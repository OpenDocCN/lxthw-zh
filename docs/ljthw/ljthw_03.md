## 练习 2：更多打印

好了，现在我们已经完成了第一个艰难的任务，我们将做另一个。好处是，在这个任务中，我们仍然有很多设置代码（几乎每次都是相同的），但是设置与“有用”代码的比例要好得多。

将以下文本键入单个文件中，文件名为`LetterToYourself.java`。确保与我写的内容完全匹配，包括间距、标点和大写。

```java
 1 public class LetterToYourself
 2 {
 3     public static void main( String[] args )
 4     {
 5         System.out.println( "+­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­+" );
 6         System.out.println( "|                                                    #### |" );
 7         System.out.println( "|                                                    #### |" );
 8         System.out.println( "|                                                    #### |" );
 9         System.out.println( "|                                                         |" );
10         System.out.println( "|                                                         |" );
11         System.out.println( "|                              Bill Gates                 |" );
12         System.out.println( "|                              1 Microsoft Way            |" );
13         System.out.println( "|                              Redmond, WA 98104          |" );
14         System.out.println( "|                                                         |" );
15         System.out.println( "+­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­+" );
16     }
17 }
```

请注意，第一行与上一个任务相同，只是类的名称现在是`LetterToYourself`而不是`FirstProg`。还要注意，您要放置内容的文件名是`LetterToYourself.java`而不是`FirstProg.java`。这不是巧合。

在 Java 中，每个文件只能包含一个公共类，而公共类的名称必须与文件名（包括大小写）匹配，除了文件名以`.java`结尾，而公共类名不是。

那么，在 Java 中，`public class`*意味着*什么？等您长大了我会告诉您。说真的，试图一开始就详细介绍这种类型的原因是大多数“初学者”编程书籍对于真正的初学者来说都很糟糕。所以不要担心。现在只需键入它。（不幸的是，这种情况会发生很多。）

您可能会注意到此程序的第二行、第三行和第四行与上一个任务*完全*相同。它们没有任何区别。

然后，在第二个左大括号之后，有十一个打印语句。它们都是完全相同的，除了引号之间的内容。小竖线（“`|`”）称为“管道”字符，您可以使用`Shift +`反斜杠（“`\`”）键入它。假设您使用的是普通的美国键盘，反斜杠键位于退格键和回车键之间。

一切都键入并保存为`LetterToYourself.java`后，您可以像之前的任务一样编译和运行它。切换到终端窗口，将目录更改为保存代码的目录，并键入以下内容进行编译：

```java

$ javac LetterToYourself.java
```

如果你非常擅长烦人的细节并且幸运的话，你将不会有错误，`javac`命令将在不说任何话的情况下完成。可能你会有错误。如果是这样，回去仔细比较你输入的内容和我写的内容。最终你会发现你的错误。修复它们，再次保存文件，然后尝试重新编译。

一旦它编译没有错误，你可以像以前一样运行它：

```java

$ javac LetterToYourself.java
$ java LetterToYourself
+­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­+
|                                                    #### |
|                                                    #### |
|                                                    #### |
|                                                         |
|                                                         |
|                              Bill Gates                 |
|                              1 Microsoft Way            |
|                              Redmond, WA 98104          |
|                                                         |
+­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­­+
```

两个程序完成了。不错！到目前为止你所取得的成就*并不*容易，任何认为它容易的人都有*很多*经验，并且已经忘记了第一次尝试这些东西是什么感觉。不要放弃！

每天多做一点，这样*会*变得更容易。

### 学习演练

1. 这个文件叫`LetterToYourself.java`而不是`LetterToBillGates.java`！回到你的文本编辑器，把名字和地址从比尔盖茨在微软的地址改成你自己的名字和地址。然后保存，编译，再次运行。

### 常见的学生问题

#### 我必须使用我的真实地址吗？

当然不是。但是确保你的虚假地址占据三行。

#### 为什么当我运行程序时我的信不对齐？！在代码中一切看起来都很完美！

你可能在你的`println()`语句中使用了制表符和空格的混合。许多文本编辑器在你按下`TAB`键时只会将光标移动 4 个空格。但当你的程序运行时，引号内嵌的任何制表符将占用 8 个空格，而不是 4 个。如果你删除引号之间的所有制表符并用空格替换它们，你的代码和运行程序时的效果应该是一样的。

