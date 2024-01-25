## 练习 7：从人类那里获取输入

现在我们已经练习了一段时间创建变量，我们将看看交互式程序的另一部分：让运行我们程序的人有机会输入一些内容。

继续输入这个，但请注意程序中的第一行不是`public class`行。这次我们从一个“导入”语句开始。

并非每个程序都需要从键盘获取人类的交互输入，因此这不是 Java 语言核心的一部分。就像一辆 F1 赛车不包括空调一样，编程语言通常有一个小的核心，然后有很多可选的库 6，如果需要可以包含进来。


```java
 1 import java.util.Scanner;
 2 
 3 public class ForgetfulMachine
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8 
 9         System.out.println( "What city is the capital of France?" );
10         keyboard.next();
11 
12         System.out.println( "What is 6 multiplied by 7?" );
13         keyboard.nextInt();
14 
15         System.out.println( "What is your favorite number between 0.0 and 1.0?" );
16         keyboard.nextDouble();
17 
18         System.out.println( "Is there anything else you would like to tell me?" );
19         keyboard.next();
20     }
21 }
```

当你第一次运行这个程序时，它只会打印第一行：

```java

What city is the capital of France?
```

然后它会在屏幕上闪烁光标，等待你输入一个单词。当我运行程序时，我输入了单词“巴黎”，但即使你输入一个不同的单词，程序也会正常工作。

然后在你输入一个单词并按回车后，程序将继续打印：

```java

What is 6 multiplied by 7?
```

……等等。假设你对每个问题都输入了合理的答案，最终看起来会像这样：

### 你应该看到的

```java

What city is the capital of France? Paris
What is 6 multiplied by 7?
42
What is your favorite number between 0.0 and 1.0? 2.3
Is there anything else you would like to tell me? No, there is not.
```

1.  库或“模块”——添加额外功能到程序中的一段代码，可能包含或不包含。

让我们来谈谈代码。在第 1 行，我们有一个`import`语句。我们导入的库是 scanner 库`java.util.Scanner`（“java 点 util 点 Scanner”）。这个库包含的功能允许我们从键盘或其他地方（如文件或互联网）读取信息。

第 2 行到第 7 行希望是无聊的。在第 8 行，我们看到了另一件新事物：我们创建了一个名为“keyboard”的“Scanner 对象”。（它不一定要被命名为“keyboard”；你可以在这里使用一个不同的词，只要你在你的代码中到处使用它。）这个名为 keyboard 的 Scanner 对象包含我们将称之为函数或“方法”的能力。在你使用之前，你必须创建并命名一个 Scanner 对象。

在第 10 行，我们要求名为 keyboard 的 Scanner 对象为我们做一些事情。我们说“键盘，运行你的`next（）`函数。”Scanner 对象将暂停程序，等待人类输入。一旦人类输入内容并按回车，Scanner 对象将把它打包成一个字符串，并允许你的代码继续。

在第 13 行，我们要求 Scanner 对象执行其`nextInt（）`函数。这会暂停程序，等待人类输入并按回车，然后将其打包成整数值（如果可能的话）并继续。

如果人类在这里没有输入整数会怎么样？再次运行程序，然后在第二个问题的答案中输入`41.9`。

该程序会因为`41.9`无法被打包成整数值而爆炸：`41.9`是一个`double`。最终，我们将研究如何处理类似问题的错误检查，但与此同时，如果人类输入了错误的内容导致程序崩溃，我们会责怪人类没有遵循指示，而不会担心这个问题。

第 16 行让人类输入一个 Scanner 对象将尝试转换为 double 值的内容，第 19 行让人类输入一个字符串。（任何东西都可以被打包为字符串，包括数字，所以这不太可能失败。）

尝试多次运行程序，注意何时会崩溃，何时不会。

