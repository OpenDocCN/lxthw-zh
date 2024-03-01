# 习题 32: 回圈和阵列

現在你應該有能力寫更有趣的程式出來了。如果你能夠一直跟得上，你應該已意識到你能將之前學到的將 `if` 語句 和 「布林表示式」這些東西結合起來，讓程式做出一些聰明的事了。

然而，我們的城市還需要能很快地完成重複的事情。這節習題中我們將使用 `for-loop` (for 迴圈) 來建立和印出各式的陣列。在做習題的過程中，你將會逐漸搞懂它們是怎麼回事。現在我不會告訴你，你需要自己找到答案。

在你開始使用 for 迴圈之前，你需要在某個位置存放迴圈的結果。最後的方法是使用陣列 `array`。一個陣列，就是一個按照順序存放東西的容器。陣列並不複雜，你只是要學習一點新的語法。首先我們來看看如何建立一個陣列：

```rb
      hairs = ['brown', 'blond', 'red']
eyes = ['brown', 'blue', 'green']
weights = [1, 2, 3, 4]

```

你要做的是以 `[` 左中括號開頭「打開」陣列，然後寫下你要放入陣列的東西、用逗號 `,` 隔開，就跟函式的參數一樣，最後你需要用 `]` 右中括號結束陣列的定義。然後 Ruby 接收這個陣列以及裡面所有的內容，將其賦予給一個變數。

> **Warning:** 對於不會寫程式的人來說這是一個困難點。習慣性思維告訴你的大腦大地是平的。記得上一個練習中的巢狀 if 語句吧，你可能覺得要理解它有些難度，因為生活中一般人不會去想這樣的問題，但這樣的問題在程式中幾乎到處都是。你會看到一個函式呼叫用另外一個包含 if 語句的函式，其中又有巢狀陣列的陣列。如果你看到這樣的東西一時無法弄懂，就用紙筆記下來，手動分割下去，直到弄懂為止。

現在我們將使用迴圈建立一些陣列，然後將它們印出來：

```rb
      the_count = [1, 2, 3, 4, 5]
fruits = ['apples', 'oranges', 'pears', 'apricots']
change = [1, 'pennies', 2, 'dimes', 3, 'quarters']

# this first kind of for-loop goes through an array
for number in the_count
  puts "This is count #{number}"
end

# same as above, but using a block instead
fruits.each do |fruit|
  puts "A fruit of type: #{fruit}"
end

# also we can go through mixed arrays too
for i in change
  puts "I got #{i}"
end

# we can also build arrays, first start with an empty one
elements = []

# then use a range object to do 0 to 5 counts
for i in (0..5)
  puts "Adding #{i} to the list."
  # push is a function that arrays understand
  elements.push(i)
end

# now we can puts them out too
for i in elements
  puts "Element was: #{i}"
end

```

## 你應該看到的結果

```rb
      $ ruby ex32.rb
This is count 1
This is count 2
This is count 3
This is count 4
This is count 5
A fruit of type: apples
A fruit of type: oranges
A fruit of type: pears
A fruit of type: apricots
I got 1
I got 'pennies'
I got 2
I got 'dimes'
I got 3
I got 'quarters'
Adding 0 to the list.
Adding 1 to the list.
Adding 2 to the list.
Adding 3 to the list.
Adding 4 to the list.
Adding 5 to the list.
Element was: 0
Element was: 1
Element was: 2
Element was: 3
Element was: 4
Element was: 5
$

```

## 加分習題

1.  注意一下 range `(0..5)`。查一下 `Range` class (類別) 並弄懂它。
2.  在第 24 行，你可以直接將 `elements` 賦值為 `(0..5)`，而不需使用 for 迴圈嗎？
3.  在 Ruby 文件中可以找到關於陣列的內容，仔細閱讀一下，除了 `push` 以外，陣列還支援那些操作？