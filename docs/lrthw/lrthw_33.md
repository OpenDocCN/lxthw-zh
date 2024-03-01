# 习题 31: 做出决定

這本書的上半部分，你印出了一些東西，並且呼叫了函式，不過一切都是直線式進行的。你的腳本從最上面一行開始，一路運行到結束，但其中並沒有決定程式流向的分支點。現在你已經學會了 `if`、`else`和 `elsif`，你就可以開始建立包含條件判斷的腳本了。

上一個腳本中你寫了一系列的簡單提問測試。這節的腳本中，你将需要向使用者提問，依據使用者的答案來做出決定。把腳本寫下來，多多搗鼓一陣子，看看他的運作原理是什麼。

```rb
      def prompt
  print "> "
end

puts "You enter a dark room with two doors.  Do you go through door #1 or door #2?"

prompt; door = gets.chomp

if door == "1"
  puts "There's a giant bear here eating a cheese cake.  What do you do?"
  puts "1\. Take the cake."
  puts "2\. Scream at the bear."

  prompt; bear = gets.chomp

  if bear == "1"
    puts "The bear eats your face off.  Good job!"
  elsif bear == "2"
    puts "The bear eats your legs off.  Good job!"
  else
    puts "Well, doing #{bear} is probably better.  Bear runs away."
  end

elsif door == "2"
  puts "You stare into the endless abyss at Cthuhlu's retina."
  puts "1\. Blueberries."
  puts "2\. Yellow jacket clothespins."
  puts "3\. Understanding revolvers yelling melodies."

  prompt; insanity = gets.chomp

  if insanity == "1" or insanity == "2"
    puts "Your body survives powered by a mind of jello.  Good job!"
  else
    puts "The insanity rots your eyes into a pool of muck.  Good job!"
  end

else
  puts "You stumble around and fall on a knife and die.  Good job!"
end

```

這裡的重點是你可以在 `if` 語句中內部再放一個 `if` 語句。這是一個很強大的功能，可以用來建立「巢狀(nested)」的決定（decision)。

你需要理解 `if` 語句包含 `if` 語句的概念。做一下加分習題，這樣你會確信自己真正理解了它們。

## 你應該看到的結果

我在玩一個小冒險遊戲。我的水準不怎麼樣。

```rb
      $ ruby ex31.rb
You enter a dark room with two doors.  Do you go through door #1 or door #2?
> 1
There's a giant bear here eating a cheese cake.  What do you do?
1\. Take the cake.
2\. Scream at the bear.
> 2
The bear eats your legs off.  Good job!

$ ruby ex31.rb 
You enter a dark room with two doors.  Do you go through door #1 or door #2?
> 1
There's a giant bear here eating a cheese cake.  What do you do?
1\. Take the cake.
2\. Scream at the bear.
> 1
The bear eats your face off.  Good job!

$ ruby ex31.rb 
You enter a dark room with two doors.  Do you go through door #1 or door #2?
> 2
You stare into the endless abyss at Cthuhlu's retina.
1\. Blueberries.
2\. Yellow jacket clothespins.
3\. Understanding revolvers yelling melodies.
> 1
Your body survives powered by a mind of jello.  Good job!

$ ruby ex31.rb 
You enter a dark room with two doors.  Do you go through door #1 or door #2?
> 2
You stare into the endless abyss at Cthuhlu's retina.
1\. Blueberries.
2\. Yellow jacket clothespins.
3\. Understanding revolvers yelling melodies.
> 3
The insanity rots your eyes into a pool of muck.  Good job!

$ ruby ex31.rb
You enter a dark room with two doors.  Do you go through door #1 or door #2?
> stuff
You stumble around and fall on a knife and die.  Good job!

$ ruby ex31.rb 
You enter a dark room with two doors.  Do you go through door #1 or door #2?
> 1
There's a giant bear here eating a cheese cake.  What do you do?
1\. Take the cake.
2\. Scream at the bear.
> apples
Well, doing apples is probably better.  Bear runs away.

```

## 加分習題

為遊戲添加新的部分，改變玩家做決定的位置。盡自己能力擴充這個遊戲，不過別把遊戲弄得太詭異了。