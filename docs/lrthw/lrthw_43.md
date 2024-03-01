你在上一節中發現 Hash 的秘密功能了嗎？你可以解釋給自己嗎？讓我來給你解釋一下，順便和你自己的理解對比看有什麼不同。這裡是我們要討論的程式碼：

```rb
      cities[:find] = method(:find_city)
puts cities[:find].call(cities, state)

```

你要記住一個函式也可以作為一個變數，為了要將一個程式碼區段儲存在一個變數裡，我們創造了一個東西叫「proc」，proc 是 procedure 縮寫。在這段程式碼中，首先我們呼叫了 Ruby 內建的函式`method`，它會回傳一個 proc 版的 `find_city` 函式。然後我們將之除存在一個 Hash 裡：key 是 `:find`，value 是 `cities`。。這和我們將州和市關聯起來的程式碼做的事情一樣，只不過在這個情況裡是個 proc。

好了，所以一旦我們知道 `find_city` 是在 Hash 中 `:find` 的位置，這就意味著我們可以去呼叫它。第二行程式碼可以分解成如下步驟：

1.  Ruby 讀到了 `cities`，然後知道了它是一個 「Hash」。
2.  然後看到了`[:find]`，於是 Ruby 就從索引找到了 cities Hash 中對應的位置，並且獲取了該位置的內容。
3.  `[:find]` 這個位置的內容是我們的函式 `find_city`，所以 Ruby 就知道了這裡表示一個函式，於是當它碰到`.call`就開始了 proc 呼叫。
4.  `cities`、`state` 這兩個參數將被傳遞到函式 `find_city` 中，然後這個函式就被運行了。
5.  `find_city` 接著從 `cities` 中尋找 `states`，並且回傳它找到的內容，如果什麼都沒找到，就返回一個信息說它什麼都沒找到。
6.  Ruby 接受 `find_city` 傳回的資訊，最後將該資訊賦值給一開始的 `city_found` 這個變數。

我再教你一個小技巧。如果你倒著閱讀的話，程式碼可能會變得更容易理解。讓我們來試一下，一樣是那行：

1.  `state` 和 `city` 是…
2.  最為參數傳遞給…
3.  一個 proc 位於…
4.  `:find` 然後尋找，目的地為…
5.  `cities` 這個 Hash…
6.  最後印到螢幕上

還有一種方法讀它，這回是「由裡向外」。

1.  找到表示式的中心位置，此次為`[:find]`。
2.  逆時針追溯，首先看到的是一個叫 `cities`的 Hash，這樣就知道了 `cities` 中的 `:find` 元素。
3.  上一步得到一個函式。繼續逆時針尋找，看到的是參數。
4.  參數傳遞給函式後，函式會傳回一個值。然後再逆時針尋找。
5.  最後，我們到了`city_found` =的賦值位置，並且得到了最終結果。

數十年的程式經驗下來，我在讀程式碼的過程中已經用不到上面的三種方法了。我只要瞄一眼就能知道它的意思。甚至給我一整頁的程式碼，我也可以一眼瞄出裡邊的 bug 和錯誤。這樣的技能是花了超乎常人的時間和精力才鍛煉得來的。在磨練的過程中，我學會了下面三種讀程式碼的方法：

1.  從前向後。
2.  從後向前。
3.  逆時針方向。

現在我們來寫這次的練習，寫完後再過一遍，這節習題其實挺有趣的。

程式碼不少，不過還是從頭寫完吧。確認它能運行，然後玩一下看看。

