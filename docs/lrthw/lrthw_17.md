# 习题 15: 读取档案

你已經學過了 `STDIN.gets` 和 `ARGV`，這些是你開始學習讀取檔案的必備基礎。你可能需要多多實驗才能明白它的運作原理，所以你要細心練習，並且仔細檢查結果。處理檔案需要非常仔細，如果不仔細的話，你可能會把有用的檔案弄壞或者清空。導致前功盡棄。

這節練習涉及到寫兩個檔案。一個正常的 `ex15.rb` 文件，另外一個是 `ex15_sample.txt`，第二個文件並不是腳本，而是供你的腳本讀取的文字檔案。以下是後者的內容：

```rb
      This is stuff I typed into a file.
It is really cool stuff.
Lots and lots of fun to have in here.

```

我們要做的是把該檔案用我們的腳本「打開(open)」，然後印出來。然而把檔名 `ex15_sample.txt`「寫死(Hard Coding」在程式碼不是一個好主意，這些資訊應該是使用者輸入的才對。如果我們碰到其他檔案要處理，寫死的檔名就會給你帶來麻煩了。解決方案是使用 `ARGV` 和 `STDIN.gets` 來從使用者端獲取資訊，從而知道哪些檔案該被處理。

```rb
      filename = ARGV.first

prompt = "> "
txt = File.open(filename)

puts "Here's your file: #{filename}"
puts txt.read()

puts "Type the filename again:"
print prompt
file_again = STDIN.gets.chomp()

txt_again = File.open(file_again)

puts txt_again.read()

```

這個腳本中有一些新奇的玩意，我們來快速地過一遍：

程式碼的 1-3 行使用 `ARGV` 來獲取檔名，這個你已經熟悉了。接下來第 4 行我們使用一個新的命令 `File.open`。現在請在命令列執行 `ri File.open` 來讀讀它的說明。注意到這多像你的腳本，它接收一個參數，並且傳回一個值，你可以將這個值賦予一個變數。這就是你打開檔案的過程。

第 6 行我們印出了一小行，但在第 7 行我們看到了新奇的東西。我們在 `txt` 上呼叫了一個函式。你從 `open` 獲得的東西是一個 `file` （檔案），檔案本身也支援一些命令。它接受命令的方式是使用句點 `.` (dot or period)，緊跟著你的命令，然後參數。就像 `File.open` 做的事一樣。差別是：當你說 `txt.read()` 時，你的意思其實是：「嘿 txt！執行你的 read 命令，無需任何參數！」

腳本剩下的部份基本差不多，不過我就把剩下的分析作為加分習題留給你自己了。

## 你應該看到的結果

我的腳本叫 “ex15_sample.txt”，以下是執行結果：

```rb
      $ ruby ex15.rb ex15_sample.txt 
Here's your file 'ex15_sample.txt':
This is stuff I typed into a file.
It is really cool stuff.
Lots and lots of fun to have in here.

I'll also ask you to type it again:
> ex15_sample.txt
This is stuff I typed into a file.
It is really cool stuff.
Lots and lots of fun to have in here.

$

```

## 加分習題

這節的難度跨越有點大，所以你要儘量做好這節加分習題，然後再繼續後面的章節。

1.  在每一行的上面用注釋說明這一行的用途。
2.  如果你不確定答案，就問別人，或者是上網搜尋。大部分時候，只要搜尋「ruby 你要搜尋的東西」，就能得到你要的答案。比如搜尋一下「ruby file.open」。
3.  我使用了「命令」這個詞，不過實際上他們的名字是「函式(function)」和「方法(method)」。上網搜尋一下這兩者的意義和區別。看不懂也沒關係，迷失在其他程式設計師的知識海洋裡是很正常的一件事。
4.  刪掉 9-15 行使用到 `STDIN.gets` 的部份，再執行一次腳本。
5.  只用 `STDIN.gets` 撰寫這個腳本，想想哪種得到檔名的方法更好，以及為什麼。
6.  執行 `ri File` 然後往下捲動直到看見 `read()` 命令（函式/方法）。看到很多其他的命令了吧。你可以玩其他試試。
7.  再次啟動 IRB，然後在裡面使用 `File.open` 打開一個文件，這種 open 和 read 的方法也值得一學。
8.  讓你的腳本針對 `txt` 和 `txt_again` 變數執行一下 `close()`，處理完檔案後你需要將其關閉，這是很重要的一點。