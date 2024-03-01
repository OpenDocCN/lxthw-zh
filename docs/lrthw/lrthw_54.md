這本書馬上就要結束了。本章的練習對你是一個真正的挑戰。當你完成以後，你就可以算是一個能力不錯的 Ruby 初學者了。為了進一步學習，你還需要多讀一些書，多寫一些程式，不過你已經具備進一步學習的技能了。接下來的學習就只是時間、動力、以及資源的問題了。

在本章習題中，我們不會去創建一個完整的遊戲，取而代之的是我們會為《習題 42》中的遊戲建立一個“引擎(engine)”，讓這個遊戲能夠在瀏覽器中運行起來。這會涉及到將《習題 42》中的遊戲「重構(refactor)」，將《習題 47》中的架構混合進來，添加自動測試程式碼，最後建立一個可以運行遊戲的 web 引擎。

這是一節很「龐大」的習題。我預測你要花一周到一個月才能完成它。最好的方法是一點一點來，每晚上完成一點，在進行下一步之前確認上一步有正確完成。

## 重構《習題 42》的遊戲

你已經在兩個練習中修改了 `gothonweb` 專案，這節習題中你會再修改一次。這種修改的技術叫做「重構(refactoring)」，或者用我喜歡的講法來說，叫「修修補補(fixing stuff)」。重構是一個程式術語，它指的是清理舊程式碼或者為舊程式碼添加新功能的過程。你其實已經做過這樣的事情了，只不過不知道這個術語而已。這是寫軟體過程的第二個自然屬性。

你在本節中要做的，是將《習題 47》中的可以測試的房間地圖，以及《習題 42》中的遊戲這兩樣東西歸併到一起，創建一個新的遊戲架構。遊戲的內容不會發生變化，只不過我們會通過“重構”讓它有一個更好的架構而已。

第一步是將 `ex47.rb` 的內容複製到 `gothonweb/lib/map.rb` 中，然後將 `ex47_tests.rb` 的內容複製到 `gothonweb/test/test_map.rb`中，然後再次運行測試，確認他們還能正常運作。

> **Note:** 從現在開始我不會再向你展示運行測試的輸出了，我就假設你回去運行這些測試，而且知道怎樣的輸出是正確的。

將《習題 47》的程式碼拷貝完畢後，你就該開始重構它，讓它包含《習題 42》中的地圖。我一開始會把基本架構為你準備好，然後你需要去完成`map.rb`和`map_tests.rb` 裡邊的內容。

首先要做的是使用 `Room` 類來構建基本的地圖架構：

```rb
      class Room

  attr_accessor :name, :description, :paths

  def initialize(name, description)
    @name = name
    @description = description
    @paths = {}
  end

  def go(direction)
    @paths[direction]
  end

  def add_paths(paths)
    @paths.update(paths)
  end

end

central_corridor = Room.new("Central Corridor",
%q{
The Gothons of Planet Percal #25 have invaded your ship and destroyed
your entire crew.  You are the last surviving member and your last
mission is to get the neutron destruct bomb from the Weapons Armory,
put it in the bridge, and blow the ship up after getting into an 
escape pod.

You're running down the central corridor to the Weapons Armory when
a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume
flowing around his hate filled body.  He's blocking the door to the
Armory and about to pull a weapon to blast you.
})

laser_weapon_armory = Room.new("Laser Weapon Armory",
%q{
Lucky for you they made you learn Gothon insults in the academy.
You tell the one Gothon joke you know:
Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr.
The Gothon stops, tries not to laugh, then busts out laughing and can't move.
While he's laughing you run up and shoot him square in the head
putting him down, then jump through the Weapon Armory door.

You do a dive roll into the Weapon Armory, crouch and scan the room
for more Gothons that might be hiding.  It's dead quiet, too quiet.
You stand up and run to the far side of the room and find the
neutron bomb in its container.  There's a keypad lock on the box
and you need the code to get the bomb out.  If you get the code
wrong 10 times then the lock closes forever and you can't
get the bomb.  The code is 3 digits.
})

the_bridge = Room.new("The Bridge",
%q{
The container clicks open and the seal breaks, letting gas out.
You grab the neutron bomb and run as fast as you can to the
bridge where you must place it in the right spot.

You burst onto the Bridge with the netron destruct bomb
under your arm and surprise 5 Gothons who are trying to
take control of the ship.  Each of them has an even uglier
clown costume than the last.  They haven't pulled their
weapons out yet, as they see the active bomb under your
arm and don't want to set it off.
})

escape_pod = Room.new("Escape Pod",
%q{
You point your blaster at the bomb under your arm
and the Gothons put their hands up and start to sweat.
You inch backward to the door, open it, and then carefully
place the bomb on the floor, pointing your blaster at it.
You then jump back through the door, punch the close button
and blast the lock so the Gothons can't get out.
Now that the bomb is placed you run to the escape pod to
get off this tin can.

You rush through the ship desperately trying to make it to
the escape pod before the whole ship explodes.  It seems like
hardly any Gothons are on the ship, so your run is clear of
interference.  You get to the chamber with the escape pods, and
now need to pick one to take.  Some of them could be damaged
but you don't have time to look.  There's 5 pods, which one
do you take?
})

the_end_winner = Room.new("The End",
%q{
You jump into pod 2 and hit the eject button.
The pod easily slides out into space heading to
the planet below.  As it flies to the planet, you look
back and see your ship implode then explode like a
bright star, taking out the Gothon ship at the same
time.  You won!
})

the_end_loser = Room.new("The End",
%q{
You jump into a random pod and hit the eject button.
The pod escapes out into the void of space, then
implodes as the hull ruptures, crushing your body
into jam jelly.
})

escape_pod.add_paths({
    '2' => the_end_winner,
    '*' => the_end_loser
})

generic_death = Room.new("death", "You died.")

the_bridge.add_paths({
    'throw the bomb' => generic_death,
    'slowly place the bomb' => escape_pod
})

laser_weapon_armory.add_paths({
    '0132' => the_bridge,
    '*' => generic_death
})

central_corridor.add_paths({
    'shoot!' => generic_death,
    'dodge!'=> generic_death,
    'tell a joke' => laser_weapon_armory
})

START = central_corridor

```

