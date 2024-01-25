## 练习 9：使用用户输入进行计算

既然我们知道如何从用户那里获取输入并将其存储到变量中，而且我们也知道如何进行一些基本的数学运算，我们现在可以编写我们的第一个*有用*的程序了！

```java

 1 import java.util.Scanner;
 2 
 3 public class BMICalculator
 4 {
 5     public static void main( String[] args )
 6     {
 7         Scanner keyboard = new Scanner(System.in);
 8         double m, kg, bmi;
 9 
10         System.out.print( "Your height in m: " );
11         m = keyboard.nextDouble();
12 
13         System.out.print( "Your weight in kg: " );
14         kg = keyboard.nextDouble();
15 
16         bmi = kg / (m*m);
17 
18         System.out.println( "Your BMI is " + bmi );
19     }
20 }
```

### 你应该看到什么

```java

Your height in m: 1.75 Your weight in kg: 73
Your BMI is 23.836734693877553
```

这个练习（希望）相当简单。我们有三个变量（都是双精度）：*m*（米）、*kg*（千克）和*bmi*（身体质量指数）。我们读取*m*和*kg*的值，但*bmi*的值不是来自人类，而是计算的结果。在第 16 行，我们计算质量除以身高的平方，并将结果存储到*bmi*中。然后我们将其打印出来。

身体质量指数（BMI）通常被健康和营养专业人员用来估计人群的体脂肪。因此，这个结果对健康专业人员来说是有信息价值的。目前我们只能做到这些。

最终，我们将学会如何根据 BMI 的值在屏幕上显示不同的消息，但目前这就够了。

今天是一个相当简单的任务，但我在学习挑战中为你准备了一些挑战，应该会让事情变得更加困难。

### 学习挑战

1.  添加一些变量并更改程序，以便人类可以使用磅和英寸输入他们的体重和身高，然后将这些值转换为千克和米，以计算 BMI。

    ```java
    Your height in inches: 69 Your weight in pounds: 160 Your BMI is 23.625289
    ```

1.  使人类可以分别输入他们的身高，一个是英尺，一个是英寸。

    ```java

    Your height (feet only): 5 Your height (inches): 9 Your weight in pounds: 160 Your BMI is 23.625289
    ```

