每一種程式語言都包含處理數字和進行數學計算的方法。不必擔心，程式設計師經常撒謊說他們是多們厲害的數學天才，其實他們根本不是。如果他們真是數學天才，他們早就去從事數學相關的行業了，而不是寫寫廣告程式和社交網路遊戲，從人們身上偷賺點小錢而已。

這章習題裡有很多的數學運算符號。我們來看一遍它們都叫什麼。你要一邊寫一邊念出它們的名稱來。直到你念煩了為止。名稱如下：

```rb
      + 加號
- 減號
/ 除號
* 乘號
% 百分比符號
< 小於符號
> 大於符號
<= 小於等於符號
>= 大於等於號

```

有沒有注意到以上只是些符號，沒有運算操作呢？寫完下面的練習程式碼後，再回到上面的列表，寫出每個符號的作用。例如 `+` 是用來做加法運算的。

```rb
      puts "I will now count my chickens:"

puts "Hens", 25 + 30 / 6
puts "Roosters", 100 - 25 * 3 % 4

puts "Now I will count the eggs:"

puts 3 + 2 + 1 - 5 + 4 % 2 - 1 / 4 + 6

puts "Is it true that 3 + 2 < 5 - 7?"

puts 3 + 2 < 5 - 7

puts "What is 3 + 2?", 3 + 2
puts "What is 5 - 7?", 5 - 7

puts "Oh, that's why it's false."

puts "How about some more."

puts "Is it greater?", 5 > -2
puts "Is it greater or equal?", 5 >= -2
puts "Is it less or equal?", 5 <= -2

```

## 你應該看到的結果

```rb
      $ ruby ex3.rb 
I will now count my chickens:
Hens 
30
Roosters 
97
Now I will count the eggs: 
7
Is it true that 3 + 2 < 5 - 7?
false
What is 3 + 2? 
5
What is 5 - 7? 
-2
Oh, that's why it's false. 
How about some more.
Is it greater? 
true
Is it greater or equal? 
true
Is it less or equal? 
false
$

```

## 加分習題

1.  使用 `#` 在程式碼每一行的前一行為自己寫一個註解，說明一下這一行的作用。
2.  記得最開始時的 的 IRB 吧？再次打開 IRB，然後使用剛才學到的運算符號，把 Ruby 當做計算機玩玩。
3.  自己找個想要計算的東西，寫一個 `.rb` 檔案把它計算出來。
4.  有沒有發現計算結果是「錯」的呢？計算結果只有整數，沒有小數部分。研究一下這是為什麼，搜尋一下「浮點數(floating point number)」是什麼東西。
5.  使用浮點數重寫一遍 `ex3.rb`，讓它的計算結果更準確(提示: 20.0 是一個浮點數)。