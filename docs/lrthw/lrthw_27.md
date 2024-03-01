# 习题 25: 更多更多的练习

我們將做一些關於函式和變數的練習，以確認你真正掌握了這些知識。這節習題對你來說可以說是一本道：寫程式，逐行研究，弄懂它。

不過這節習題還是有些不同，你不需要執行它，取而代之，你需要將它導入到 Ruby 通過自己執行函式的方式運行。

```rb
      module Ex25
  def self.break_words(stuff)
    # This function will break up words for us.
    words = stuff.split(' ')
    words
  end

  def self.sort_words(words)
    # Sorts the words.
    words.sort()
  end

  def self.print_first_word(words)
    # Prints the first word and shifts the others down by one.
    word = words.shift()
    puts word
  end

  def self.print_last_word(words)
    # Prints the last word after popping it off the end.
    word = words.pop()
    puts word
  end

  def self.sort_sentence(sentence)
    # Takes in a full sentence and returns the sorted words.
    words = break_words(sentence)
    sort_words(words)
  end

  def self.print_first_and_last(sentence)
    # Prints the first and last words of the sentence.
    words = break_words(sentence)
    print_first_word(words)
    print_last_word(words)
  end

  def self.print_first_and_last_sorted(sentence)
    # Sorts the words then prints the first and last one.
    words = sort_sentence(sentence)
    print_first_word(words)
    print_last_word(words)
  end
end

```

首先以正常的方式 `ruby ex25.rb` 運行，找出裡面的錯誤，並把它們都改正過來。然後你需要接著下面的答案章節完成這節習題。

## 你應該看到的結果

這節練習我們將在你之前用來做算術的 Ruby 編譯器(IRB)裡，用交互的方式和你的`.rb` 作交流。

這是我做出來的樣子：

```rb
      $ irb
irb(main):001:0> require './ex25'
=> true
irb(main):002:0> sentence = "All good things come to those who wait."
=> "All good things come to those who wait."
irb(main):003:0> words = Ex25.break_words(sentence)
=> ["All", "good", "things", "come", "to", "those", "who", "wait."]
irb(main):004:0> sorted_words = Ex25.sort_words(words)
=> ["All", "come", "good", "things", "those", "to", "wait.", "who"]
irb(main):005:0> Ex25.print_first_word(words)
All
=> nil
irb(main):006:0> Ex25.print_last_word(words)
wait.
=> nil
irb(main):007:0> Ex25.wrods
NoMethodError: undefined method `wrods' for Ex25:Module
        from (irb):6
irb(main):008:0> words
=> ["good", "things", "come", "to", "those", "who"]
irb(main):009:0> Ex25.print_first_word(sorted_words)
All
=> nil
irb(main):010:0> Ex25.print_last_word(sorted_words)
who
=> nil
irb(main):011:0> sorted_words
=> ["come", "good", "things", "those", "to", "wait."]
irb(main):012:0> Ex25.sort_sentence(sentence)
=> ["All", "come", "good", "things", "those", "to", "wait.", "who"]
irb(main):013:0> Ex25.print_first_and_last(sentence)
All
wait.
=> nil
irb(main):014:0> Ex25.print_first_and_last_sorted(sentence)
All
who
=> nil
irb(main):015:0> ^D
$

```

我們來逐行分析一下每一步實現的是什麼：

1.  在第 2 行你 require 了自己的 `./ex25.rb` Ruby 檔案，和你做過的其他 require 一樣＄。在 require 的時候你不需要加 `.rb` 後綴。這個過程裡，你將這個檔案當做了一個 `module` (模組)來使用，你在這個模組裡定義的函式也可以直接呼叫出來。
2.  第 4 行你創造了一個用來處理的 `sentence` (句子)。
3.  第 6 行你使用了 `Ex25` 模組呼叫了你的第一個函式 `Ex25.break_words`。其中的 `.` (dot, period) 符號可以告訴 Ruby：「Hi，我要執行 `Ex25` 裡的那個叫 `break_word` 的函式！」
4.  第 8 行我們只是輸入 `Ex25.sort_words` 來得到一個排序過的句子。
5.  10-15 行我們使用 `Ex25.print_first_word` 和 `Ex25.print_last_word` 將第一個和最後一個詞印出來。
6.  第 16 行比較有趣。我把 `words` 變數寫錯成了 `wrods`，所以 Ruby 在 17-18 行給了一個錯誤訊息。
7.  第 19-20 行我們印出了修改過後的詞彙列表。第一個和最後一個詞我們已經印過了，所以在這裡沒有再印出來。
8.  剩下的行你需要自己分析一下，就留作你的加分習題了。

## 加分習題

1.  研究答案中沒有分析過的行，找出它們的來龍去脈。確認自己明白了自己使用的是模組 Ex25 中定義的函式。
2.  我們將我們的函式放在一個 `module` 裡式因為他們擁有自己的 命名空間 (namespace)。這樣如果有其他人寫了一個函式也叫 `break_words`，這樣就不會發生碰創。無論如何，輸入 `Ex25.` 是一件很煩人的事。有一個比較方便的作法，你可以輸入 `include Ex25`，這相當於說：「我要將所有 Ex25 這個 mudle 裡的所有東西 include 到我現在的 module 裡。」
3.  試著在你正在使用 IRB 時，弄爛檔案會發生什麼事。你可能要執行 CTRL-D ( Windows 下是 CTRL-Z ) 才能把 IRB 關掉 reload 一次。