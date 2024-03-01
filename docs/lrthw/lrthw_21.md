# 习题 19: 函式和变数

函式這個概念也許承載了太多的資訊量。不過別擔心，只要堅持做這些練習題，對照上個練習中的檢查清單檢查這次練習的關聯，你最終會明白這些內容的。

有一個你可能沒有注意到的細節，我們現在強調一下，函式裡面的變數和腳本裡面的變數之間是沒有連接的。下面的這個練習可以讓你對這一點有更多的思考：

```rb
      def cheese_and_crackers(cheese_count, boxes_of_crackers)
  puts "You have #{cheese_count} cheeses!"
  puts "You have #{boxes_of_crackers} boxes of crackers!"
  puts "Man that's enough for a party!"
  puts "Get a blanket."
  puts # a blank line
end

puts "We can just give the function numbers directly:"
cheese_and_crackers(20, 30)

puts "OR, we can use variables from our script:"
amount_of_cheese = 10
amount_of_crackers = 50
cheese_and_crackers(amount_of_cheese, amount_of_crackers)

puts "We can even do math inside too:"
cheese_and_crackers(10 + 20, 5 + 6)

puts "And we can combine the two, variables and math:"
cheese_and_crackers(amount_of_cheese + 100, amount_of_crackers + 1000)

```

通過這個練習，你看到我們給我們的函式 `cheese_and_crackers` 很多的參數，然後在函式裡把他們印出來。我們可以塞數字、塞變數進去函式，我們甚至可以將變數和數學運算結合在一起。

從一方面來說，函式的參數和我們生成變數時用的 `=` 賦值符號類似。事實上，如果一個物件你可以用 `=` 將其命名，你通常也可以將其作為參數傳給一個函式。

## 你應該看到的結果

你應該研究一下腳本的輸出，和你想像的結果對比一下看有什麼不同。

```rb
      $ ruby ex19.rb
We can just give the function numbers directly:
You have 20 cheeses!
You have 30 boxes of crackers!
Man that's enough for a party!
Get a blanket.

OR, we can use variables from our script:
You have 10 cheeses!
You have 50 boxes of crackers!
Man that's enough for a party!
Get a blanket.

We can even do math inside too:
You have 30 cheeses!
You have 11 boxes of crackers!
Man that's enough for a party!
Get a blanket.

And we can combine the two, variables and math:
You have 110 cheeses!
You have 1050 boxes of crackers!
Man that's enough for a party!
Get a blanket.
$

```

## 加分習題

1.  倒著將腳本讀完，在每一行上面添加一行註解，說明這行程式的作用。
2.  從最後一行開始，倒著閱讀每一行，讀出所有重要的符號來。
3.  自己邊寫出至少一個函式出來，然後用十種方法運行這個函式。