你會發現我們的 `Room` 類和地圖有一些問題：

1.  在進入一個房間以前會打出一段文字作為房間的描述，我們需要將這些描述和每個房間關聯起來，這樣房間的次序就不會被打亂了，這對我們的遊戲是一件好事。這些描述本來是在 `if-else` 結構中的，這是我們後面要修改的東西。

2.  原版遊戲中我們使用了專門的程式來生成一些內容，例如炸彈的激活鍵碼，艦艙的選擇等，這次我們做遊戲時就先使用預設值好了，不過後面的加分習題裡，我會要求你把這些功能再加到遊戲中。

3.  我為所有的遊戲中的失敗結尾寫了一個 `generic_death`，你需要去補全這個函式。你需要把原版遊戲中所有的失敗結尾都加進去，並確保程式碼能正確運行。

4.  我添加了一種新的轉換模式，以`"*"`為標記，用來在遊戲引擎中實現「catch-all」動作。

等你把上面的程式碼基本寫好以後，接下來就是引導你繼續寫下去的自動測試的內容 `test/test_map.rb` 了：

```rb
      require 'test/unit'
require_relative '../lib/map'

class MapTests < Test::Unit::TestCase

  def test_room()
    gold = Room.new("GoldRoom",
                %q{This room has gold in it you can grab. There's a
                door to the north.})
    assert_equal(gold.name, "GoldRoom")
    assert_equal(gold.paths, {})
  end

  def test_room_paths()
    center = Room.new("Center", "Test room in the center.")
    north = Room.new("North", "Test room in the north.")
    south = Room.new("South", "Test room in the south.")

    center.add_paths({'north' => north, 'south' => south})
    assert_equal(center.go('north'), north)
    assert_equal(center.go('south'), south)
  end

  def test_map()
    start = Room.new("Start", "You can go west and down a hole.")
    west = Room.new("Trees", "There are trees here, you can go east.")
    down = Room.new("Dungeon", "It's dark down here, you can go up.")

    start.add_paths({'west' => west, 'down' => down})
    west.add_paths({'east' => start})
    down.add_paths({'up' => start})

    assert_equal(start.go('west'), west)
    assert_equal(start.go('west').go('east'), start)
    assert_equal(start.go('down').go('up'), start)
  end

  def test_gothon_game_map()
    assert_equal(START.go('shoot!'), generic_death)
    assert_equal(START.go('dodge!'), generic_death)

    room = START.go('tell a joke')
    assert_equal(room, laser_weapon_armory)
  end

end

```

你在這部分練習中的任務是完成地圖，並且讓自動測試可以完整地檢查過整個地圖。這包括將所有的 `generic_death` 物件修正為遊戲中實際的失敗結尾。讓你的程式碼成功運行起來，並讓你的測試越全面越好。後面我們會對地圖做一些修改，到時候這些測試將保證修改後的程式碼還可以正常工作。

## 會話(session)和用戶跟踪

在你的 web 程式運行的某個位置，你需要追踪一些信息，並將這些信息和用戶的瀏覽器關聯起來。在 HTTP 協議的框架中，web 環境是「無狀態(stateless)」的，這意味著你的每一次請求和你其它的請求都是相互獨立的。如果你請求了頁面 A，輸入了一些資料，然後點了一個頁面 B 的鏈接，那你在頁面 A 輸入的數據就全部消失了。

解決這個問題的方法是為 web 程式建立一個很小的資料儲存功能，給每個瀏覽器賦予一個獨一無二的數字，用來跟踪瀏覽器所作的事情。這個功能通常適用資料庫或者是存儲在磁碟上的檔案來實現。在 Sinatra 這個框架中實現這樣的功能是很容易的，以下就是一個這樣的例子（使用 Rack middleware)：

