# 习题 39: 阵列的操作

你已經學過了陣列。在你學習“`while` 迴圈的時候，你對陣列進行過「pushed」動作，而且將陣列的內容印了出來。另外你應該還在加分習題裡研究過 Ruby 文件，看了陣列支援的其他操作。這已經是一段時間以前了，所以如果你不記得了的話，就回到本書的前面再複習一遍吧。

找到了嗎？還記得嗎？很好。那時候你對一個陣列執行了 `push` 函式。不過，你也許還沒有真正明白發生的事情，所以我們再來看看我們可以對陣列進行什麼樣的操作。

當你看到像 `mystuff.append('hello')`這樣的程式時，你事實上已經在 Ruby 內部激發了一個連鎖反應。以下是它的運作原理：

1.  Ruby 看到你用到了 `mystuff`，於是就去找到這個變數。也許它需要倒著檢查看你有沒有在哪裡用 `=` 建立過這個變數，或者檢查它是不是一個函式參數，或者看它是不是一個全局變數。不管哪種方式，它得先找到 `mystuff` 這個變數才行。
2.  一旦它找到了 `mystuff`，就輪到處理句點 `.` (period)這個操作符號，而且開始查看 `mystuff` 內部的一些變數了。由於 `mystuff` 是一個陣列，Ruby 知道 `mystuff` 支援一些函式。
3.  接下來輪到了處理 `push`。Ruby 會將 「push」和 `mystuff` 支援的所有函式的名稱一一對比，如果確實其中有一個叫 `push` 的函式，那麼 Ruby 就會去使用這個函式。
4.  接下來 Ruby 看到了括號(parenthesis)並且意識到, 「噢，原來這應該是一個函式」，到了這裡，它就正常會呼叫這個函式了，不過這裡的函式還要多一個參數才行。

一下子要消化這麼多可能有點難度，不過我們將做幾個練習，讓你頭腦中有一個深刻的印象。下面的練習將字符串和列表混在一起，看看你能不能在裡邊找出點樂子來：

```rb
      ten_things = "Apples Oranges Crows Telephone Light Sugar"

puts "Wait there's not 10 things in that list, let's fix that."

stuff = ten_things.split(' ')
more_stuff = %w(Day Night Song Frisbee Corn Banana Girl Boy)

while stuff.length != 10
  next_one = more_stuff.pop()
  puts "Adding: #{next_one}"
  stuff.push(next_one)
  puts "There's #{stuff.length} items now."
end

puts "There we go: #{stuff}"

puts "Let's do some things with stuff."

puts stuff[1]
puts stuff[-1] # whoa! fancy
puts stuff.pop()
puts stuff.join(' ') # what? cool!
puts stuff.values_at(3,5).join('#') # super stellar!

```

## 你應該看到的結果

```rb
      $ ruby ex39.rb 
Wait there's not 10 things in that list, let's fix that.
Adding: Boy
There's 7 items now.
Adding: Girl
There's 8 items now.
Adding: Banana
There's 9 items now.
Adding: Corn
There's 10 items now.
There we go: ["Apples", "Oranges", "Crows", "Telephone", "Light", "Sugar", "Boy", "Girl", "Banana", "Corn"]
Let's do some things with stuff.
Oranges
Corn
Corn
Apples Oranges Crows Telephone Light Sugar Boy Girl Banana
Telephone#Sugar
$

```

## 加分習題

1.  上網閱讀一些關於「物件導向程式(Object Oriented Programming)」的資料。暈了吧？嗯，我以前也是。別擔心。你將從這本書學到足夠用的關於物件導向程式的基礎知識，而以後你還可以慢慢學到更多。
2.  `something.methods` 和 something 的 class 有什麼關係？
3.  如果你不知道我講的是些什麼東西，別擔心。程式設計師為了顯得自己聰明，於是就發明了 Opject Oriented Programming，簡稱為 OOP，然後他們就開始濫用這個東西了。如果你覺得這東西太難，你可以開始學一下「函式式程式(functional programming)」。