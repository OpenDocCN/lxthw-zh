## 练习 55：记录数组

记录很棒，数组更好，但是当你把记录放入数组时，这个生活中几乎没有你不能编码的东西。

```java

 1 class Student
 2 {
 3     String name;
 4     int credits;
 5     double gpa;
 6 }
 7 
 8 public class StudentDatabase
 9 {
10     public static void main( String[] args )
11     {
12         Student[] db;
13         db = new Student[3];
14 
15         db[0] = new Student();
16         db[0].name = "Esteban";
17         db[0].credits = 43;
18         db[0].gpa = 2.9;
19 
20         db[1] = new Student();
21         db[1].name = "Dave";
22         db[1].credits = 15;
23         db[1].gpa = 4.0;
24 
25         db[2] = new Student();
26         db[2].name = "Michelle";
27         db[2].credits = 132;
28         db[2].gpa = 3.72;
29 
30         for ( int i=0; i<db.length; i++ )
31         {
32             System.out.println("Name: " + db[i].name);
33             System.out.println("\tCredit hours: " + db[i].credits);
34             System.out.println("\tGPA: " + db[i].gpa + "\n");
35         }
36 
37         int max = 0;
38         for ( int i=1; i<db.length; i++ )
39             if ( db[i].gpa > db[max].gpa )
40                 max = i;
41 
42         System.out.println(db[max].name + " has the highest GPA.");
43     }
44 }
```

### 你应该看到什么

```java

Name: Esteban
Credit hours: 43
GPA: 2.9

Name: Dave
Credit hours: 15
GPA: 4.0

Name: Michelle
Credit hours: 132
GPA: 3.72

Dave has the highest GPA.
```

当你看到变量定义中某物的右侧有方括号时，那就是“某物的数组”。实际上，由于这本书快要结束了，也许我应该解释一下`public static` `void main`的业务。至少部分地。

```java

public static void main( String[] args )
```

这一行声明了一个名为 main 的函数。该函数需要一个参数：名为 args 的字符串数组（缩写为“arguments”）。该函数不返回任何值；它是`void`。

无论如何。

第 12 行声明了*db*作为一个可以容纳“学生数组”的变量。还没有数组，只是一个可能容纳数组的变量。就像我们说…

```java

int n;
```

…还没有整数。变量*n*可能容纳一个整数，但它里面还没有数字。*n*被声明但未定义。同样，一旦第 12 行执行完毕，*db*是一个*可能*指向学生数组的变量，但仍未定义。

幸运的是，我们不必等太久；第 13 行通过创建一个实际的具有三个槽的学生数组来初始化 db。此时，db 被定义，`db.length`为`3`，db 有三个合法索引：`0`，`1`和`2`。

好吧，在这一点上，*db*是一个学生记录的数组。除了它不是。*db*是一个学生*变量*的数组，每个变量都*可能*容纳一个学生记录，但没有一个变量是这样的。数组中的所有三个槽都未定义。

（从技术上讲，它们包含值`null`，这是 Java 中引用变量在其中没有对象时具有的特殊值。）

因此，在第 15 行，重要的是创建一个学生对象并将其存储到数组的第一个槽（索引`0`）中。然后在第 16 行，我们可以将一个值存储到数组 db 中索引`0`的学生记录的名字字段中。

让我们从外到内追踪它：

| 表达式 | 类型 | 描述 |
| --- | --- | --- |
| `db` | `students[]` | 一组学生记录 |
| `db[0]` | `students` | 一个单独的学生记录（第一个） |
| `db[0].name` | `String` | 数组中第一个学生的*name*字段 |
| `db.name` | 错误 | 整个数组没有一个名字字段 |

因此，第 16 行将一个值存储到数组中第一个记录的*name*字段中。第 17 和 18 行将值存储到该记录中的其余字段中。第 20 到 28 行创建并填充数组中的其他两个记录

尽管在第 30 到 34 行，我们使用循环在屏幕上显示所有的值。

然后，第 37 到 42 行找到了 GPA 最高的学生。这值得更详细解释。在第 37 行，定义了一个名为 max 的`int`。但 max 不会保存最高 GPA 的值；它只会保存它的索引。

所以当我把`0`放入 max 时，我的意思是“在代码的这一点上，就我所知，最高分的学生

在槽`0`中。”这可能不是真的，但由于我们还没有查看数据库中的任何值，这是一个很好的起点。

然后在第 38 行，我们设置循环来查看数组的每个槽。然而，请注意，循环从索引`1`（第二个槽）开始。为什么？

因为 max 已经是`0`。所以如果 i 也从`0`开始，那么`if`语句将进行以下比较：

```java

if ( db[0].gpa > db[0].gpa )
```

…这是浪费。因此，通过从`1`开始，第一次循环时，`if`语句将进行以下比较：

```java

if ( db[1].gpa > db[0].gpa )
```

“如果戴夫的 GPA 大于埃斯特万的 GPA，则将 max 从`0`更改为 i（`1`）的当前值。”

因此，当循环结束时，*max*包含具有最高 GPA 的记录的**索引**。这正是我们在第 42 行显示的内容。

### 学习演练

1.  将数组的容量更改为`4`而不是 3。不改变任何其他内容，编译并运行程序。你明白为什么程序会崩溃吗？

1.  现在添加一些代码，将值放入新学生的字段中。给这个新学生一个比“Dave”更高的 GPA，并确认代码正确地将他们标记为具有最高的 GPA。

1.  更改代码，使其查找具有最少学分的人，而不是具有最高 GPA 的人。

