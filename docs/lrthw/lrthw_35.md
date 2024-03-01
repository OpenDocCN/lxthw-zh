接下來是一個更在你意料之外的概念：`while-loop`(while 迴圈)。`while` 迴圈會一直執行它下面的程式碼區段，直到它對應的布林表示式為 `false` 才會停下來。

等等，你還能跟的上這些術語吧？如果我們寫了這樣一個語句：`if items > 5` 或者是 `for fruit in fruits`，那就是在開始一個程式碼區段 (code block)，新的程式碼區段是需要被縮排的，最後再以 `end` 語句結尾。只有將程式碼用這樣的方式格式化，Ruby 才能知道你的目的。如果你不太明白這一點，就回去看看 「if 語句」、「函式」和「for 迴圈」章節，直到你明白為止。

接下來的店席將訓練你的大腦去閱讀這些結構化的與集，這和我們將布林表示式燒錄到你的大腦中的過程有點類似。

回到 `while` 迴圈，它所作的和 `if` 語句類似，也是去檢查一個布林表示式的真假，不一樣的是它下面的程式碼區段不是只被執行一次，而是執行完後再趟回到 `while` 所在的位置，如此重複進行，直到 while 表示式為 **false** 為止。

`while` 迴圈有一個問題：那就是有時它會永不結束。如果你的目的是循環到宇宙毀滅為止，那這樣也挺好的，不過其他的情況下你的迴總需要有一個結束點。

為了避免這樣的問題，你需要遵循下面的規定：

1.  盡量少用 `while` 迴圈，大部分時候 `for` 迴圈是更好的選擇。
2.  重複檢查你的 `while` 語句，確定你測試的布林表示式最終會變成 **false**。
3.  如果不確定，就在 `while` 迴圈的結尾印出你要測試的值。看看它的變化。

在這節練習中，你將通過上面的三樣事情學會 `while` 迴圈：

```rb
      i = 0
numbers = []

while i < 6
  puts "At the top i is #{i}"
  numbers.push(i)

  i = i + 1
  puts "Numbers now: #{numbers}"
  puts "At the bottom i is #{i}"
end

puts "The numbers: "

for num in numbers
  puts num
end

```

## 你應該看到的結果

```rb
      $ ruby ex33.rb
At the top i is 0
Numbers now:  [0]
At the bottom i is 1
At the top i is 1
Numbers now:  [0, 1]
At the bottom i is 2
At the top i is 2
Numbers now:  [0, 1, 2]
At the bottom i is 3
At the top i is 3
Numbers now:  [0, 1, 2, 3]
At the bottom i is 4
At the top i is 4
Numbers now:  [0, 1, 2, 3, 4]
At the bottom i is 5
At the top i is 5
Numbers now:  [0, 1, 2, 3, 4, 5]
At the bottom i is 6
The numbers: 
0
1
2
3
4
5

```

## 加分習題

1.  將這個 `while` 迴圈改成一個函式，將測試條件 `(i < 6)`中的 6 換成一個變數。
2.  使用這個函式重寫你的腳本，並使用不同的數字進行測試。
3.  為函式添加另一個參數，這個參數用來定義第 8 行的 `+1`，這樣你就可以讓它任意加值了。
4.  再使用該函式重寫一遍這個腳本。看看效果如何。
5.  接下來使用 `for` 迴圈和 range 把這個腳本再寫一遍。你還需要中間的加值操作嗎？如果你不去掉它，會有什麼樣的結果？

有可能你會碰到程序跑著停不下來了，這時你只要按著 CTRL 再敲 c (CTRL-c)，這樣程式就會中斷下來了。