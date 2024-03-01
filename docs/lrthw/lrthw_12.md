# 习题 10: 那是什么？

在習題 9 中我丟給你了一些新東西。我讓你看到兩種讓字串擴展到多行的方法。第一種方法是在月份中間用 `\n` (back-slash n) 隔開。這兩個字串的作用是在該位置上放入一個「新行(new line)」字符。

使用反斜線 `\` (back-slash) 可以將難印出的字符放到字串裡。針對不同的符號有很多這樣的所謂「跳脫序列(escape sequences)」，但有一個特殊的跳脫序列，就是 `\` 雙反斜線( double back-slash)。這兩個字符組合會印出一個反斜線來。接下來我們做幾個練習，然後你就知道這些跳脫序列的意義了。

另外一種重要的跳脫序列是用來將單引號 `'` 和雙引號 `"` 跳脫。想像你有一個用雙引號括起來的字串，你想要在字串裡的內容裡再加入一組雙引號進去，比如你想說 `" I "understand" joke."` ，Ruby 就認為 `"understand"` 前後的兩個引號是字串的邊界，從而把字串弄錯。你需要一種方法告訴 Ruby 字串裡面的雙引號不是真正的雙引號。

要解決這個問題，你需要將雙引號和單引號跳脫，讓 Ruby 將引號也包含到字串裡面去。這裡有一個例子：

```rb
      "I am 6'2\" tall."  # escape double-quote inside string
'I am 6\'2" tall.'  # escape single-quote inside string

```

第二種方法是使用文件語法(document syntax)，也就是 `<<NAME` ，你可以在鍵入 `NAME` 前放入\ 任意多行的文字。接下來你可以看到如何使用。

```rb
      tabby_cat = "\tI'm tabbed in."
persian_cat = "I'm split\non a line."
backslash_cat = "I'm \\ a \\ cat."

fat_cat = <<MY_HEREDOC
I'll do a list:
\t* Cat food
\t* Fishies
\t* Catnip\n\t* Grass
MY_HEREDOC

puts tabby_cat
puts persian_cat
puts backslash_cat
puts fat_cat

```

## 你應該看到的結果

注意你打出來的 tab 字符，這節練習中的文字間隔符號對於答案的正確性是很重要的。

```rb
      $ ruby ex10.rb
    I'm tabbed in.
I'm split
on a line.
I'm \ a \ cat.
I'll do a list:
    * Cat food
    * Fishies
    * Catnip
    * Grass

$

```

## 加分習題

1.  上網搜尋一下還有哪些可用的跳脫字符。
2.  結合跳脫序列和格式化字串，創造一種複雜的格式。