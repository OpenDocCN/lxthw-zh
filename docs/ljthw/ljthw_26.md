## 练习 25：更复杂的随机数

上一个练习中有一些复杂的思考，所以这个练习不会教授新的东西，而是会花更多时间来学习相同的概念。


```java

 1 public class RandomNumbers2
 2 {
 3     public static void main( String[] args )
 4     {
 5         int a, b, c, d, e, low, high;
 6 
 7         a = 1 + (int)(Math.random()*10);
 8         b = 1 + (int)(Math.random()*10);
 9         c = 1 + (int)(Math.random()*10);
10         d = 1 + (int)(Math.random()*10);
11         e = 1 + (int)(Math.random()*10);
12 
13         System.out.println( a + "\t" + b + "\t" + c + "\t" + d + "\t" + e );
14 
15         a = 1 + (int)(Math.random()*100);
16         b = 1 + (int)(Math.random()*100);
17         c = 1 + (int)(Math.random()*100);
18         d = 1 + (int)(Math.random()*100);
19         e = 1 + (int)(Math.random()*100);
20 
21         System.out.println( a + "\t" + b + "\t" + c + "\t" + d + "\t" + e );
22 
23         a = 70 + (int)(Math.random()*31); // 31 is 100­70+1
24         b = 70 + (int)(Math.random()*31);
25         c = 70 + (int)(Math.random()*31);
26         d = 70 + (int)(Math.random()*31);
27         e = 70 + (int)(Math.random()*31);
28 
29         System.out.println( a + "\t" + b + "\t" + c + "\t" + d + "\t" + e );
30 
31         low  =  70;
32         high = 100;
33 
34         a = low + (int)(Math.random()*(high­low+1));
35         b = low + (int)(Math.random()*(high­low+1));
36         c = low + (int)(Math.random()*(high­low+1));
37         d = low + (int)(Math.random()*(high­low+1));
38         e = low + (int)(Math.random()*(high­low+1));
39 
40         System.out.println( a + "\t" + b + "\t" + c + "\t" + d + "\t" + e );
41     }
42 }
```

### 你应该看到什么

```java

7
9
3
3
3
10
53
78
17
75
76
96
99
85
86
99
91
96
99
83
```

（再次强调，你看不到这一点。这些数字将是随机的。）

在第 7 到 11 行，我们选择了五个随机数。每个数字都乘以 10 并转换为整数以截断它（因此每个随机数是 10 个数字之一：0 到 9）。然后对每个数字加 1，所以变量 a 到 e 每个都得到 1 到 10 的随机数。

在第 15 到 19 行，我们再次选择了五个随机数。每个数字都乘以一

百分之一并转换为整数以截断它（因此每个随机数是 100 个数字之一：0 到 99）。然后对每个数字加 1，所以变量 a 到 e 每个都得到 1 到 100 的随机数。

在第 23 到 27 行，我们选择了另外五个随机数。每个数字都乘以 31 并转换为整数以截断它（因此每个随机数是 31 个数字之一：0 到 30）。然后每个数字都加上 70。`0`加上`70`得到 70。`1`加上`70`得到 71。`23`加上`70`得到 93。`30`（最大值）加上`70`得到 100。因此，变量 a 到 e 每个都得到 70 到 100 的随机数。

因此，一般公式是这样的：

```java

int a = low + (int)(Math.random() * range);
```

`low`是我们想要的最小可能数字。`range`是**范围内**应该有多少个随机数。如果你知道你的最小可能数字和最大可能数字，但不知道有多少数字，那么公式是：

```java

int range = high ­ low + 1;
```

如果我想要的最小随机数是`1`，最大随机数是`5`，那么范围是五。5 减 1 是 4，然后加 1 来解决减法给出的两个数字之间的距离，而不是沿途停止点的计数。 8

你甚至可以这样写公式：

```java

int a = low + (int)(Math.random()*(high­low+1));
```

这将使计算机从`low`到`high`中选择一个随机数。这正是我们在第 34 到 38 行所做的。

### 学习演练

1.  更改第 31 行和第 32 行的`low`和`high`的值为其他值。编译并运行程序多次，以确认您总是在该范围内获得随机数。

1.  编程中常见的逻辑错误是，如果您意外地计算距离而不是停止，就会发生“栅栏问题”。这个名字来自以下脑筋急转弯：如果我需要用一堆略长于一米的木板建造五米长的栅栏，我需要多少栅栏柱？你需要五块木板，但需要六根栅栏*柱*。