```rb
      def prompt()
  print "> "
end

def death()
  quips = ["You died.  You kinda suck at this.",
    "Nice job, you died ...jackass.",
    "Such a luser.",
    "I have a small puppy that's better at this."]
  puts quips[rand(quips.length())]
  Process.exit(1)
end

def central_corridor()
  puts "The Gothons of Planet Percal #25 have invaded your ship and destroyed"
  puts "your entire crew.  You are the last surviving member and your last"
  puts "mission is to get the neutron destruct bomb from the Weapons Armory,"
  puts "put it in the bridge, and blow the ship up after getting into an "
  puts "escape pod."
  puts "\n"
  puts "You're running down the central corridor to the Weapons Armory when"
  puts "a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume"
  puts "flowing around his hate filled body.  He's blocking the door to the"
  puts "Armory and about to pull a weapon to blast you."

  prompt()
  action = gets.chomp()

  if action == "shoot!"
    puts "Quick on the draw you yank out your blaster and fire it at the Gothon."
    puts "His clown costume is flowing and moving around his body, which throws"
    puts "off your aim.  Your laser hits his costume but misses him entirely.  This"
    puts "completely ruins his brand new costume his mother bought him, which"
    puts "makes him fly into an insane rage and blast you repeatedly in the face until"
    puts "you are dead.  Then he eats you."
    return :death

  elsif action == "dodge!"
    puts "Like a world class boxer you dodge, weave, slip and slide right"
    puts "as the Gothon's blaster cranks a laser past your head."
    puts "In the middle of your artful dodge your foot slips and you"
    puts "bang your head on the metal wall and pass out."
    puts "You wake up shortly after only to die as the Gothon stomps on"
    puts "your head and eats you."
    return :death

  elsif action == "tell a joke"
    puts "Lucky for you they made you learn Gothon insults in the academy."
    puts "You tell the one Gothon joke you know:"
    puts "Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr."
    puts "The Gothon stops, tries not to laugh, then busts out laughing and can't move."
    puts "While he's laughing you run up and shoot him square in the head"
    puts "putting him down, then jump through the Weapon Armory door."
    return :laser_weapon_armory

  else
    puts "DOES NOT COMPUTE!"
    return :central_corridor
  end
end

def laser_weapon_armory()
  puts "You do a dive roll into the Weapon Armory, crouch and scan the room"
  puts "for more Gothons that might be hiding.  It's dead quiet, too quiet."
  puts "You stand up and run to the far side of the room and find the"
  puts "neutron bomb in its container.  There's a keypad lock on the box"
  puts "and you need the code to get the bomb out.  If you get the code"
  puts "wrong 10 times then the lock closes forever and you can't"
  puts "get the bomb.  The code is 3 digits."
  code = "%s%s%s" % [rand(9)+1, rand(9)+1, rand(9)+1]
  print "[keypad]> "
  guess = gets.chomp()
  guesses = 0

  while guess != code and guesses < 10
    puts "BZZZZEDDD!"
    guesses += 1
    print "[keypad]> "
    guess = gets.chomp()
  end

  if guess == code
    puts "The container clicks open and the seal breaks, letting gas out."
    puts "You grab the neutron bomb and run as fast as you can to the"
    puts "bridge where you must place it in the right spot."
    return :the_bridge
  else
    puts "The lock buzzes one last time and then you hear a sickening"
    puts "melting sound as the mechanism is fused together."
    puts "You decide to sit there, and finally the Gothons blow up the"
    puts "ship from their ship and you die."
    return :death
  end
end

def the_bridge()
  puts "You burst onto the Bridge with the netron destruct bomb"
  puts "under your arm and surprise 5 Gothons who are trying to"
  puts "take control of the ship.  Each of them has an even uglier"
  puts "clown costume than the last.  They haven't pulled their"
  puts "weapons out yet, as they see the active bomb under your"
  puts "arm and don't want to set it off."

  prompt()
  action = gets.chomp()

  if action == "throw the bomb"
    puts "In a panic you throw the bomb at the group of Gothons"
    puts "and make a leap for the door.  Right as you drop it a"
    puts "Gothon shoots you right in the back killing you."
    puts "As you die you see another Gothon frantically try to disarm"
    puts "the bomb. You die knowing they will probably blow up when"
    puts "it goes off."
    return :death

  elsif action == "slowly place the bomb"
    puts "You point your blaster at the bomb under your arm"
    puts "and the Gothons put their hands up and start to sweat."
    puts "You inch backward to the door, open it, and then carefully"
    puts "place the bomb on the floor, pointing your blaster at it."
    puts "You then jump back through the door, punch the close button"
    puts "and blast the lock so the Gothons can't get out."
    puts "Now that the bomb is placed you run to the escape pod to"
    puts "get off this tin can."
    return :escape_pod
  else
    puts "DOES NOT COMPUTE!"
    return :the_bridge
  end
end

def escape_pod()
  puts "You rush through the ship desperately trying to make it to"
  puts "the escape pod before the whole ship explodes.  It seems like"
  puts "hardly any Gothons are on the ship, so your run is clear of"
  puts "interference.  You get to the chamber with the escape pods, and"
  puts "now need to pick one to take.  Some of them could be damaged"
  puts "but you don't have time to look.  There's 5 pods, which one"
  puts "do you take?"

  good_pod = rand(5)+1
  print "[pod #]>"
  guess = gets.chomp()

  if guess.to_i != good_pod
    puts "You jump into pod %s and hit the eject button." % guess
    puts "The pod escapes out into the void of space, then"
    puts "implodes as the hull ruptures, crushing your body"
    puts "into jam jelly."
    return :death
  else
    puts "You jump into pod %s and hit the eject button." % guess
    puts "The pod easily slides out into space heading to"
    puts "the planet below.  As it flies to the planet, you look"
    puts "back and see your ship implode then explode like a"
    puts "bright star, taking out the Gothon ship at the same"
    puts "time.  You won!"
    Process.exit(0)
  end
end

ROOMS = {
  :death => method(:death),
  :central_corridor => method(:central_corridor),
  :laser_weapon_armory => method(:laser_weapon_armory),
  :the_bridge => method(:the_bridge),
  :escape_pod => method(:escape_pod)
}

def runner(map, start)
  next_one = start

  while true
    room = map[next_one]
    puts "\n--------"
    next_one = room.call()
  end
end

runner(ROOMS, :central_corridor)

```

