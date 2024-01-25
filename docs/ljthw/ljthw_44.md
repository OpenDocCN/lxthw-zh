            ## 练习 43：保存最高分

            现在你知道如何从文件中获取信息*以及*如何将信息放入文件，我们可以创建一个保存最高分的游戏！

            这是之前几个练习中的抛硬币游戏，但现在高分保存在运行之间。

            ```java

            6 public class CoinFlipSaved 7 {
            8  public static void main( String[] args ) throws Exception 9  {
            10    Scanner keyboard = new Scanner(System.in); 11
            14
            15
            File in = new File(saveFile);

            16
            if ( in.createNewFile() )

            17
            {

            18
            System.out.println("Save game file doesn't exist. Created.");

            19
            best = ­1;

            20
            bestName = "";

            21
            }

            22
            else

            23
            {

            24
            Scanner input = new Scanner(in);

            25
            bestName = input.next();

            26
            best = input.nextInt();

            27
            input.close();

            28
            System.out.println("High score is " + best + " flips in a row
            by "
            + bestName
            );

            29
            }

            30

            31

            32
            do

            33
            {

            34
            flip = 1 + (int)(Math.random()*2);

            35

            36
            if ( flip == 1 )

            37
            coin = "HEADS";

            38
            else

            39
            coin = "TAILS";

            40

            41
            System.out.println( "You flip a coin and it is... " + coin );

            42

            43
            if ( flip == 1 )

            44
            {

            50      else
            51      {
            54      }
            55    } while ( again.equals("y") );
            ```

            1.  ```java
                import java.util.Scanner;
                ```

            1.  ```java
                import java.io.File;
                ```

            1.  ```java
                import java.io.FileWriter;
                ```

            1.  ```java
                import java.io.PrintWriter; 5
                ```

            1.  ```java
                String coin, again, bestName, saveFile = "coin­flip­score.txt";
                ```

            1.  ```java
                int flip, streak = 0, best;
                ```

            1.  ```java
                streak++;
                ```

            1.  ```java
                System.out.println( "\tThat's " + streak + " in a row...." );
                ```

            1.  ```java
                System.out.print( "\tWould you like to flip again (y/n)? " );
                ```

            1.  ```java
                again = keyboard.next(); 49      }
                ```

            1.  ```java
                streak = 0;
                ```

            1.  ```java
                again = "n";
                ```

            ```java

            56
            57
            58
            59
            60
            61
            62
            63
            64
            65
            66
            67
            68
            69
            70
            71
            72
            ```

            ```java
            System.out.println( "Final score: " + streak );

            if ( streak > best )
            {
            System.out.println("That's a new high score!"); System.out.print("Your name: ");
            bestName = keyboard.next(); best = streak;
            }
            else if ( streak == best )
            {
            System.out.println("That ties the high score. Cool.");
            }
            else
            {
            System.out.println("You'll have to do better than " + streak + "
            ```

            ```java
            if you want a high score.");
            ```

            ```java
            73
            74
            75
            76
            77
            78
            79
            80
            81 }
            ```

            ```java
            }
            ```

            ```java
            // Save this name and high score to the file.
            PrintWriter out = new PrintWriter( new FileWriter(saveFile) ); out.println(bestName);
            out.println(best); out.close();
            ```

            ```java
            }
            ```

            ### 你应该看到什么

            ```java

            Save game file doesn't exist. Created. You flip a coin and it is... HEADS
            That's 1 in a row....
            Would you like to flip again (y/n)? y You flip a coin and it is.  HEADS
            That's 2 in a row....
            Would you like to flip again (y/n)? y You flip a coin and it is.  HEADS
            That's 3 in a row....
            Would you like to flip again (y/n)? n Final score: 3
            That's a new high score! Your name: Mitchell
            ```

            （好吧，我作弊了。我尝试了很多次才连续三次猜对。）

            在第 15 行，我们使用文件名`coin-flip-score.txt`创建了一个`File`对象。即使文件不存在，我们也可以这样做。

            在第 16 行有一个`if`语句，在条件中我调用了 File 对象的`createNewFile()`方法。这将检查文件是否存在。如果是，它将什么也不做并返回布尔值`false`。如果文件不存在，它将创建一个空文件并返回值`true`。

            当`if`语句为真时，这意味着保存游戏文件不存在。我们会这样说，并将合适的初始值放入变量 best 和 bestName 中。如果不是，那么已经有一个文件存在，所以我们使用 Scanner 对象从文件中获取现有的名称和最高分。很酷，对吧？

            第 32 到 57 行是现有的抛硬币游戏。我一点也没有改变这段代码。

            在第 59 行，我们需要弄清楚他们是否打破了最高分。如果是，我们会打印出相应的消息并让他们输入他们的名字。

            如果他们打破了最高分，我们会这样说，但他们不会因此而得到任何名声。

            并且在第 70 行，如果他们没有打破或并列最高分，`else`将运行。所以我们当然会嘲笑他们。

            在第 75 到 79 行，我们将当前的最高分以及最高得分者的名字保存到文件中。这可能是一个新分数，也可能是我们在程序开始时读取的先前值。

            ### 学习训练

            1.  更改程序，只有在高分发生变化时才保存到高分文件。

            1.  通过在文本编辑器中打开高分文件并手动更改它来“黑客”高分文件。用您惊人的幸运连胜给朋友留下深刻印象！

