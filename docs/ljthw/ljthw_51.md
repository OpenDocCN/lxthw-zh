            ## 练习 50：说数组中没有某个东西

            在生活中，某些类型的陈述之间存在一般缺乏对称性。

            存在一只白色的乌鸦。

            这个陈述很容易证明。开始观察乌鸦。一旦找到一只白色的，就停下。完成。

            不存在白色的乌鸦。

            这个陈述*要难得多，因为要证明它，我们必须收集世界上所有符合乌鸦资格的东西。如果我们已经*全部*看过它们，却没有找到任何白色的乌鸦，那么我们才能安全地说*没有*存在。

            1 import java.util.Scanner; 2

            3 public class ItemNotFound 4 {

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

            35 }

            public static void main( String[] args )

            {

            Scanner keyboard = new Scanner(System.in);

            String[] heroes = {

            "阿布德鲁斯"，"阿喀琉斯"，"埃涅阿斯"，"阿贾克斯"，"安菲特里翁"，"贝勒福龙"，"卡斯特尔"，"克里西普"，"戴达罗斯"，"迪俄米德"，"埃琉西斯"，"尤诺斯图斯"，"盖尼米德"，"赫克托尔"，"伊阿索"，"贾森"，

            "梅勒阿格尔"，"奥德修斯"，"奥耳佩斯"，"佩尔修斯"，"忒修斯"}; String guess;

            boolean found;

            System.out.print( "小测验！说出希腊神话中的任何凡人英雄：" ); guess = keyboard.next();

            found = false;

            for ( String hero : heroes )

            {

            if ( guess.equals(hero) )

            {

            System.out.println( "那是正确的！" ); found = true;

            }

            }

            if ( found == false )

            {

            System.out.println( "不，" + guess + "不是希腊凡人英雄。" );

            }

            }

            希望您尝试了昨天练习中的学习演习。

            ### 你应该看到的

            ```java

            Pop Quiz! Name any mortal hero from Greek mythology: Hercules No, Hercules wasn't a Greek mortal hero.
            ```

            大多数学生希望通过在循环内部放置另一个`if`语句（或`else`）来解决这个问题，以表明“未找到”。但这是行不通的。如果我想知道是否找到了某物，那么一旦我找到它，就可以这样说。但是，如果我想知道某物从未被找到，您必须等到循环结束才能确定。

            所以在这种情况下，我使用了一种称为“标志”的技术。标志是一个以一个值开始的变量。如果发生了某事，该值将被更改。然后在程序的后面，您可以使用标志的值来查看是否发生了该事件。

            我的标志变量是一个名为 found 的布尔变量，在第 20 行设置为`false`。如果找到匹配，我们会这样做，并在第 26 行将标志更改为`true`。请注意，在循环内部没有可以将标志更改为`false`的代码，因此一旦它被翻转为`true`，它将保持不变。

            然后在第 30 行，在循环结束后，您可以检查标志。如果它仍然是`false`，那么我们知道

            循环内的`if`语句从未为真，因此我们从未找到我们要找的东西。

