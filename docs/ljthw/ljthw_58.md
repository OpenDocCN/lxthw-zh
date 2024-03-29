## 练习 57：一副扑克牌

在这本书结束之前，我需要向你展示如何使用记录数组来模拟一副扑克牌。

```java
 1 class Card
 2 {
 3     int value;
 4     String suit;
 5     String name;
 6 
 7     public String toString()
 8     {
 9         return name + " of " + suit;
10     }
11 }
12 
13 public class PickACard
14 {
15     public static void main( String[] args )
16     {
17         Card[] deck = buildDeck();
18         // displayDeck(deck);
19 
20         int chosen = (int)(Math.random()*deck.length);
21         Card picked = deck[chosen];
22 
23         System.out.println("You picked a " + picked + " out of the deck.");
24         System.out.println("In Blackjack your card is worth " + picked.value + " 
points.");
25     }
26 
27     public static Card[] buildDeck()
28     {
29         String[] suits = { "clubs", "diamonds", "hearts", "spades" };
30         String[] names = { "ZERO", "ONE", "two", "three", "four", "five", "six",
31             "seven", "eight", "nine", "ten", "Jack", "Queen", "King", "Ace" };
32 
33         int i = 0;
34         Card[] deck = new Card[52];
35 
36         for ( String s: suits )
37         {
38             for ( int v = 2; v <= 14 ; v++ )
39             {
40                 Card c = new Card();
41                 c.suit = s;
42                 c.name = names[v];
43                 if ( v == 14 )
44                     c.value = 11;
45                 else if ( v > 10 )
46                     c.value = 10;
47                 else
48                     c.value = v;
49 
50                 deck[i] = c;
51                 i++;
52             }
53         }
54         return deck;
55     }
56 
57     public static void displayDeck( Card[] deck )
58     {
59         for ( Card c : deck )
60             System.out.println(c.value + "\t" + c);
61     }
62 }
```

### 你应该看到什么

```java

You picked a seven of hearts out of the deck. In Blackjack your card is worth 7 points.
```

当然，即使这几乎是最后一个练习，我也忍不住加入了一些新东西。你想学点新东西，不是吗？

首先，我在记录中偷偷加了一个函数。（实际上，因为这个函数在一个类中，它不是一个函数，而是一个“方法”。）

这个方法被命名为 to`String`。它没有参数，并返回一个`String`。在这个方法的主体中，我们通过连接名称字段、花色字段和单词`of`来创建一个字符串。这个方法不需要任何参数，因为它可以访问记录的字段。（事实上，这就是它成为“方法”而不是“函数”的原因。）

否则，`Card`记录应该是你期望的：它有卡的值（2-11）、花色名称和卡本身的名称的字段。

在第 17 到 24 行，你可以看到`main()`，它真的很短。第 17 行声明了一个卡片数组，并使用`buildDeck()`函数的返回值进行初始化。

第 18 行被注释掉了，但当我最初编写这个程序时，我使用了`displayDeck()`

确保`buildDeck()`函数是否正常工作。

第 20 行选择了一个介于`0`和`deck.length - 1`之间的随机数。你可能会注意到这恰好是数组中合法索引的范围，这不是巧合。

实际上，你也可以说第 20 行选择了数组中的一个随机索引，或者第 20 行随机选择了数组的一个槽位。

然后在第 21 行，我们声明了一个新的`Card`变量`picked`，并给它一个从数组中随机选择的值。

第 23 行看起来相当无聊，但实际上发生了魔法。`picked`是什么类型的变量？它是一张卡。通常当你尝试像这样在屏幕上打印整个记录时，Java 不知道你想要打印哪些字段或以什么顺序打印，所以它只是在屏幕上打印垃圾。（你在上一个练习的学习中看到了吧？）

但是，如果你在记录中提供了一个名为`toString()`的方法，它返回一个`String`并且没有参数，那么在这种情况下，Java 将在幕后调用该方法。它将获取返回值并打印出来，而不是垃圾。

