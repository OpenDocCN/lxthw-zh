# 习题 47: 自动化测试

為了確認遊戲的功能是否正常，你需要一遍一遍地在你的遊戲中輸入命令。這個過程是很枯燥無味的。如果能寫一小段程式碼用來測試你的程式碼豈不是更好？然後只要你對程序做了任何修改，或者添加了什麼新東西，你只要「跑一下你的測試」，而這些測試能確認程序依然能正確運行。這些自動測試不會抓到所有的 bug，但可以讓你無需重複輸入命令運行你的程式碼，從而為你節約很多時間。

從這一章開始，以後的練習將不會有「你應該看到的結果」這一節，取而代之的是一個「你應該測試的東西」一節。從現在開始，你需要為自己寫的所有程式碼寫自動化測試，而這將讓你成為一個更好的程序員。

我不會試圖解釋為什麼你需要寫自動化測試。我要告訴你的是，你想要成為一個程式設計師，而程序的作用是讓無聊冗繁的工作自動化，測試軟件毫無疑問是無聊冗繁的，所以你還是寫點程式碼讓它為你測試的更好。

這應該是你需要的所有的解釋了。因為你寫單元測試的原因是讓你的大腦更加強健。你讀了這本書，寫了很多程式碼讓它們實現一些事情。現在你將更進一步，寫出懂得你寫的其他程式碼的程式碼。這個寫程式碼測試你寫的其他程式碼的過程將強迫你清楚的理解你之前寫的程式碼。這會讓你更清晰地了解你寫的程式碼實現的功能及其原理，而且讓你對細節的注意更上一個台階。

## 撰寫 Test Case

我們將拿一段非常簡單的程式碼為例，寫一個簡單的測試，這個測試將建立在上節我們創建的項目骨架上面。

首先從你的專案骨架創建一個叫做 `ex47` 的專案。確認該改名稱的地方都有改過，尤其是 `tests/ex47_tests.rb` 這處不要寫錯。

接下來建立一個簡單的 `ex47/lib/game.rb` 檔案，裡邊放一些用來被測試的程式碼。我們現在放一個傻乎乎的小 class 進去，用來作為我們的測試對象：

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

```

一旦你有了這個檔案，修改你的 unit test 骨架變成這樣：

```rb
      require 'test/unit'
require_relative '../lib/ex47'

class MyUnitTests < Test::Unit::TestCase

  def test_room()
    gold = Room.new("GoldRoom",
                    """This room has gold in it you can grab. There's a
                door to the north.""")
    assert_equal(gold.name, "GoldRoom")
    assert_equal(gold.paths, {})
  end

  def test_room_paths()
    center = Room.new("Center", "Test room in the center.")
    north = Room.new("North", "Test room in the north.")
    south = Room.new("South", "Test room in the south.")

    center.add_paths({:north => north, :south => south})
    assert_equal(center.go(:north), north)
    assert_equal(center.go(:south), south)
  end

  def test_map()
    start = Room.new("Start", "You can go west and down a hole.")
    west = Room.new("Trees", "There are trees here, you can go east.")
    down = Room.new("Dungeon", "It's dark down here, you can go up.")

    start.add_paths({:west => west, :down => down})
    west.add_paths({:east => start})
    down.add_paths({:up => start})

    assert_equal(start.go(:west), west)
    assert_equal(start.go(:west).go(:east), start)
    assert_equal(start.go(:down).go(:up), start)
  end

end

```

這個文件 require 了你在 `lib/ex47.rb` 裡建立的 `Room`這個類，接下來我們要做的就是測試它。於是我們看到一系列的以 `test_` 開頭的測試函式，它們就是所謂的「Test Case」，每一個 Test Case 裡面都有一小段程式碼，它們會建立一個或者一些房間，然後去確認房間的功能和你期望的是否一樣。它測試了基本的房間功能，然後測試了路徑，最後測試了整個地圖。

這裡最重要的函數時 `assert_equal`，它保證了你設置的變數，以及你在`Room` 裡設置的路徑和你的期望相符。如果你得到錯誤的結果的話，Ruby 的 `Test::Unit` 模組將會印出一個錯誤信息，這樣你就可以找到出錯的地方並且修正過來。

## 測試指南

在寫測試程式碼時，你可以照著下面這些不是很嚴格的指南來做：

1.  測試腳本要放到 `tests/` 目錄下，並且命名為 `test_NAME.rb`。這樣做還有一個好處就是防止測試程式碼和別的程式碼互相混掉。
2.  為你的每一個模組寫一個測試。
3.  Test Cast 函式保持簡短，但如果看上去不怎麼整潔也沒關係，Test Cast 一般都有點亂。
4.  就算 Test Cast 有些亂，也要試著讓他們保持整潔，把裡邊重複的程式碼刪掉。建立一些輔助函數來避免重複的程式碼。當你下次在改完程式碼需要改測試的時候，你會感謝我這一條建議的。重複的程式碼會讓修改測試變得很難操作。
5.  最後一條是別太把測試當做一回事。有時候，更好的方法是把程式碼和測試全部刪掉，然後重新設計程式碼。

## 你應該看到的結果

```rb
      $ ruby test_ex47.rb 
Loaded suite test_ex47
Started
...
Finished in 0.000353 seconds.

3 tests, 7 assertions, 0 failures, 0 errors, 0 skips

Test run options: --seed 63537

```

That’s what you should see if everything is working right. Try causing an error to see what that looks like and then fix it.

## 加分習題

1.  仔細閱讀 `Test::Unit`相關的文件，再去了解一下其他的替代方案。
2.  了解一下 `Rspec`，看看它是否可以幹得更出色。
3.  改進你遊戲裡的 Room，然後用它重建你的遊戲。這次重寫，你需要一邊寫程式碼，一般把單元測試寫出來。