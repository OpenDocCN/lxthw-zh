        ## 练习 18：带字符串的 if 语句

        ```java

        1 import java.util.Scanner; 2
        3 public class SecretWord 4 {
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
        ```

        ```java
        public static void main( String[] args )
        {
        Scanner keyboard = new Scanner(System.in);
        ```

        ```java
        String secret = "please", guess;

        System.out.print( "What's the secret word? " ); guess = keyboard.next();

        if ( guess == secret )
        {
        System.out.println( "Impossible. (This will never be printed.)" );
        }

        if ( guess.equals(secret) )
        {
        System.out.println( "That's correct!" );
        }
        else
        {
        System.out.println( "Nope, the secret word is not \"" + guess +
        ```

        ```java
        "\"." );
        26    }
        27
        28 }
        29 }
        ```

        几个练习之前，你学会了比较字符串不像比较数字那么容易。所以让我们用一个你可以实际测试的例子来复习一下。

        ### 你应该看到的

        ```java

        What's the secret word? abracadabra
        Nope, the secret word is not "abracadabra".
        ```

        注意，和往常一样，我在偷偷加入一些东西。在第 9 行，我不仅仅是声明 *secret*，我还给它赋了一个值。也就是说，我“定义”了它（一次性声明和初始化）。

        无论如何，第 14 行的 `if` 语句永远不会为真。无论你输入什么，猜测 `==` 秘密永远不会成立。

        （我无法解释为什么，因为那样会涉及太多细节，但这与`==`只比较变量的浅层值有关，两个字符串的浅层值只有在它们引用相同的内存位置时才相等。）

        有效的方法是使用`.equals()`方法（它比较变量的深层值而不是它们的浅层值）。如果他们输入了正确的秘密词，这将为真。

