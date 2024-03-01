前一習題中你寫了一些「if 語句 (if-statements)」，並且試圖猜出它們是什麼，以及實現的是什麼功能。在你繼續學習之前，我給你解釋一下上一節的加分習題的答案。上一節的加分習題你做過了吧，有沒有？

1.  你認為 if 對於它下一行的代碼做了什麼？`if` 語句為程式碼創建了一個所謂的「分支(branch)」，就跟 RPG 遊戲中的情節分支一樣。if 語句告訴你的腳本：「如果這個布林表示式為真，就執行接下來的程式碼，否則就跳過這一段。」
2.  把習題 29 中的其它布林表示式放到 if 語句中會不會也可以執行呢？試一下。可以。而且不管多複雜都可以，雖然寫複雜的東西通常是一種不好的寫作風格。
3.  如果把變數 people、cats 和 dogs 的初始值改掉，會發生什麼事情？因為你比較的對象是數字，如果你把這些數字改掉的話，某些位置的 if 語句會被演繹為 True，而它下面的程式區段將被運行。你可以試著修改這些數字，然後在頭腦裡假想一下那一段程式碼會被運行。

把我的答案和你的答案比較一下，確認自己真正懂得程式碼「區段(block)」的含義。這點對於你下一節的習題習很重要，因為你將會寫很多的 if 語句。

把這一段寫下來，並讓它運行起來：

```rb
      people = 30
cars = 40
buses = 15

if cars > people
  puts "We should take the cars."
elsif cars < people
  puts "We should not take the cars."
else
  puts "We can't decide."
end

if buses > cars
  puts "That's too many buses."
elsif buses < cars
  puts "Maybe we could take the buses."
else
  puts "We still can't decide."
end

if people > buses
  puts "Alright, let's just take the buses."
else
  puts "Fine, let's stay home then."
end

```

## 你應該看到的結果

```rb
      $ ruby ex30.rb
We should take the cars.
Maybe we could take the buses.
Alright, let's just take the buses.
$

```

## 加分習題

1.  猜想一下 `elsif` 和 `else` 的功能。
2.  將 `cars`、`people`和`buses`的數量改掉，然後追溯每一個 if 語句。看看最後會印出什麼來。
3.  試著寫一些複雜的布林表示式，例如 `cars > people and buses < cars`。 在每一行的上面寫註解，說明這一行的功用。