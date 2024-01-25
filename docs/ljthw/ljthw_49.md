        ## 练习 48：数组-单个变量中的多个值

        在这个练习中，你将学到两件新事物。第一件事*非常*重要，第二件事只是有点有趣。

        ```java

        1 public class ArrayIntro 2 {
        3  public static void main( String[] args ) 4 {
        5  String[] planets = { "Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune" };
        ```

        ```java
        6
        7
        8
        9
        10
        11
        12 }
        ```

        ```java
        for ( String p : planets )
        {
        System.out.println( p + "\t" + p.toUpperCase() );
        }
        ```

        ```java
        }
        ```

        在 Java 中，“数组”是一种类型的变量，它有一个名称（“标识符”），但包含多个变量。在我看来，只有当你能够处理数组时，你才能成为一个真正的程序员。所以，这是个好消息。你快要成功了！

        ### 你应该看到的内容

        ```java

        Mercury MERCURY Venus VENUS
        Earth EARTH
        Mars MARS Jupiter JUPITER Saturn SATURN Uranus URANUS Neptune NEPTUNE
        ```

        在第 5 行，我们声明并定义了一个名为*planets*的变量。它不仅仅是一个字符串：注意方括号。这个变量是一个字符串数组。这意味着这个变量包含了所有八个字符串，并且它们被分成不同的槽，所以我们可以逐个访问它们。

        这一行上的花括号用于不同于通常的目的。所有这些值都在引号中，因为它们是字符串。每个值之间有逗号，然后整个初始化列表在花括号中。最后有一个分号。

        这个练习中的第二个新东西是一种新的`for`循环。（有时被称为`foreach`循环，因为它有点像另一种编程语言中的循环，那里的关键字实际上是`foreach`而不是`for`。）

        在第 7 行，你将看到这个 foreach 循环在运行。你可以这样大声朗读：“对于数组‘planets’中的每个字符串‘p’……”

        因此，在这个 foreach 循环的循环体内，字符串变量 p 将获得字符串数组 planets 中每个值的副本。也就是说，第一次循环时，p 将包含数组中的第一个值（`"Mercury"`）的副本。然后第二次循环时，p 将包含数组中的第二个值（`"Venus"`）的副本。依此类推，直到数组中的所有值都被看到。然后循环将自动停止。

        在循环体内（第 9 行），我们只是打印出*p*的当前值和*p*的大写版本。可能只是为了好玩。

        这种新的`for`循环只适用于像这样的复合变量：只有一个名称的变量。

        但包含多个值。数组不是 Java 中唯一的复合变量，但我们在本书中不会研究其他任何复合变量。

        数组很重要，所以这就够了。在给你增加更多内容之前，我想要*绝对确定*你理解了这个任务中发生的事情。
