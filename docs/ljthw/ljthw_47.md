## 练习 46：嵌套 for 循环

在编程中，“嵌套”一词通常意味着将某物放在同一物体内。“嵌套循环”将是两个循环，一个在另一个内部。如果你做对了，那么内部循环将在外部循环执行一次迭代时重复所有迭代。


```java

 1 public class NestingLoops
 2 {
 3     public static void main( String[] args )
 4     {
 5         // this is #1 ­ I'll call it "CN"
 6         for ( char c='A'; c <= 'E'; c++ )
 7         {
 8             for ( int n=1; n <= 3; n++ )
 9             {
10                 System.out.println( c + " " + n );
11             }
12         }
13 
14         System.out.println("\n");
15 
16         // this is #2 ­ I'll call it "AB"
17         for ( int a=1; a <= 3; a++ )
18         {
19             for ( int b=1; b <= 3; b++ )
20             {
21                 System.out.print( "(" + a + "," + b + ") " );
22             }
23             // * You will add a line of code here.
24         }
25 
26         System.out.println("\n");
27 
28     }
29 }
```


### 你应该看到什么

```java

A 1
A 2
A 3
B 1
B 2
B 3
C 1
C 2
C 3
D 1
D 2
D 3
E 1
E 2
E 3
(1,1) (1,2) (1,3) (2,1) (2,2) (2,3) (3,1) (3,2) (3,3) 
```

### 学习演习

1.  看看嵌套循环的第一组（“CN”）。哪个变量变化更快？是变量

    由外部循环（c）控制还是由内部循环（n）控制的变量？

1.  更改循环的顺序，使“c”循环在内部，“n”循环在外部。输出如何改变？

1.  看看第二组嵌套循环（“AB”）。将`print（）`语句更改为`println（）`。输出如何改变？（然后将其改回`print（）`。）

1.  在内部循环（“b”循环）的关闭大括号后添加一个`System.out.println（）`语句，但仍在外部循环内。输出如何改变？

