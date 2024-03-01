你已經學會了 `if` 語句、函式、還有陣列。現在你要練習扭轉一下思維了。把下面的代碼寫下來，看你是否能弄懂它實現的是什麼功能。

```rb
      def prompt()
  print "> "
end

def gold_room()
  puts "This room is full of gold.  How much do you take?"

  prompt; next_move = gets.chomp
  if next_move.include? "0" or next_move.include? "1"
    how_much = next_move.to_i()
  else
    dead("Man, learn to type a number.")
  end

  if how_much < 50
    puts "Nice, you're not greedy, you win!"
    Process.exit(0)
  else
    dead("You greedy bastard!")
  end
end

def bear_room()
  puts "There is a bear here."
  puts "The bear has a bunch of honey."
  puts "The fat bear is in front of another door."
  puts "How are you going to move the bear?"
  bear_moved = false

  while true
    prompt; next_move = gets.chomp

    if next_move == "take honey"
      dead("The bear looks at you then slaps your face off.")
    elsif next_move == "taunt bear" and not bear_moved
      puts "The bear has moved from the door. You can go through it now."
      bear_moved = true
    elsif next_move == "taunt bear" and bear_moved
      dead("The bear gets pissed off and chews your leg off.")
    elsif next_move == "open door" and bear_moved
      gold_room()
    else
      puts "I got no idea what that means."
    end
  end
end

def cthulu_room()
  puts "Here you see the great evil Cthulu."
  puts "He, it, whatever stares at you and you go insane."
  puts "Do you flee for your life or eat your head?"

  prompt; next_move = gets.chomp

  if next_move.include? "flee"
    start()
  elsif next_move.include? "head"
    dead("Well that was tasty!")
  else
    cthulu_room()
  end
end

def dead(why)
  puts "#{why}  Good job!"
  Process.exit(0)
end

def start()
  puts "You are in a dark room."
  puts "There is a door to your right and left."
  puts "Which one do you take?"

  prompt; next_move = gets.chomp

  if next_move == "left"
    bear_room()
  elsif next_move == "right"
    cthulu_room()
  else
    dead("You stumble around the room until you starve.")
  end
end

start()

```

## 你應該看到的結果

你可以結果：

```rb
      $ ruby ex35.rb
You are in a dark room.
There is a door to your right and left.
Which one do you take?
> left
There is a bear here.
The bear has a bunch of honey.
The fat bear is in front of another door.
How are you going to move the bear?
> taunt bear
The bear has moved from the door. You can go through it now.
> open door
This room is full of gold.  How much do you take?
> asf
Man, learn to type a number. Good job!
$

```

## 加分習題

1.  把這個遊戲的地圖畫出來，把自己的路線也畫出來。
2.  改正你所有的錯誤，包括拼寫錯誤。
3.  為你不懂的函式寫註解。記得 **RDoc** 中的註釋嗎？
4.  為遊戲添加更多元素。通過怎樣的方式可以簡化並且擴充遊戲的功能呢？
5.  這個 gold_room 遊戲使用了奇怪的方式讓你鍵入一個數字。這種方式會導致什麼樣的 bug？你可以用比檢查 0、1 更好的方式判斷輸入是否是數字嗎？ `to_i()` 這個函式可以給你一些頭緒。