```rb
      require 'rubygems'
require 'sinatra'

use Rack::Session::Pool

get '/count' do
  session[:count] ||= 0
  session[:count] +=1
  "Count: #{session[:count]}"
end

get '/reset' do
  session.clear
  "Count reset to 0."
end

```

## 建立引擎

你應該已經寫好了遊戲地圖和它的單元測試程式碼碼。現在我要求你製作一個簡單的遊戲引擎，用來讓遊戲中的各個房間運轉起來，從玩家收集輸入，並且記住玩家到了那一幕。我們將用到你剛學過的會話來製作一個簡單的引擎，讓它可以：

1.  為新使用者啟動新的遊戲。
2.  將房間展示給使用者。
3.  接受使用者的輸入。
4.  在遊戲中處理使用者的輸入。
5.  顯示遊戲的結果，繼續遊戲的下一幕，知道玩家角色死亡為止。

為了建立這個引擎，你需要將我們久經考驗的`lib/gothonsweb.rb` 搬過來，建立一個功能完備的、基於 session 的遊戲引擎。這裡的難點是我會先使用基本的 HTML 檔案創建一個非常簡單的版本，接下來將由你完成它，基本的引擎是這個樣子的：

```rb
      require_relative "gothonweb/version"
require_relative "map"
require "sinatra"
require "erb"

module Gothonweb

  use Rack::Session::Pool

  get '/' do
    # this is used to "setup" the session with starting values
    p START
    session[:room] = START
    redirect("/game")
  end

  get '/game' do
    if session[:room]
      erb :show_room, :locals => {:room => session[:room]}
    else
      # why is there here? do you need it?
      erb :you_died
    end
  end

  post '/game' do
    action = "#{params[:action] || nil}"
    # there is a bug here, can you fix it?
    if session[:room]
      session[:room] = session[:room].go(params[:action])
    end
    redirect("/game")
  end

end

```

下一步，你應該刪除 `lib/views/hello_form.erb` 和 `lib/views/index.erb` 然後創作兩個在上述 code 提到的 template，這裡是一個非常簡單的 `lib/views/show_room.erb`:

```rb
      <h1><%= room.name %></h1>

<pre>
<%= room.description %>
</pre>

<% if room.name == "death" %>
  <p>
  <a href="/">Play Again?</a>
  </p>
<% else %>
  <p>
  <form action="/game" method="POST">
    - <input type="text" name="action"> <input type="SUBMIT">
  </form>
  </p>
<% end %>

```

這就用來顯示遊戲中的房間的模板。接下來，你需要在使用者跑到地圖的邊界時，用一個模板告訴使用者他的角色的死亡信息，也就是`lib/views/you_died.erb` 這個模板：

```rb
      <h1>You Died!</h1>

<p>Looks like you bit the dust.</p>
<p><a href="/">Play Again</a></p>

```

準備好了這些文件，你現在可以做下面的事情了：

1.  讓測試代碼 `test/test_gothonsweb.rb` 再次運行起來，這樣你就可以去測試這個遊戲。由於 session 的存在，你可能頂多只能實現幾次點擊，不過你應該可以做出一些基本的測試來。
2.  執行 lib/gothonsweb.rb` 腳本，試玩一下你的遊戲。
3.  你需要和往常一樣刷新和修正你的遊戲，慢慢修改遊戲的 HTML 檔案和引擎，直到你實現遊戲需要的所有功能為止。

## 你的期末考試

你有沒有覺著我一下子給了你超多的資訊呢？那就對了，我想要你在學習技能的同時可以有一些可以用來鼓搗的東西。為了完成這節習題，我將給你最後一套需要你自己完成的練習。你將注意到，到目前為止你寫的遊戲並不是很好，這只是你的第一版程式碼而已。你現在的任務是讓遊戲更加完善，實現下面的這些功能：

1.  修正程式碼中所有我提到和沒提到的 bug，如果你發現了新的 bug，你可以告訴我。
2.  改進所有的自動測試，讓你可以測試更多的內容，直到你可以不用瀏覽器就能測到所有的內容為止。
3.  讓 HTML 頁面看上去更美觀一些。
4.  研究一下網頁登錄系統，為這個程式創建一個登錄界面，這樣人們就可以登錄這個遊戲，並且可以保存遊戲高分。
5.  完成遊戲地圖，盡可能地把遊戲做大，功能做全。
6.  給用戶一個「幫助系統」，讓他們可以查詢每個房間裡可以執行哪些命令。
7.  為你的遊戲添加新功能，想到什麼功能就添加什麼功能。
8.  創建多個地圖，讓用戶可以選擇他們想要玩的一張來進行遊戲。你的 `lib/gothonsweb.rb` 應該可以運行提供給它的任意的地圖，這樣你的引擎就可以支持多個不同的遊戲。
9.  最後，使用你在習題 48 和 49 中學到的東西來創建一個更好的輸入處理器。你手頭已經有了大部分必要的程式碼，你只需要改進語法，讓它和你的輸入表單以及遊戲引擎掛鉤即可。

祝你好運！