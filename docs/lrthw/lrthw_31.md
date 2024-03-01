# 习题 29: 如果（if）

這裡是你接下要寫的作業，這段介紹了 `if-statement` （if 語句）。把這段輸入進去，讓它能夠正確執行。然後我們看看你是否有收穫。

```rb
      people = 20
cats = 30
dogs = 15

if people < cats
  puts "Too many cats! The world is doomed!"
end

if people > cats
  puts "Not many cats! The world is saved!"
end

if people < dogs
  puts "The world is drooled on!"
end

if people > dogs
  puts "The world is dry!"
end

dogs += 5

if people >= dogs
  puts "People are greater than or equal to dogs."
end

if people <= dogs
  puts "People are less than or equal to dogs."
end

if people == dogs
  puts "People are dogs."
end

```

## 你應該看到的結果

```rb
      $ ruby ex29.rb 
Too many cats! The world is doomed!
The world is dry!
People are greater than or equal to dogs.
People are less than or equal to dogs.
People are dogs.
$

```

## 加分習題

猜猜「if 語句」是什麼，它有什麼用處。在做下一道習題前，試著用自己的話回答下面的問題:

1.  你認為 if 對於它下一行的程式碼做了什麼？
2.  把習題 29 中的其它布林表示式放到「if 語句」中會不會也可以運行呢？試一下。
3.  如果把變數 people、cats 和 dogs 的初始值改掉，會發生什麼事情？