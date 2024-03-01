你已經學過使用 `=` 給變數命名，以及將變數定義為某個數字換字串。接下來我們將讓你見證更多奇蹟。我們要示範給你的是如何使用 `=` 來將變數設置為「一個函式的值」。有一件事你需要特別注意，但待會再說，先輸入下面的腳本吧：

```rb
      def add(a, b)
  puts "ADDING #{a} + #{b}"
  a + b
end

def subtract(a, b)
  puts "SUBTRACTING #{a} - #{b}"
  a - b
end

def multiply(a, b)
  puts "MULTIPLYING #{a} * #{b}"
  a * b
end

def divide(a, b)
  puts "DIVIDING #{a} / #{b}"
  a / b
end

puts "Let's do some math with just functions!"

age = add(30, 5)
height = subtract(78,4)
weight = multiply(90, 2)
iq = divide(100, 2)

puts "Age: #{age}, Height: #{height}, Weight: #{weight}, IQ: #{iq}"

# A puzzle for the extra credit, type it in anyway.
puts "Here is a puzzle."

what = add(age, subtract(height, multiply(weight, divide(iq, 2))))

puts "That becomes: #{what} Can you do it by hand?"

```

現在我們創造了我們自己的加減乘除數學函式：`add`、`subtract`、`multiply` 以及 `divide`。最重要的是函式的最後一行，例如 `add` 的最後一行是 `return a + b`，它實現的功能是這樣的：

1.  我們呼叫函式時使用了兩個參數：`a` 和 `b`。
2.  我們印出這個函式的功能，這裡就是計算加法（ADDING)。
3.  接下來我們告訴 Ruby 讓他做某個回傳的動作：我們將 `a+b` 的值傳回 (return)。或者你可以這麼說：「我將 a 和 b 加起來，再把結果傳回。」
4.  Ruby 將兩個數字相加，然後當函式結束時，它就可以將 a + b 的結果賦予給一個變數。

和本書裡的很多其他東西一樣，你要慢慢消化這些內容，一步一步執行下去，追蹤一下究竟發生了什麼。為了幫助你理解，本節的加分習題將讓你解決一個謎題，並且讓你學到點比較酷的東西。

## 你應該看到的結果

```rb
      $ ruby ex21.rb
Let's do some math with just functions!
ADDING 30 + 5
SUBTRACTING 78 - 4
MULTIPLYING 90 * 2
DIVIDING 100 / 2
Age: 35, Height: 74, Weight: 180, IQ: 50
Here is a puzzle.
DIVIDING 50 / 2
MULTIPLYING 180 * 25
SUBTRACTING 74 - 4500
ADDING 35 + -4426
That becomes:  -4391 Can you do it by hand?
$

```

## 加分習題

1.  如果你不是很確定 return 回來的值，試著自己寫幾個函式出來，讓它們傳回一些值。你可以將任何可以放在 `=` 右邊的東西作為一個函式的傳回值。

2.  這個腳本的結尾是一個謎題。我將一個函式的傳回值當作了另外一個函式的參數。我將它們鏈接到了一起，接跟寫數學等式一樣。這樣可能有些難讀，不過執行一下你就知道結果了。接下來，你需要試試看能不能用正常的方法實現和這個方程式一樣的功能。

3.  一旦你解決了這個謎題，試著修改一下函式里的某些部分，然後看會有什麼樣的結果。你可以有目的地修改它，讓它輸出另外一個值。

4.  最後，倒過來做一次。寫一個簡單的等式，使用一樣的函式來計算它。

這個習題可能會讓你有些頭大，不過還是慢慢來，把它當做一個遊戲，解決這樣的謎題正是寫程式的樂趣之一。後面你還會看到類似的小謎題。