因此，第 23 行将在屏幕上打印出运行所选卡的`toString()`方法的结果。相比之下，第 24 行确实很无聊。它打印出所选卡的值字段。

在我们开始`buildDeck()`，这是这个练习中最复杂的部分之前，让我们跳到`displayDeck()`函数。`displayDeck()`期望你传入一个`Card`数组作为参数。

然后在第 59 行，我们看到了一些我们在前几个练习中没有见过的东西：一个`foreach`循环。这表示“对于牌组中的每张卡……”由于这个`for`循环的主体中只有一行代码，我省略了花括号。

第 60 行显示了当前卡片的值，一个制表符，然后调用`toString()`的结果。

代表`Card c`的方法。

好吧，让我们来解决这个`buildDeck()`函数。`buildDeck()`不需要任何参数，因为它只是从无中创建牌组。不过它确实返回一个值：一组卡片。

在第 29 到 31 行，我们创建了两个字符串数组。第一个（第 29 行）包含了花色的名称。第二个包含了卡片的名称。

你可能会注意到我有一张叫做`"ZERO"`的卡片，另一张叫做`"ONE"`的卡片。为什么？这是为了我可以把这个数组当作“查找表”来使用。我将写我的循环，使得我的卡片值从`2`到`14`，我希望单词`"two"`在这个数组中的索引是`2`。所以我需要把一些字符串放到槽位`0`和`1`中来占用空间。

最初我只是放了两个空字符串，如下所示：

```java

String[] names = { "", "", "two", "three", "four", "five", "six",
```

...但后来我担心如果我的代码有 bug，那么很难判断是没有打印任何内容还是`names[0]`（或`names[1]`）的值。因此，我为这两个索引放入了单词，但将它们全部大写，这样如果它们被打印出来，我就会注意到。

在第 33 行，我们创建了`i`，它将跟踪下一个需要放入卡片的索引。第 34 行定义了我们的 52 张卡片的数组（从 0 到 51 索引）。

第 36 行是另一个`foreach`循环。变量`s`将被设置为`"clubs"`，然后

“方块”，然后“红心”，最后“黑桃”。

第 38 行是另一个`for`循环，但这个循环是嵌套的。记住这意味着这个循环将进行

在外部循环改变`s`的值之前，`v`会从 2 到 14 变化。

第 40 行定义了一个名为`c`的`Card`。在第 41 行，我们将这张卡的花色字段设置为当前`s`中的任何值（一开始是`"clubs"`）。

根据循环的次数，`v`将是 2 到 14 之间的某个值，所以在第 42 行，我们使用`v`作为`names`数组的索引。也就是说，当`v`是 5 时，我们进入数组的第六个位置，那里会找到字符串`"five"`。我们将这个值的副本放入当前卡片的名称字段。

第 43 到 48 行将一个从 2 到 11 的整数存储到当前卡片的值字段中。我们需要`v`从 2 到 14 进行查找表，但现在已经完成了，我们需要确保没有卡片的值为 12 到 14。

第 14 张卡是 A，所以我们使用 11 作为卡的值。然后第 11、12 和 13 张卡是花牌，所以它们的卡值都是 10。其他卡的值都可以不变。

最后，我们将这张卡存储到`deck`的下一个可用槽中（用`i`索引），并使`i`增加 1。

当嵌套循环结束时，我们已经成功创建了标准牌组中的所有 52 张卡，并为它们赋予了与二十一点中使用方式相匹配的卡值。如果您想要确保，可以取消注释第 18 行上的`displayDeck()`调用。

`buildDeck()`的最后一步是`return`现在已经填满的`Cards`数组，这样它就可以存储到`main()`第 17 行的`deck`变量中。

### 学习演练

1.  添加一个名为`shuffleDeck()`的函数。它应该以一组卡片的数组作为参数，并返回一组卡片。一种洗牌的方法是从 0 到 51 选择两个随机数，并“交换”这些槽中的卡片。然后将该代码放入一个重复大约 1000 次的循环中。这有点难以做到正确。

