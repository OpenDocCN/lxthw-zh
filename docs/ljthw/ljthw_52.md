            ## 练习 51：没有 foreach 循环的数组

            正如您现在可能已经注意到的那样，数组和 foreach 循环被设计为很好地配合使用。但也有一些情况下，我们一直在做的事情不起作用。

            +   foreach 循环无法*向后*迭代数组；它只能向前。

            +   foreach 循环不能用来更改数组槽中的值。foreach 循环变量是数组中的一个只读副本，更改它不会改变数组。

                此外，我们一直在使用初始化列表（花括号的东西）将值放入数组中，这有其自身的局限性：

            +   初始化列表只在声明数组时有效；你不能在代码的其他地方使用它。

            +   初始化列表最适合相对较小的数组，如果数组中有 1000 个值，初始化列表就不好玩了。

            +   如果我们希望数组中的值来自文件或者我们在输入代码时没有的其他地方，初始化列表就帮不上忙了。

                ```java

                1 public class ArraySlotAccess 2 {
                ```

                ```java
                3
                4
                5
                6
                7
                8
                9
                10
                11
                ```

                ```java
                public static void main( String[] args )
                {
                int[] arr = new int[3]; int i;
                ```

                ```java
                arr[0] = 0;
                arr[1] = 0;
                arr[2] = 0;
                ```

                ```java
                12
                arr[2] ); 13
                14
                15
                16
                17
                18
                19
                20
                arr[2] ); 21
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
                ```

                ```java
                System.out.println("Array contains: " + arr[0] + " " + arr[1] + " " +
                ```

                ```java
                // Fill each slot of this array with a random number 1­100 arr[0] = 1 + (int)(Math.random()*100);
                arr[1] = 1 + (int)(Math.random()*100); arr[2] = 1 + (int)(Math.random()*100);

                // Display them again.
                System.out.println("Array contains: " + arr[0] + " " + arr[1] + " " +

                // This is a bit silly, but try to understand it. i = 0;
                arr[i] = 1 + (int)(Math.random()*100); i = 1;
                arr[i] = 1 + (int)(Math.random()*100); i = 2;
                arr[i] = 1 + (int)(Math.random()*100);

                // Display them again. System.out.print("Array contains: "); i = 0;
                System.out.print(arr[i] + " "); i = 1;
                System.out.print(arr[i] + " "); i = 2;
                System.out.print(arr[i] + " ");
                ```

                所以还有另一种方法可以存储数组中的值并访问它们。事实上，这种方法比你一直在做的更常见。使用方括号和槽号，我们可以单独访问数组的槽。

                ```java

                61
                for ( i=0 ; i < arr.length ; i++ )
                62
                {
                63
                arr[i] = 1 + (int)(Math.random()*100);
                64
                }
                65

                66
                // Display them again.
                67
                System.out.print("Array contains: ");
                68
                for ( i=0 ; i < arr.length ; i++ )
                69
                {
                70
                System.out.print(arr[i] + " ");
                71
                }
                72
                System.out.println();
                73  }
                74 }

                38
                39
                40
                headed? 41
                42
                43
                44
                45
                46
                47
                48
                49
                50
                51
                52
                53
                54
                55
                56
                57
                58
                59
                60
                ```

                ```java
                System.out.println();
                ```

                ```java
                // This is even more silly but it works. Can you guess where this is

                i = 0;
                arr[i] = 1 + (int)(Math.random()*100); i++;
                arr[i] = 1 + (int)(Math.random()*100); i++;
                arr[i] = 1 + (int)(Math.random()*100); i++;

                // Display them again. System.out.print("Array contains: "); i = 0;
                System.out.print(arr[i] + " "); i++;
                System.out.print(arr[i] + " "); i++;
                System.out.print(arr[i] + " "); i++;
                System.out.println();

                // Ah! Let's just use a regular 'for' loop!
                ```

                ### 你应该看到的

                ```java

                Array contains: 0 0 0
                Array contains: 98 49 18
                Array contains: 83 77 1
                Array contains: 62 74 32
                Array contains: 40 17 54
                ```

                在第 5 行，我们创建了一个整数数组，没有使用初始化列表。`[3]`表示数组的容量为 3。由于我们没有提供值，数组中的每个槽最初都存有值`0`。一旦数组被创建，它的容量就不能改变。

                在第 8 到 10 行有一个惊喜。数组有 3 个槽，但槽号是基于 0 的。（指代数组槽的数字称为“索引”。总体上应该称为“索引”（INN-duh-SEEZ），但大多数人只说“索引”）。

                所以数组中的第一个槽是索引`0`。这个数组可以容纳三个值，所以最后一个索引是`2`。除了习惯它，你无法做任何事情。所以`arr.length`是`3`，但没有一个槽的索引是`3`。这可能会在一开始给你带来 bug，但最终你会学会的。

                无论如何，第 8 到 10 行将值`0`存储到数组的所有三个槽中。（这个值已经在其中了，所以这段代码没有任何用处。）

                在第 12 行，我们打印出数组中所有三个当前值，这样你就可以看到它们都是零。

                在第 15 到 17 行，我们将随机数放入数组的每个槽中。然后在第 20 行再次打印出来。

                从第 22 行开始，我做了一些傻事。在练习结束之前，请不要下判断。

                不管你为什么要这样做，你看到第 24 行基本上与第 15 行相同吗？第 24 行将一个随机数存储到数组的一个位置。哪个位置？索引取决于 i 的当前值。而 i 当前是`0`。所以我们将随机数存储到索引为`0`的槽中。明白了吗？

                所以在第 25 行，我们将 i 的值从`0`改为`1`。然后在第 26 行，我们将一个随机值存储在由 i 的值索引的槽中，所以索引是`1`。明白了吗？奇怪，但合法。

                我在第 31 到 38 行使用了类似的花招来再次在屏幕上显示所有的值。现在，这显然比我在第 20 行做的要糟糕。我的意思是，我用了 8 行代码来做我之前用一行代码做的事情。（跟着我。）

                在第 40 到 47 行，我们做的事情甚至可能比第 22 到 28 行更糟糕。第 41 和 42 行是一样的，但在第 43 行，我没有直接将`1`放入 i，而是说“增加 i 的值 1”。所以 i 原来是`0`；在第 43 行之后它变成了`1`。

                这种方法的唯一优势几乎是复制和粘贴更容易。第 42 和 43 行*完全相同*于第 44 和 45 行。第 46 和 47 行也是如此。我的意思是，完全一样。

                我们以类似的愚蠢方式在第 50 到 58 行显示它们。

                但也许你会想到。“为什么我要连续三次输入完全相同的行，而不是……”你知道一种允许你重复一段代码的东西，同时使一个变量每次增加一个的东西，对吧？

                没错：`for`循环就是这样的。我一点都不傻，对吧？

                第 61 到 64 行与第 41 到 47 行相同，只是我们让`for`循环处理重复和索引的变化。`for`循环的初始化表达式（第一部分）将 i 设置为`0`，这恰好是数组的最小合法索引。条件说“只要 i 小于`arr.length`（即`3`）就重复这个操作。”请注意，这是小于，而不是小于或等于，那样就太多了。更新表达式（第三部分）每次只是将 i 加 1。

                第 67 到 72 行显示了屏幕上的值。

                事实上，这种代码在 61 到 72 行之间可能看起来有点复杂，但在 Java 中使用数组时，你会一直写这样的代码。我甚至无法告诉你我有多少次为了处理数组而写了一个像那样的`for`循环。

                实际上，如果你的问题是“我怎么才能一个数组？”（在空白处填入你喜欢的任何任务。）答案是“用`for`循环。”几乎可以肯定。

                ### 学习演习

                1. 在代码的顶部，将数组的容量改为 1000 而不是 3。不要改变任何其他代码，然后重新编译和运行。猜猜看？底部的那些`for`循环可能会更难写和理解，但一旦写好，它们对于 1000 个值和 3 个值一样有效。这很酷。

