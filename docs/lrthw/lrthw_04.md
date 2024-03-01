程式裡的註釋是很重要的。它們可以用自然語言告訴你某段程式碼的功能是什麼。在你想要臨時移除一段程式碼時，你還可以用註釋的方式將這段程式碼臨時禁用。接下來的練習將讓你學會註釋：

```rb
      # A comment, this is so you can read your program later.
# Anything after the # is ignored by Ruby.

puts "I could have code like this." # and the comment after is ignored

# You can also use a comment to "disable" or comment out a piece of code:
# print "This won't run."

puts "This will run."

```

## 你應該看到的結果

```rb
      $ ruby ex2.rb 
I could have code like this.
This will run.
$

```

## 加分習題

1.  弄清楚 `#` 符號的作用。而且記住它的名稱。（中文為井號，英文為 octothorpe 或者 pound character)。
2.  打開你的 `ex2.rb` 檔案，從後往前逐行檢查。從最後一行開始，倒著逐個單詞單詞檢查回去。
3.  有發現更多錯誤嘛？有的話就改正過來。
4.  閱讀你寫的習題，把每個字符（charcter）都讀出來。有沒有發現更多的錯誤呢？有的話也一樣改正過來。