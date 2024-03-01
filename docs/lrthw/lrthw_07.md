# 习题 5: 更多的变数和印出

我們現在要鍵入更多的變數並且將它們印出來，這次我們將使用一個叫「格式化字串(format string)」的東西，每一次你使用 `"` 將一些文字包起來，你就建立一個字串。字串是程式將資訊展示給人的方式。你可以印出他們，可以將它們寫入檔案，還可以將它們發給網站伺服器等等。

字串是很好用的東西，所以在這個練習中你將學會如何創造包含變數內容的字串，使用專門的格式和語法將變數的內容放到字串裡，相當於來告訴 Ruby: “Hey 這是一個格式化字串，把這些變數放到那幾個位置上”

如常，即使你還不懂這些內容，只要一字不差的鍵入就可以了。

```rb
      my_name = 'Zed A. Shaw'
my_age = 35 # not a lie
my_height = 74 # inches
my_weight = 180 # lbs
my_eyes = 'Blue'
my_teeth = 'White'
my_hair = 'Brown'

puts "Let's talk about %s." % my_name
puts "He's %d inches tall." % my_height
puts "He's %d pounds heavy." % my_weight
puts "Actually that's not too heavy."
puts "He's got %s eyes and %s hair." % [my_eyes, my_hair]
puts "His teeth are usually %s depending on the coffee." % my_teeth

# this line is tricky, try to get it exactly right
puts "If I add %d, %d, and %d I get %d." % [
    my_age, my_height, my_weight, my_age + my_height + my_weight]

```

## 你應該看到的結果

```rb
      $ ruby ex5.rb
Let's talk about Zed A. Shaw.
He's 74 inches tall.
He's 180 pounds heavy.
Actually that's not too heavy.
He's got Blue eyes and Brown hair.
His teeth are usually White depending on the coffee.
If I add 35, 74, and 180 I get 289.
$

```

## 加分習題

1.  修改所有的變數名稱，把它們前面的 `my_` 去掉，確認將每一個地方的都改掉，不只是你使用 `=` 賦值過的地方。
2.  試著使用更多的格式化字串。
3.  在網路上搜尋所有的 Ruby 格式化字串。
4.  試著使用變數將英吋和磅轉換成公分和公斤。不要直接鍵入答案，使用 Ruby 的數學計算來完成。