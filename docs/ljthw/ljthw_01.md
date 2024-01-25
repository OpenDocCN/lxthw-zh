## 练习 0：设置

这个练习没有代码，但**不要跳过它**。这将帮助您安装一个体面的文本编辑器并安装 Java 开发工具包（JDK）。如果您不做这两件事，您将无法完成本书中的任何其他练习。您应该尽可能准确地遵循这些说明。

#### 警告！

这个练习需要您在终端窗口（也称为“shell”，“控制台”或“命令提示符”）中执行操作。如果您没有终端窗口的经验，那么您可能需要先学习一下。

[Zed Shaw 的出色的命令行快速入门课程在](http://cli.learncodethehardway.org/book/) http://cli.learncodethehardway.org/book/，将教您如何在 Windows 上使用 PowerShell 或在 OS X 上使用终端或在 Linux 上使用“bash”。

### Mac OS X

要完成这个练习，完成以下任务：

1.  [转到](http://www.barebones.com/products/textwrangler/) http://www.barebones.com/products/textwrangler/，使用您的网络浏览器。下载 TextWrangler 文本编辑器并安装它。

1.  将 TextWrangler 放在您的 Dock 中，以便您可以轻松访问它。

1.  找到一个名为“终端”的程序。（如果需要，进行搜索。）

1.  也将终端放在您的 Dock 中。

1.  启动终端。

1.  在终端程序中，键入`javac ­version`并按`RETURN`。您应该会看到一个类似`javac 1.7.0_04`的响应。如果`javac`后面的数字不完全相同，只要是 1.6 或更高都可以。但如果出现错误消息，您可能需要安装 JDK。

1.  完成后，您应该回到提示符。

1.  学习如何从终端创建一个文件夹（创建一个目录）。创建一个目录，以便您可以将本书中的所有代码放入其中。

1.  学习如何从终端切换到这个新目录。切换到它。

1.  使用文本编辑器（TextWrangler）创建一个名为`test.txt`的文件，并将其保存到您刚刚创建的目录中。

1.  只使用键盘切换窗口返回到终端。

1.  回到终端，查看是否可以列出目录的内容以查看您新创建的文件。

### OS X：您应该看到的内容

我目前无法访问 Mac，所以这是 Zed 在他的计算机终端上按照上述步骤操作的情况。您的计算机可能会有所不同，因此看看您能否找出他所做的事情和您应该做的事情之间的所有差异。

```java

Last login: Fri Jul 19 00:56:54 on ttys001
```

+   ```java
    $ javac ­version javac 1.6.22
    ```

+   ```java
    $ mkdir javacode
    ```

+   ```java
    $ cd javacode javacode $ ls
    ```

```java
# ... Use TextWrangler here to edit test.txt....
javacode $ ls test.txt javacode $
```

### Windows

1.  [转到](http://notepad/) http://notepad­plus­plus.org/，使用您的网络浏览器，获取 Notepad++文本编辑器，并安装它。您不需要是管理员才能这样做。

1.  确保您可以轻松访问 Notepad++，将其放在桌面和/或快速启动栏上。这两个选项都可以在安装过程中选择。

1.  从开始菜单运行 PowerShell。搜索它，然后按 Enter 运行。

1.  在桌面和/或快速启动栏上创建 PowerShell 的快捷方式，以方便使用。

1.  [转到](http://www.oracle.com/technetwork/java/javase/downloads/) http://www.oracle.com/technetwork/java/javase/downloads/，使用您的网络浏览器。

    1.  点击左上角的“Java”按钮，下载 Java 平台（JDK）7u25\. 点击后会跳转到另一个页面。

    1.  在此页面上，您需要接受许可协议，然后选择列表底部的“Windows x86”版本。下载文件。

    1.  下载完成后，运行`jdk­7u25­windows­i586.exe`进行安装。点击“下一步>”后，您将首次看到一个屏幕，上面写着`安装到：C:\Program` `Files (x86)\Java\jdk1.7.0_25\`或类似的内容。记下这个位置，您很快就会需要它。

1.  安装 JDK 后，您需要找出安装位置的确切名称。在`C:`驱动器内查看`Program Files`文件夹或`C:\Program` `Files (x86)`文件夹（如果有的话）。您要找的是一个名为`Java`的文件夹。里面有一个名为`jdk1.7.0_25`的文件夹，里面有一个名为`bin`的文件夹。文件夹名称必须包含`jdk1.7`；`jre7`不一样。确保有一个`bin`文件夹。

1.  进入此文件夹后，您可以在文件夹位置左键单击，它将变成类似`C:\Program Files (x86)\Java\jdk1.7.0_25\bin`的内容。您可以记下这个内容，或者将其高亮显示并右键单击复制到剪贴板。

1.  安装 JDK 并知道其位置后，打开您的终端窗口（PowerShell）。在 PowerShell 中，键入以下内容：

[Environment]::SetEnvironmentVariable("Path",

"$env:Path;C:\Program Files (x86)\Java\jdk1.7.0_25\bin", "User")

将所有内容放在一行上。

如果您将文件夹位置复制到剪贴板，那么您可以键入`$env:Path;`之前的所有内容，然后在 PowerShell 窗口中右键单击，它应该会为您粘贴文件夹名称。然后您只需完成这一行，输入`", "User")`并按`ENTER`。如果出现错误，您输入了错误的内容。您可以按上箭头将其取回，使用左右箭头找到并纠正错误，然后再次按`ENTER`。

1.  一旦`setEnvironmentVariable`命令完成而没有给出错误，通过在提示符处键入`exit`关闭 PowerShell 窗口。如果你不关闭它，你刚刚做的更改就不会生效。

1.  再次启动 PowerShell。

1.  在提示符处键入`javac ­version`。你应该会看到一个类似`javac 1.7.0_25`的响应。恭喜！如果你成功了，这本书的其余部分应该相对容易。

1.  之后，你应该回到一个闪烁的 PowerShell 提示符。

1.  学习如何从终端窗口（PowerShell）创建一个文件夹（创建一个目录）。创建一个目录，这样你就可以把这本书中的所有代码放进去。

1.  学习如何从提示符中切换到这个新目录。切换到它。

1.  使用你的文本编辑器（Notepad++）创建一个名为`test.txt`的文件，并将其保存到目录中

    你刚刚创建的。

1.  只使用键盘切换窗口回到终端。

1.  回到终端，看看你是否可以列出目录的内容，以查看你新创建的文件。

```java

Windows PowerShell
Copyright (C) 2009 Microsoft Corporation. All rights reserved.

PS C:\Users\Graham_Mitchell> javac ­version javac 1.7.0_25
PS C:\Users\Graham_Mitchell> mkdir javacode
```

```java
Directory: C:\Users\Graham_Mitchell\javacode
```

```java
PS C:\Users\Graham_Mitchell> cd javacode PS C:\Users\Graham_Mitchell\javacode> ls PS C:\Users\Graham_Mitchell\javacode>
... Here you would use Notepad++ to make test.txt in javacode ... PS C:\Users\Graham_Mitchell\javacode> ls
```

```java
Directory: C:\Users\Graham_Mitchell\javacode
```

### Windows：你应该看到的内容

```java

Mode
LastWriteTime
Length Name
­­­­
­­­­­­­­­­­­­
­­­­­­ ­­­­
d­­­­
7/19/2013 7:39 PM
javacode

Mode
LastWriteTime
Length Name
­­­­
­­­­­­­­­­­­­
­­­­­­ ­­­­
­a­­­
7/19/2013
7:45 PM
4 test.txt

PS C:\Users\Graham_Mitchell\javacode>
```

你可能会看到不同的提示和其他细微的差异，但你不应该会得到任何错误，这是一般的想法。

### Linux

Linux 有很多不同的版本，所以我将为最新版本的 Ubuntu 提供说明。如果你使用其他系统，你可能知道如何修改这些说明以适应你的设置。

1.  使用你的 Linux 软件包管理器安装`gedit`文本编辑器（可能只是称为“文本编辑器”）。

1.  确保你可以通过将其放在启动器中轻松地找到 gedit。

1.  运行 gedit，这样我们就可以更改一些默认设置，使其更适合程序员：

    1.  打开*首选项*并选择*编辑器*选项卡。

    1.  将选项卡宽度更改为 4。

    1.  在“自动缩进”旁边打上勾

    1.  打开*查看*选项卡，打开“显示行号”。

1.  找到你的终端程序。它可能被称为 GNOME 终端、Konsole 或 xterm。

1.  也把你的终端放到启动器中。

1.  使用你的 Linux 软件包管理器安装 Java JDK。我使用`openjdk­7­jdk`，但如果你更喜欢 Oracle 的，也可以。

1.  如果你还没有启动终端，启动你的终端。

1.  在提示符处键入`javac ­version`。你应该会看到一个类似`javac 1.7.0_25`的响应。如果没有，确保 JDK 已安装，并且包含可执行文件`javac`的`bin`目录在你的 PATH 中。

1.  学习如何从终端创建一个文件夹（创建一个目录）。创建一个目录，这样你就可以把这本书中的所有代码放进去。

1.  学习如何从提示符中切换到这个新目录。切换到它。

1.  使用你的文本编辑器（gedit）创建一个名为`test.txt`的文件，并将其保存到你刚刚创建的目录中。

1.  只使用键盘切换窗口回到终端。如果你不知道如何做，查一下。

1.  回到终端，看看你是否可以列出目录的内容，以查看你新创建的文件。

### Linux：你应该看到的内容

```java

mitchell@graham­desktop:~$ javac ­version javac 1.7.0_25
mitchell@graham­desktop:~$ mkdir javacode mitchell@graham­desktop:~$ cd javacode/ mitchell@graham­desktop:~/javacode$ ls mitchell@graham­desktop:~/javacode$
... Here you would use Notepad++ to make test.txt in javacode ... mitchell@graham­desktop:~/javacode$ ls
test.txt mitchell@graham­desktop:~/javacode$
```

你可能会看到不同的提示和其他细微的差异，但你不应该会得到任何错误，这是一般的想法。

### 初学者警告

你已经完成了第一个练习。这个练习可能对你来说很难，这取决于你对计算机的熟悉程度。如果很困难，你没有完成，回去花时间阅读和学习，然后再试一次。编程需要仔细阅读和注意细节。

如果一个程序员告诉你使用 vim 或 emacs 或 Eclipse，只需说“不”。这些编辑器是给你成为更好的程序员时使用的。你现在所需要的只是一个能让你把文本放入文件中的编辑器。我们将使用 gedit、TextWrangler 或 Notepad++（从现在开始称为“文本编辑器”或“一个文本编辑器”），因为它简单，并且在所有计算机上都是一样的。专业程序员使用这些文本编辑器，所以对于你来说已经足够了。

程序员最终会告诉你使用 Mac OS X 或 Linux。如果程序员喜欢字体和排版，他会告诉你买一个 Mac OS X 电脑。如果他喜欢控制并且留着大胡子，他们会告诉你安装 Linux。再次强调，使用你现在拥有的能工作的计算机。你只需要一个编辑器、一个终端和 Java。

最后，这个设置的目的是让你在做练习时可以非常可靠地做三件事：

+   使用你的文本编辑器（Linux 上的 gedit，OSX 上的 TextWrangler，或 Windows 上的 Notepad++）编写练习。

+   运行你写的练习。

+   当它们坏了就修好它们。

+   重复。

其他任何事情都只会让你困惑，所以坚持计划。

### 常见问题

#### 我必须使用这个糟糕的文本编辑器吗？我想用 Eclipse！

不要使用 Eclipse。虽然它是一个不错的程序，但不适合初学者。它对初学者有两个坏处：

1.  它让你做一些你现在不需要担心的事情。

1.  它为你做了一些你需要先学会如何做的事情。

所以按照我的指示使用一个体面的文本编辑器和一个终端窗口。一旦你学会了编码，你可以使用其他工具，但现在不行。

#### 我可以在我的平板电脑上完成这本书吗？还是我的 Chromebook？

很不幸。你不能在这两台机器上安装 Java 开发工具包（JDK）。你必须有某种传统的计算机。

