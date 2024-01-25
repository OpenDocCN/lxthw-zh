## 练习 31：逐个添加值

这个练习将演示一件你必须经常做的事情：处理一次只得到一个值。

如果我让你让人类输入三个数字并将它们相加，并且我保证他们只需要输入确切的三个数字（不多，不少），你可能会写出这样的东西：

```java

int a, b, c, total;
a = keyboard.nextInt(); b = keyboard.nextInt(); c = keyboard.nextInt(); total = a + b + c;
```

如果我告诉你人类要输入*五*个数字，你的代码可能是这样的：

```java

double num1, num2, num3, num4, num5, total; num1 = keyboard.nextDouble();
num2 = keyboard.nextDouble(); num3 = keyboard.nextDouble(); num4 = keyboard.nextDouble(); num5 = keyboard.nextDouble(); total = num1+num2+num3+num4+num5;
```

但是，如果我告诉你他们想要输入一百个数字呢？或者一万个？或者*可能*是三个，*可能*是五个，我不确定？那么你需要另一种方法。你需要一个循环（这就是我们重复事情的方式），并且你需要一个变量，它将随着值的逐个添加而逐渐增加。一个从“空白”开始并逐个添加值的变量称为“累加器”变量，尽管这是一个相当古老的词，所以如果你的编程朋友年龄不到四十岁，他们可能从未听说过。

无论如何，基本想法看起来是这样的：

```java

1 import java.util.Scanner; 2
3 public class RunningTotal
4 {
5

public static void main( String[] args )
6

{
7

Scanner keyboard = new Scanner(System.in);
8

9

int current, total = 0;
10

11

System.out.print("Type in a bunch of values and I'll add them up. ");
12

System.out.println("I'll stop when you type a zero.");
13

14

do
15

{
16

System.out.print("Value: ");
17

current = keyboard.nextInt();
18

int newtotal = current + total;
19

total = newtotal;
20

System.out.println("The total so far is: " + total);
21

} while ( current != 0 );
22

23

System.out.println("The final total is: " + total);
24

}
25
}

```

### 你应该看到的是

```java

Type in a bunch of values and I'll add them up. I'll stop when you type a zero. Value: 3
The total so far is: 3 Value: 4
The total so far is: 7 Value: 5
The total so far is: 12 Value: 6
The total so far is: 18 Value: 0
The total so far is: 18 The final total is: 18
```

我们需要两个变量：一个用于保存他们刚刚输入的值（*current*），一个用于保存运行总数（嗯...*total*）。在第 9 行，我们确保首先将零放入*total*中。很快你就会明白为什么。

在第 17 行，人类可以输入一个数字。这是在 do-while 循环的主体内，无论如何都会运行至少一次，所以这段代码总是会发生。假设他们一开始输入`3`。

在第 18 行，魔法的第一部分发生了。我们声明了一个名为*newtotal*的新变量，并将其值设置为人类刚刚输入的数字加上*变量*total 中已经存在的值。一开始*total*中有一个零，所以这行代码将零添加到*current*中，并将该数字存储到*newtotal*中。

然后在第 19 行，魔法的第二部分发生了：我们用 newtotal 的当前值替换 total 中的值（零）。所以现在 total 不再是零；它具有与 current 相同的值。所以 total 是`0`，现在是`3`。

然后我们打印小计，并在第 21 行检查*current*是否为零。如果不是，则循环重复到第 14 行。

人类可以输入第二个数字。假设是`4`。变量 newtotal 被初始化为

current（`4`）加上 total（`3`），所以 newtotal 是`7`。然后在第 19 行，我们将 total 的值更改为`7`。

条件再次被检查，过程继续。最终，人类输入了一个`0`，那个`0`被添加到总数中（这不会伤害它），条件变为假，所以 do-while 循环停止循环。

在练习结束之前，我应该提到两件事：

1.  因为变量*newtotal*在第 18 行被声明（并定义），所以该变量的范围仅限于 do-while 循环的主体。这意味着在第 21 行，*newtotal*不再在范围内，因此在 do-while 循环的条件中引用*newtotal*的任何尝试都会导致错误。该变量在每次循环中不断创建和销毁。这有点低效。

1.  我们甚至可以编写代码而不使用*newtotal*变量。由于 Java 在将右侧的最终值存储到左侧命名的变量之前，我们可以将第 18 行和第 19 行合并为一行：

    ```java

    total = current + total;
    ```

    这个工作完全正常。（事实上，你以前见过它。）

    ### 学习训练

    1.  重写代码，使用`while`循环而不是 do-while 循环。确保它能够编译并确保它仍然有效。然后改回来。

    1.  更改 do-while 循环的条件，使得当*newtotal*恰好为 20 时循环停止。

哦？它不编译，因为*newtotal*超出了范围？更改*newtotal*声明的位置，使其正常工作。

