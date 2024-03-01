# 习题 42: 物以类聚

雖說將函式放到 Hash 裡是很有趣的一件事情，你應該也會想到「如果 Ruby 內建這件事情該多好」。事實上也的確有，那就是 `class` 這個關鍵字。你可以使用 `class` 創建更棒的 「函式 Hash」，比你在上節練習中做的強大多了。Class（類）有著各種各樣強​​大的功能和用法，但本書不會深入講這些內容，在這裡，你只要你學會把它們當作高級的「函式字典」使用就可以了。

用到「class」的程式語言被稱作「Object Oriented Programming（面向對象編程式語言」。這是一種傳統的寫程式的方式，你需要做出「東西」來，然後你「告訴」這些東西去完成它們的工作。類似的事情你其實已經做過不少了，只不過還沒有意識到而已。記得你做過的這個吧：

```rb
      stuff = ['Test', 'This', 'Out']
puts stuff.join(' ')

```

其實你這裡已經使用了 `class`。 stuff 這個變數其實是一個 Array Class。而 `stuff.join()` 呼叫了 `Array` 函式中的 `join`，然後傳遞了字串 `' '`（就是一個空格），這也是一個 class —— 它是一個 `String` class (字符串類)。到處都是 class！

其實你這裡已經使用了 `class`。`stuff`這個變量其實是一個 list `class`（列表類）。而’ ‘.join(stuff)裡調用函式 join 的字符串’ ‘（就是一個空格）也是一個`class` ——它是一個 string `class` (字符串類)。到處都是`class`！

還有一個概念是 object（物件），不過我們暫且不提。當你建立過幾個`class` 後就會學到了。怎樣建立`class`呢？和你建立 `ROOMS` Hash 的方法差不多，但其實更簡單：

```rb
      class TheThing
  attr_reader :number

  def initialize()
    @number = 0
  end

  def some_function()
    puts "I got called."
  end

  def add_me_up(more)
    @number += more
    return @number
  end
end

# two different things
a = TheThing.new
b = TheThing.new

a.some_function()
b.some_function()

puts a.add_me_up(20)
puts a.add_me_up(20)
puts b.add_me_up(30)
puts b.add_me_up(30)

puts a.number
puts b.number

```

看到了在 `@number` 前面的 `@` 吧？這是一個實例變數 (instance variable)。每個在 `TheThing` 中你建立的實例都會擁有 `@number` 中自己的值。我們不能透過直接打 `a.number` 直接拿到 number。除非我們特別使用 `attr_reader :number`，宣告讓外界能存取資料。

若要讓 `@number` write-only，我們可以使用 `attr_writer :number`。為了讓它可以既可讀又可寫，我們可以使用 `attr_accessor :number`。Ruby 使用了這些優良的物件導向原則來封裝資料。

下來，看到 `initialize` 函式了嗎？這就是你為建立 `class` 設置內部變數的方式。你可以用以 `@`符號開頭的方式去設定它們。另外看到我們使用了`add_me_up()` 為你建立 `number`加值。後面你可以看到我們怎樣可以使用這種方法為數字加值，然後印出來。

Class 是很強大的東西，你應該好好讀讀相關的東西。盡可能多找些東西讀並且多多實驗。你其實知道它們該怎麼用，只要試試就知道了。其實我馬上就要去練吉他了，所以我不會讓你寫練習了。你將使用 `class` 寫一個練習。

接下來我們將把習題 41 的內容重寫一遍，不過這回我們將使用 `class`：

```rb
      class Game

  def initialize(start)
    @quips = [
      "You died.  You kinda suck at this.",
      "Nice job, you died ...jackass.",
      "Such a luser.",
      "I have a small puppy that's better at this."
    ]
    @start = start
    puts "in init @start = " + @start.inspect
  end

  def prompt()
    print "> "
  end

  def play()
    puts "@start => " + @start.inspect
    next_room = @start

    while true
      puts "\n--------"
      room = method(next_room)
      next_room = room.call()
    end
  end

  def death()
    puts @quips[rand(@quips.length())]
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
end

a_game = Game.new(:central_corridor)
a_game.play()

```

## 你應該看到的結果

這個版本的遊戲和你的上一版效果應該是一樣的，其實有些代碼都幾乎一樣。比較一下兩版程式碼，弄懂其中不同的地方，重點在需要理解這些東西：

1.  怎樣建立一個 `class` Game 並且放函式到裡面去。
2.  `initialize` 是一個特殊的初始方法，怎樣預設重要的變數在裡面。
3.  你如何透過將在 `class` 下這個關鍵字再巢狀排列這些定義的方式為`class` 添加函式。
4.  你如何透過在名稱底下加進巢狀內容來添加函式的。
5.  `@` 的概念，還有它在 `initialize`、`play` 和 `death` 是怎樣被使用的。
6.  最後我們怎樣建立了一個 Game，然後透過 `play()`讓所有的東西運行起來。

加分習題 研究一下**dict**是什麼東西，應該怎樣使用。 再為遊戲添加一些房間，確認自己已經學會使用`class` 。 創建一個新版本，裡邊使用兩個`class`，其中一個是 Map，另一個是 Engine。提示:把 play 放到 Engine 裡面。

## 加分習題

1.  再為遊戲添加一些房間，確認自己已經學會使用 `class`。
2.  建一個新版本，裡邊使用兩個 `class`，其中一個是 `Map`，另一個是 `Engine`。提示:把 play 放到 `Engine` 裡面。