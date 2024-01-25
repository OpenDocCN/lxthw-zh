## 练习 58：最终项目-文本冒险游戏

如果您已经完成了到目前为止的所有练习，那么您应该准备好进行这个最终项目了。它比您之前做过的任何练习都要长，但比最近几个练习并不难。

您的最终练习是基于文本的冒险游戏*引擎*。通过*引擎*，我的意思是代码对冒险本身一无所知；游戏的进行完全取决于文件中的内容。更改文件就会改变游戏的进行。

所以首先要下载游戏数据文件的副本，并将其保存到与您要放置代码的相同文件夹中。

+   [`learnjavathehardway.org/txt/text­adventure­rooms.txt`](http://learnjavathehardway.org/txt/text-adventure-rooms.txt)

```java

  1 import java.util.Scanner;
  2 
  3 class Room
  4 {
  5     int roomNumber;
  6     String roomName;
  7     String description;
  8     int numExits;
  9     String[] exits = new String[10];
 10     int[] destinations = new int[10];
 11 }
 12 
 13 public class TextAdventureFinal
 14 {
 15     public static void main( String[] args )
 16     {
 17         Scanner keyboard = new Scanner(System.in);
 18 
 19         // initialize rooms from file
 20         Room[] rooms = loadRoomsFromFile("text­adventure­rooms.txt");
 21 
 22         // showAllRooms(rooms); // for debugging
 23 
 24         // Okay, so let's play the game!
 25         int currentRoom = 0;
 26         String ans;
 27         while ( currentRoom >= 0 )
 28         {
 29             Room cur = rooms[currentRoom];
 30             System.out.print( cur.description );
 31             System.out.print("> ");
 32             ans = keyboard.nextLine();
 33 
 34             // See if what they typed matches any of our exit names
 35             boolean found = false;
 36             for ( int i=0; i<cur.numExits; i++ )
 37             {
 38                 if ( cur.exits[i].equals(ans) )
 39                 {
 40                     found = true;
 41                     // if so, change our next room to that exit's room number
 42                     currentRoom = cur.destinations[i];
 43                 }
 44             }
 45             if ( ! found )
 46                 System.out.println("Sorry, I don't understand.");
 47         }
 48 
 49     }
 50 
 51     public static Room[] loadRoomsFromFile( String filename )
 52     {
 53         Scanner file = null;
 54         try
 55         {
 56             file = new Scanner(new java.io.File(filename));
 57         }
 58         catch ( java.io.IOException e )
 59         {
 60             System.err.println("Sorry, I can't read from the file '" + 
filename + "'.");
 61             System.exit(1);
 62         }
 63 
 64         int numRooms = file.nextInt();
 65         Room[] rooms = new Room[numRooms];
 66 
 67         // initialize rooms from file
 68         int roomNum = 0;
 69         while ( file.hasNext() )
 70         {
 71             Room r = getRoom(file);
 72             if ( r.roomNumber != roomNum )
 73             {
 74                 System.err.println("Reading room # " + r.roomNumber + ", but 
" + roomNum + " was expected.");
 75                 System.exit(2);
 76             }
 77             rooms[roomNum] = r;
 78             roomNum++;
 79         }
 80         file.close();
 81 
 82         return rooms;
 83     }
 84 
 85     public static void showAllRooms( Room[] rooms )
 86     {
 87         for ( Room r : rooms )
 88         {
 89             String exitString = "";
 90             for ( int i=0; i<r.numExits; i++ )
 91                 exitString += "\t" + r.exits[i] + " (" + r.destinations[i] + 
")";
 92             System.out.println( r.roomNumber + ") " + r.roomName + "\n" + 
exitString );
 93         }
 94     }
 95 
 96     public static Room getRoom( Scanner f )
 97     {
 98         // any rooms left in the file?
 99         if ( ! f.hasNextInt() )
100             return null;
101 
102         Room r = new Room();
103         String line;
104 
105         // read in the room # for error­checking later
106         r.roomNumber = f.nextInt();
107         f.nextLine();   // skip "\n" after room #
108 
109         r.roomName = f.nextLine();
110 
111         // read in the room's description
112         r.description = "";
113         while ( true )
114         {
115             line = f.nextLine();
116             if ( line.equals("%%") )
117                 break;
118             r.description += line + "\n";
119         }
120 
121         // finally, we'll read in the exits
122         int i = 0;
123         while ( true )
124         {
125             line = f.nextLine();
126             if ( line.equals("%%") )
127                 break;
128             String[] parts = line.split(":");
129             r.exits[i] = parts[0];
130             r.destinations[i] = Integer.parseInt(parts[1]);
131             i++;
132         }
133         r.numExits = i;
134 
135         // should be done; return the Room
136         return r;
137     }
138 
139 }
```

### 你应该看到什么

```java
This is the parlor.
It's a beautiful room.
There looks to be a kitchen to the "north".
And there's a shadowy corridor to the "east".
> north
There is a long countertop with dirty dishes everywhere. Off to one side
there is, as you'd expect, a refrigerator. You may open the "refrigerator"
or "go back".
> go back
This is the parlor.
It's a beautiful room.
There looks to be a kitchen to the "north".
And there's a shadowy corridor to the "east".
> east
The corridor has led to a dark room. The moment you step inside, the door
slams shut behind you. There is no handle on the interior of the door.
There is no escaping. Type "quit" to die.
> quit
```


在我开始讨论代码之前，让我花点时间谈谈冒险游戏的“文件格式”。

游戏由几个“房间”组成。每个房间都有一个房间号和一个房间名称；这些只用于游戏引擎，玩家看不到。

每个房间还有一个描述和一个或多个“出口”，这是通往另一个房间的路径。

冒险游戏文件以一个数字开头：游戏中的位置（房间）的总数。之后是每个房间的记录。这是一个例子：

```java

1
KITCHEN
There is a long countertop with dirty dishes everywhere. Off to one side there is, as you'd expect, a refrigerator. You may open the "refrigerator" or "go back".
%%
fridge:3 refrigerator:3 go back:0 back:0
%%
```

这个记录的第一行是房间号，所以这是房间号 1。记录的第二行是房间名称，我们只用于调试。

从记录的第三行开始是房间的描述，一直到有一行只有`%%`的行为止。描述中允许有空行。

在第一个双百分号之后是一个出口列表。每一行都有出口的名称（玩家输入的内容）后跟一个冒号，再跟着出口通往的房间号。

例如，在这个房间，如果玩家输入`"fridge"`，游戏引擎将把他们从这个房间（房间＃1）移动到房间＃3。如果他们输入`"go back"`，他们将“旅行”到房间＃0。您可能会注意到，为了让玩家更容易决定输入什么，我在列表中有重复的出口。无论是`"fridge"`还是`"refrigerator"`都会把他们带到房间＃3。

出口列表以另一行只包含`%%`的行结束。这就是记录的结尾。

好的，现在让我们转向代码。第 3 到 11 行声明了一个房间的记录。您可以看到我们为冒险游戏文件中的每个字段都有字段。您可能没有猜到的唯一一件事是，出口字符串数组（出口）和目的地房间号数组（目的地）的任意容量为`10`，然后有一个 numExits 字段来跟踪这个房间实际上有多少出口。如果您认为一个房间需要超过 10 个出口，请随时将此容量增加。

进入`main()`，第 20 行声明了房间数组并从中初始化。

`loadRoomsFromFile()`函数，稍后我会解释。

第 22 行有一个注释掉的`showAllRooms()`函数调用，我用于调试。

在第 25 行，您将看到我们当前房间变量的定义，它保存了玩家所在房间的房间号。他们从房间`0`开始，这是文件中的第一个房间。在第 26 行是`String` ans 的声明，它将保存玩家输入的内容。

第 27 行是主游戏循环的开始。只要 currentRoom 变量为`0`或更多，它就会重复。因此，我们将使用它来停止游戏：当玩家死亡（或获胜）时，我们将 currentRoom 设置为`-1`。

数组 rooms 包含游戏中所有位置的列表。包含玩家的房间号的房间的变量 currentRoom 存储在变量中。因此，`rooms[currentRoom]`是整个房间的记录...嗯，当前房间。在第 29 行，我们将这个房间的副本存储到`Room`变量 cur 中。（我这样做只是因为我懒，想要输入像`cur.description`而不是`rooms[currentRoom].description`这样的东西。）

说到这一点，第 30 行打印出当前房间的描述，它存储在

描述字段。

在第 31 和 32 行，我们打印出一个小提示，并让玩家输入他们想去的地方的字符串。

第 36 到 44 行搜索这个房间的出口数组，看看它们是否与玩家输入的内容匹配。请记住，出口数组的容量为`10`，但实际上这个房间可能并没有那么多出口。因此，在`for`循环中，我们计数到 numExits 字段的值，而不是`10`。

如果我们找到与玩家命令匹配的出口，我们将标志设置为`true`（这样我们就知道如果他们最终输入了我们列表中没有的内容，我们应该抱怨）。然后，由于出口数组中的单词与目的地数组中的房间号相对应，我们从目的地数组的相应槽中取出房间号，并将其作为我们的新房间号。这样，当主游戏循环再次重复时，我们将自动前往新的房间。

在第 45 行，我们检查我们的标志。如果它仍然是`false`，这意味着用户输入了我们在出口列表中从未找到的东西。我们可以礼貌地抱怨。因为当前房间没有改变，所以在主游戏循环中再次循环将只是再次打印出他们已经在的房间的描述。

这就是主游戏循环的结束，也是`main()`的结束。剩下的就是从冒险游戏文件中实际填充房间数组。

第 51 行是`loadRoomsFromFile()`函数的开始，它以要打开的文件名作为参数，并返回一个`Room`数组。

（我决定在这个文件中不想有`throws Exception`，所以这里有一个 try-catch 块。它打开文件。

如果我们成功到达第 64 行，这意味着文件已成功打开。我们读取文件的第一行，告诉我们有多少个房间。然后第 65 行定义了一个具有适当容量的 Room 记录数组。

在第 68 行，我创建了一个名为 roomNum 的变量，它有双重作用。首先：它是房间数组中下一个可用槽的索引。但其次，它用于双重检查文件中的房间号和房间的槽号是否相同。如果不是，游戏数据文件中可能存在某种错误。如果我们在这里检测到这样的错误（在第 72 行），我们会抱怨并结束程序。（`System.exit()`结束程序，即使是在函数调用内部。）

第 69 行是“读取所有房间”的循环的开始。只要文件中还有未见过的内容，它就会继续进行。这里存在潜在的错误：如果数据文件顶部的房间数量是错误的，那么这个循环可能会在数组中走得太远并导致错误。（例如，如果文件的第一行说你只有 7 个房间，但实际上有 8 个房间记录，那么这个循环将重复太多次。）

在第 71 行，我们使用`getRoom()`函数读取单个房间记录，我稍后会解释。

第 72 到 76 行是我已经提到的房间号健全性检查，然后第 77 行只是将这个新房间存储到房间数组的下一个可用槽中。第 78 行增加了房间索引。

循环结束后，所有房间都已从文件中读取并存储在数组的各自位置。因此，在第 82 行，我们可以将房间数组返回到`main()`的第 20 行。

第 85 到 94 行是我用于调试的`showAllRooms()`函数。它只是在屏幕上显示数组中的所有房间，并且对于每个房间，它还显示所有的出口以及它们的目的地。

我们的最后一个函数是`getRoom()`，它期望传入一个 Scanner 对象作为参数，并返回一个单独的 Room 对象。

在第 99 和 100 行，如果数据文件格式不正确，会进行简单的健全性检查。如果下一个

如果文件中的东西不是整数，那么只需返回`null`（未初始化对象的值）。在这里放置一个`return`将立即从函数中返回，而不必运行剩下的代码。

在第 102 行定义了空房间对象。第 103 行创建了一个名为*line*的字符串，我用它来做一些不同的事情。

第 106 行从文件中读取房间号。房间号是房间记录的第一部分。这个函数的其余部分将只使用 Scanner 对象的`nextLine()`方法，而在`nextInt()`之后的`nextLine()`通常不起作用，因为它只读取刚刚读取的整数后面的行尾。

因此，第 107 行调用`nextLine()`方法，但不必在任何地方存储它的返回值，因为它不会读取任何值值得保存。

第 109 行从文件中读取房间名称。我们只在调试时使用这个。

在第 112 行，我们首先将这个房间的描述字段设置为空字符串。这样我们就可以在不出错的情况下添加内容。（就像我们在循环中将“总数”变量设置为`0`一样，然后再进行累加。）

好吧。我喜欢写无限循环。告我吧。第 113 行是一个无限循环的开始。这是因为我们不知道房间描述中会有多少行；它会一直持续，直到我们看到一行什么都没有的`%%`。还有其他方法可以做到这一点，但我喜欢“写一个无限循环，然后在找到你要找的东西时跳出它”的方法。就像我以前说过的，理智的人意见不一。

一旦我们进入“无限”循环，我们就会将描述的一行读入 line 变量中。然后，在第 116 行，我们检查刚刚读取的内容是否为`%%`。如果是的话，我们就不想将其添加到描述中，所以我们跳出循环。break 有点像 continue 的相反；continue 跳回到循环的条件，而 break 直接跳到末尾并停止循环。

如果我们仍然在第 118 行附近，这意味着我们读入了一行描述，而且它不是`%%`。所以我们使用+=将该行（和一个\n）添加到描述字段的末尾。然后循环重复。（无论如何。）

最终，我们希望碰到`%%`，循环就会停止。

第 122 行定义了 i，我用它来表示 exits 和 destinations 数组中我们要放入下一个值的槽的索引。然后从第 123 行开始又是一个无限循环。我使用了一个非常类似的方法来读取所有的出口。

第 125 行读取整行，这意味着该行包含类似于“'refrigerator:3'”的内容。（如果不是这样，而实际上是`%%`，则第 126 行和第 127 行停止循环。）

所以现在我们需要将这行分成两部分。幸运的是，String 类有一个名为 split()的内置方法。

line.split(":")在字符串 line 中搜索并在每次看到`:`（冒号）时将其分割开。然后它返回一个字符串数组。例如，如果 line 包含 thisXisXaXtest，那么 line.split("X")将返回一个包含{"this"，"is"，"a"，"test"}的数组。在我们的情况下，line 中只有一个冒号，所以它返回类似于{"refrigerator"，"3"}的内容。

因此，在第 128 行之后，parts[0]包含出口词（如“refrigerator”），parts[1]包含目的地房间号的字符串（如`"3"`）。这对我们来说不太适用，因为我们需要房间号是整数，而不是字符串。

对我们来说（再次），Java 的标准库来拯救我们。有一个内置函数可以将字符串转换为整数：Integer.parseInt()。我们在第 130 行使用了这个函数。

回想一下，i 是我们需要存储下一个值的出口数组中的槽的索引。因此，第 129 行将 parts[0]（出口的名称）存储到出口数组的适当槽中。第 130 行将 parts[1]（要移动到的房间号）从字符串转换为 int，并将其存储在目的地数组的相同槽中。然后第 131 行增加下一轮的出口索引。

最终我们会碰到`%%`，这个循环也会停止循环。然而，这里存在一个潜在的错误。出口数组只有十个槽。如果数据文件中有一个房间有超过十个出口，这个循环将继续超出数组的末端，并导致程序崩溃。所以不要这样做。

循环结束后，我们的索引 i 将包含我们读入的房间的真实数量。所以我们将其存储到第 133 行当前房间的 numExits 字段中。

然后就是这样了。房间中的所有字段都已经被赋值，我们返回这个 Room。

对象到`loadRoomsFromFile()`函数的第 71 行。

### 学习演练

1.  写你自己的文字冒险。如果你觉得它变得相当不错，就把它发给我！

1.  添加一个保存游戏的功能，这样玩家可以输入一些内容来停止游戏，游戏将把他们当前的房间号存储到一个文本文件中，然后在游戏重新开始时加载它。
