## 练习 56：从文件中读取记录的数组（温度重访）

这个练习从互联网上的一个文件中填充了一个记录数组。到目前为止，您应该知道您是否需要下载此文件的副本，还是您的计算机可以直接从互联网上打开它。

+   http://learnjavathehardway.org/txt/avg­daily­temps­with­dates­atx.txt

与本书中迄今为止使用的所有其他文件不同，这个数据文件正是我从戴顿大学的平均日温度档案中下载的。这意味着三件事：

1.  文件的第一行没有数字告诉我们有多少记录。

1.  除了温度之外，每个记录还包括样本的月份、日期和年份。

1.  文件中有错误数据。特别是，“当数据不可用时，我们使用`-99`作为无数据标志。”

因此，有些天的温度是-99。我们将不得不在代码中处理这个问题。

```java

 1 import java.util.Scanner;
 2 
 3 class TemperatureSample
 4 {
 5     int month, day, year;
 6     double temperature;
 7 }
 8 
 9 public class TemperaturesByDate
10 {
11     public static void main(String[] args) throws Exception
12     {
13         String url = 
"http://learnjavathehardway.org/txt/avg­daily­temps­with­dates­atx.txt";
14         Scanner inFile = new Scanner((new java.net.URL(url)).openStream());
15 
16         TemperatureSample[] tempDB = new TemperatureSample[10000];
17         int numRecords, i = 0;
18 
19         while ( inFile.hasNextInt() && i < tempDB.length )
20         {
21             TemperatureSample e = new TemperatureSample();
22             e.month = inFile.nextInt();
23             e.day   = inFile.nextInt();
24             e.year  = inFile.nextInt();
25             e.temperature = inFile.nextDouble();
26             if ( e.temperature == ­99 )
27                 continue;
28             tempDB[i] = e;
29             i++;
30         }
31         inFile.close();
32         numRecords = i;
33 
34         System.out.println(numRecords + " daily temperatures loaded.");
35 
36         double total = 0, avg;
37         int count = 0;
38         for ( i=0; i<numRecords; i++ )
39         {
40             if ( tempDB[i].month == 11 )
41             {
42                 total += tempDB[i].temperature;
43                 count++;
44             }
45         }
46 
47         avg = total / count;
48         avg = roundToOneDecimal(avg);
49         System.out.println("Average daily temperature over " + count + " days 
in November: " + avg);
50     }
51 
52     public static double roundToOneDecimal( double d )
53     {
54         return Math.round(d*10)/10.0;
55     }
56 }
```



### 你应该看到什么

```java

6717 daily temperatures loaded.
Average daily temperature over 540 days in November: 59.7
```

第 3 到 7 行声明了我们的记录，它将存储单个平均日温度值（一个

`double`），还有月份、日期和年份的字段。

第 16 行定义了一个记录数组。但是我们有一个问题。我们无法在不提供容量的情况下定义数组，而在看到文件中有多少记录之前，我们不知道需要多大的容量。这个问题有三种可能的解决方案：

1.  不要使用数组。使用其他东西，比如一个可以在添加条目时自动增长的数组。这实际上可能是正确的解决方案，但是“其他东西”超出了本书的范围。

1.  读取文件两次。首先只计算记录的数量，然后使用完美大小创建数组。然后再次读取文件将所有值读入数组。这样做很慢，但有效。

1.  不要担心使数组的大小合适。只需使其“足够大”。然后在读取它们时计算实际拥有的记录数量，并在任何循环中使用该计数，而不是数组的容量。这并不完美，但它有效且简单。编写软件有时需要妥协，这就是其中之一。

因此，第 16 行声明了数组并定义为有一万个槽位：“足够大”。

在第 19 行，我们开始一个循环，读取文件中的所有值。我们使用索引变量`i`来跟踪数组中下一个需要填充的槽位。因此，只要文件中还有更多整数，并且我们的数组容量还没有用完，我们的循环就会继续。

仅仅因为我们通过使数组“足够大”来节省了一些步骤，并不意味着我们会对此感到愚蠢。如果文件最终比我们的数组容量大，我们希望尽早停止读取文件，而不是因为`ArrayIndexOutOfBounds`异常而使程序崩溃。

21 行定义了一个名为`e`的`TemperatureSample`记录。22 到 25 行将文件中的下几个值加载到该记录的适当字段中。

但是！请记住，我们的文件中有“缺失”的值。有些天的温度读数是

`-99`，所以我们在第 26 行放置了一个`if`语句来检测它，然后将它们放入我们的数据库中。

然后在第 27 行有一些新东西：Java 关键字`continue`。`continue`只能在循环体内合法。它的意思是“跳过循环体中剩余的代码行，然后返回顶部进行下一次迭代。”

这实际上丢弃了当前（无效）记录，因为它跳过了第 28 和 29 行，这两行将当前记录存储在数组中的下一个可用槽位中，然后增加索引。

有些人不喜欢使用`continue`，他们会这样写：

```java

if ( e.temperature != ­99 )
{
    tempDB[i] = e; i++;
}
```

这也完全没问题。只有当温度不是`-99`时，才将此条目放入数组中。我更喜欢使用`continue`，因为这样的代码对我来说更清晰，但是理智的人可能会有不同意见。选择对你来说最有意义的方式。

一旦在第 31 行完成循环，我们确保关闭文件，然后将最终索引存储到`numRecords`中，以便我们可以在任何循环中使用它，而不是`tempDB.length`。毕竟，我们使数组比我们需要的大，最后的 3283 个槽（在这个例子中）是空的。仅循环到`numRecords`会更有效一些，我们可以通过这种方式避免检查任何无效的记录。

在第 34 行，我们在屏幕上显示记录的数量，这可以帮助您查看是否在读取时出现了任何问题。

第 36 至 45 行循环遍历所有我们的记录。任何月份字段为`11`（11 月）的记录都会被添加到一个运行总数中，我们也在此过程中计算匹配记录的总数。

然后，当循环结束时，我们可以通过将总和除以计数来获得数据库中所有 11 月份每日温度的平均值。

现在，我的程序的第一个版本的整体平均温度是`59.662962962963`。这不仅看起来不好，而且不正确：所有输入温度只精确到十分之一度。因此，显示具有十几个有效数字的结果看起来比实际更准确。

因此，在第 52 至 55 行，您将找到一个小小的函数，用于将数字四舍五入到小数点后一位。据我所知，Java 没有内置的此功能，但它确实有一个内置的将数字四舍五入到最接近的整数的函数：`Math.round()`。所以我将数字乘以十，四舍五入，然后再除以十。也许有更好的方法，但我喜欢这样做。

第 48 行将平均温度作为参数传递给我的函数，然后取舍返回值并将其存储为`avg`的新值。

### 学习演练

1.  访问戴顿大学的温度档案，并下载一个附近城市的温度数据文件！让你的代码从该文件中读取数据。

1.  更改代码以查找其他内容，比如二月份的最高温度或其他你感兴趣的内容。

1.  尝试在屏幕上打印整个`TemperatureSample`记录。类似于这样：

```java

TemperatureSample ts = tempDB[0]; System.out.println( ts );
```

请注意，它不会打印像 ts.year 这样的整数或像`ts.temperature`这样的双精度；它试图在屏幕上显示整个记录。编译并运行文件。屏幕上显示了什么？

尝试更改索引以从数组中提取不同的值，并查看它如何改变打印出来的内容。

