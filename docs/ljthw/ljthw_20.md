        ## 练习 19：使用 if 和 else 链进行互斥

        在上一个练习中，我们看到使用`else`可以更容易地包含一块备用代码，当`if`语句没有发生时，你想要运行的。

        ```java

        1 import java.util.Scanner; 2
        3 public class BMICategories 4 {
        ```

        ```java
        5
        6
        7
        8
        9
        10
        11
        12
        13
        14
        15
        16
        17
        18
        19
        20
        21
        22
        23
        24
        25
        26
        27
        28
        29
        30
        31
        32
        33
        34
        35
        36
        37
        38
        39
        40
        41
        42
        43
        44
        45
        46
        47
        48 }
        ```

        ```java
        public static void main( String[] args )
        {
        Scanner keyboard = new Scanner(System.in);
        ```

        ```java
        double bmi;

        System.out.print( "Enter your BMI: " ); bmi = keyboard.nextDouble();

        System.out.print( "BMI category: " ); if ( bmi < 15.0 )
        {
        System.out.println( "very severely underweight" );
        }
        else if ( bmi <= 16.0 )
        {
        System.out.println( "severely underweight" );
        }
        else if ( bmi < 18.5 )
        {
        System.out.println( "underweight" );
        }
        else if ( bmi < 25.0 )
        {
        System.out.println( "normal weight" );
        }
        else if ( bmi < 30.0 )
        {
        System.out.println( "overweight" );
        }
        else if ( bmi < 35.0 )
        {
        System.out.println( "moderately obese" );
        }
        else if ( bmi < 40.0 )
        {
        System.out.println( "severely obese" );
        }
        else
        {
        System.out.println( "very severely/\"morbidly\" obese" );
        }
        ```

        ```java
        }
        ```

        但是，如果替代代码是……另一个`if`语句呢？

        ### 你应该看到什么

        ```java

        Enter your BMI: 22.5
        BMI category: normal weight
        ```

        （*注意*：尽管 BMI 是人体脂肪的一个很好的估计值，但这个公式对于肌肉量很大的运动员，或者身材极矮或极高的人来说效果不佳。如果你担心

        你的 BMI，请咨询医生。）

        请注意，即使几个`if`语句可能都为真，只有第一个为真的`if`语句才会在屏幕上打印它的消息。没有其他消息被打印：只有一个。这就是使用`else`与`if`的威力。

        在第 15 行有一个`if`语句，检查你的 BMI 是否小于`15.0`，如果是，则显示该体重指数的适当类别。

        第 19 行以`else`开头。这个 else 关注前面的`if`语句——第 15 行的那个——以确定它是否应该运行它的代码块或自动跳过它。假设你输入了 BMI 为`22.5`，那么前面的`if`语句不成立，也没有运行。因为那个`if`语句失败了，else 将自动执行它的代码块。

        然而，这段代码块紧跟在`else`后面，后面是一个新的`if`语句！这意味着当前面的`if`语句为假时，语句`if ( bmi <= 16.0 )`才会被考虑。

        每当我的学生对此感到困惑时，我都会给他们一个类比。（有点粗糙，但似乎有所帮助。）

        想象一下你是单身（浪漫方面的意思），你和一些朋友在酒吧或商场或其他地方。在对面，你看到一个真的很有吸引力的单身，你悄声告诉其他人：“好的，我先来。”

        你的团队走向这个人，但除非他们看到你的表现如何，否则没有人会开始调情。如果你似乎正在取得进展，你的朋友们会退后，让你畅所欲言。然而，如果你被拒绝，那么你的其他伙伴之一就会感到有机会尝试并发起进攻。

        这基本上就是`else if`的作用。一个`else if`语句（一个在`if`语句前面有`else`的`if`语句）包含一个可能为真或可能为假的条件。但是`else`意味着`if`语句只会检查它是否为真或假，假设前面的`if`语句（只有紧接着的那个）为假。

        第 23 行的`else`使得第 19 行开始的`if`语句推迟到第 19 行的`if`语句：如果为真，第 23 行的`if`语句将跳过，即使它本来是真的。第 27 行的`else`使得它的`if`语句推迟到前面的`if`语句，依此类推。最后一行 43 的`else`就像一群中最小的狗：只有在链中所有前面的`if`语句都为假时才会执行。

        我们将在下一个练习中再多谈一些这个问题，现在就到此为止。

        ### 学习演习

        1.  从第 27 行`if`语句前面删除`else`。运行程序，然后输入

            `15.5`作为 BMI。你看到了吗，这使得第 27 行的`if`语句“打破了规矩”，不再关心它之前的`if`语句？

        1.  不要让人直接输入他们的 BMI，让他们输入身高和体重，然后为他们计算 BMI。