## 你應該看到的結果

```rb
      $ ruby ex41.rb

--------
The Gothons of Planet Percal #25 have invaded your ship and destroyed
your entire crew.  You are the last surviving member and your last
mission is to get the neutron destruct bomb from the Weapons Armory,
put it in the bridge, and blow the ship up after getting into an 
escape pod.

You're running down the central corridor to the Weapons Armory when
a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume
flowing around his hate filled body.  He's blocking the door to the
Armory and about to pull a weapon to blast you.
> dodge!
Like a world class boxer you dodge, weave, slip and slide right
as the Gothon's blaster cranks a laser past your head.
In the middle of your artful dodge your foot slips and you
bang your head on the metal wall and pass out.
You wake up shortly after only to die as the Gothon stomps on
your head and eats you.

--------
Such a luser.

$ ruby ex41.rb 

--------
The Gothons of Planet Percal #25 have invaded your ship and destroyed
your entire crew.  You are the last surviving member and your last
mission is to get the neutron destruct bomb from the Weapons Armory,
put it in the bridge, and blow the ship up after getting into an 
escape pod.

You're running down the central corridor to the Weapons Armory when
a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume
flowing around his hate filled body.  He's blocking the door to the
Armory and about to pull a weapon to blast you.
> tell a joke
Lucky for you they made you learn Gothon insults in the academy.
You tell the one Gothon joke you know:
Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr.
The Gothon stops, tries not to laugh, then busts out laughing and can't move.
While he's laughing you run up and shoot him square in the head
putting him down, then jump through the Weapon Armory door.

--------
You do a dive roll into the Weapon Armory, crouch and scan the room
for more Gothons that might be hiding.  It's dead quiet, too quiet.
You stand up and run to the far side of the room and find the
neutron bomb in its container.  There's a keypad lock on the box
and you need the code to get the bomb out.  If you get the code
wrong 10 times then the lock closes forever and you can't
get the bomb.  The code is 3 digits.
[keypad]> 123 
BZZZZEDDD!
[keypad]> 234
BZZZZEDDD!
[keypad]> 345
BZZZZEDDD!
[keypad]> 456
BZZZZEDDD!
[keypad]> 567
BZZZZEDDD!
[keypad]> 678
BZZZZEDDD!
[keypad]> 789
BZZZZEDDD!
[keypad]> 384
BZZZZEDDD!
[keypad]> 764
BZZZZEDDD!
[keypad]> 354
BZZZZEDDD!
[keypad]> 263
The lock buzzes one last time and then you hear a sickening
melting sound as the mechanism is fused together.
You decide to sit there, and finally the Gothons blow up the
ship from their ship and you die.

--------
You died.  You kinda suck at this.

```

## 加分習題

1.  解釋一下返回至下一個房間的運作原理。 2.建立更多的房間，讓遊戲規模變大。
2.  除了讓每個函式印出自己以外，試試學習一下「文件註解(doc comments)」。
3.  看看你能不能將房間描述寫成文件註解，然後修改運行它的程式碼，讓它把文檔註解打印出來。
4.  一旦你用了文件註解作為房間描述，你還需要讓這個函式打出用戶提示嗎？試著讓運行函數的代碼打出用戶提示來，然後將用戶輸入傳遞到各個函式。你的函式應該只是一些 `if` 語句組合，將結果印出來，並且返回下一個房間。
5.  這其實是一個小版本的「有限狀態機(finite state machine)」，找資料閱讀了解一下，雖然你可能看不懂，但還是找來看看吧