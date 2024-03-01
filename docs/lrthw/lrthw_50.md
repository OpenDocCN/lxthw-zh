# 习题 48: 更进阶的使用者输入

你的遊戲可能一路跑得很爽，不過你處理使用者輸入的方式肯定讓你不勝其煩了。每一個房間都需要一套自己的語句，而且只有使用者完全輸入正確後才能執行。你需要一個設備，它可以允許使用者以各種方式輸入語彙。例如下面的幾種表述都應該被支援才對：

*   open door
*   open the door
*   go THROUGH the door
*   punch bear
*   Punch The Bear in the FACE

也就是說，如果使用者的輸入和常用英語很接近也應該是可以的，而你的遊戲要識別出它們的意思。為了達到這個目的，我們將寫一個模組專門做這件事情。這個模組裡邊會有若干個類，它們互相配合，接受使用者輸入，並且將使用者輸入轉換成你的遊戲可以識別的命令。

英語的簡單格式是這個樣子的：

*   單詞由空格隔開。
*   句子由單詞組成。
*   語法控制句子的含義。

所以最好的開始方式是先搞定如何得到使用者輸入的詞彙，並且判斷出它們是什麼。

## 我們的遊戲語彙

我在遊戲裡建立了下面這些語彙：

*   表示方向: north, south, east, west, down, up, left, right, back.
*   動詞: go, stop, kill, eat.
*   修飾詞: the, in, of, from, at, it
*   名詞: door, bear, princess, cabinet.
*   數字詞: 由 0-9 構成的數字。

說到名詞，我們會碰到一個小問題，那就是不一樣的房間會用到不一樣的一組名詞，不過讓我們先挑一小組出來寫程式，以後再做改進吧。

## 如何斷句

我們已經有了詞彙表，為了分析句子的意思，接下來我們需要找到一個斷句的方法。我們對於句子的定義是「空格隔開的單詞」，所以只要這樣就可以了：

```rb
      stuff = gets.chomp()
words = stuff.split()

```

目前做到這樣就可以了，不過這招在相當一段時間內都不會有問題。

## 語彙結構

一旦我們知道瞭如何將句子轉化成詞彙列表，剩下的就是逐一檢查這些詞彙，看它們是什麼類型。為了達到這個目的，我們將用到一個非常便利的 Ruby 資料結構「struct」。「struct」其實就是一個可以把一串的 attrbutes 綁在一起的方式，使用 accessor 函式，但不需要寫一個複雜的 class。它的建立方式就像這樣：

```rb
      Pair = Struct.new(:token, :word)
first_word = Pair.new("direction", "north")
second_word = Pair.new("verb", "go")
sentence = [first_word, second_word]

```

這建立了一對 (TOKEN, WORD) 可以讓你看到 word 和在裡面做事。

這只是一個例子，不過最後做出來的樣子也差不多。你接受使用者輸入，用 split 將其分隔成單詞列表，然後分析這些單詞，識別它們的類型，最後重新組成一個句子。

## 掃描輸入資料

現在你要寫的是詞彙掃描器。這個掃描器會將使用者的輸入字符串當做參數，然後返回由多個(TOKEN, WORD) struct 組成的列表，這個列表實現類似句子的功能。如果一個單詞不在預定的詞彙表中，那它返回時 WORD 應該還在，但 TOKEN 應該設置成一個專門的錯誤標記。這個錯誤標記將告訴使用者哪裡出錯了。

有趣的地方來了。我不會告訴你這些該怎樣做，但我會寫一個「單元測試(unit test)」，而你要把掃描器寫出來，並保證單元測試能夠正常通過。

## Exceptions And Numbers

有一件小事情我會先幫幫你，那就是數字轉換。為了做到這一點，我們會作一點弊，使用「異常(exceptions)」來做。「異常」指的是你運行某個函數時得到的錯誤。你的函數在碰到錯誤時，就會「提出(raise)」一個「異常」，然後你就要去處理(handle)這個異常。假如你在 IRB 裡寫了這些東西：

```rb
      ruby-1.9.2-p180 :001 > Integer("hell")
ArgumentError: invalid value for Integer(): "hell"
    from (irb):1:in `Integer'
    from (irb):1
    from /home/rob/.rvm/rubies/ruby-1.9.2-p180/bin/irb:16:in `<main>'

```

這個 `ArgumentError` 就是 `Integer()` 函式拋出的一個異常。因為你給`Integer()` 的參數不是一個數字。`Integer()`函數其實也可以傳回一個值來告訴你它碰到了錯誤，不過由於它只能傳回整數值，所以很難做到這一點。它不能返回-1，因為這也是一個數字。 `Integer()`沒有糾結在它「究竟應該返回什麼」上面，而是提出了一個叫做`TypeError`的異常，然後你只要處理這個異常就可以了。

處理異常的方法是使用 `begin` 和 `rescue` 這兩個關鍵字：

```rb
      def convert_number(s)
  begin
    Integer(s)
  rescue ArgumentError
    nil
  end
end

```

你把要試著運行的程式碼放到「begin」的區段裡，再將出錯後要運行的程式碼放到「except」區段裡。在這裡，我們要試著呼叫 `Integer()` 去處理某個可能是數字的東西，如果中間出了錯，我們就「rescue」這個錯誤，然後返回 「nil」。

在你寫的掃描器裡面，你應該使用這個函數來測試某個東西是不是數字。做完這個檢查，你就可以聲明這個單詞是一個錯誤單詞了。

## What You Should Test

這裡是你應該使用的測試檔案 `test/test_lexicon.rb`:

```rb
      require 'test/unit'
require_relative "../lib/lexicon"

class LexiconTests < Test::Unit::TestCase

  Pair = Lexicon::Pair
  @@lexicon = Lexicon.new()

  def test_directions()
    assert_equal([Pair.new(:direction, 'north')], @@lexicon.scan("north"))
    result = @@lexicon.scan("north south east")
    assert_equal(result, [Pair.new(:direction, 'north'),
                 Pair.new(:direction, 'south'),
                 Pair.new(:direction, 'east')])
  end

  def test_verbs()
    assert_equal(@@lexicon.scan("go"), [Pair.new(:verb, 'go')])
    result = @@lexicon.scan("go kill eat")
    assert_equal(result, [Pair.new(:verb, 'go'),
                 Pair.new(:verb, 'kill'),
                 Pair.new(:verb, 'eat')])
  end

  def test_stops()
    assert_equal(@@lexicon.scan("the"), [Pair.new(:stop, 'the')])
    result = @@lexicon.scan("the in of")
    assert_equal(result, [Pair.new(:stop, 'the'),
                 Pair.new(:stop, 'in'),
                 Pair.new(:stop, 'of')])
  end

  def test_nouns()
    assert_equal(@@lexicon.scan("bear"), [Pair.new(:noun, 'bear')])
    result = @@lexicon.scan("bear princess")
    assert_equal(result, [Pair.new(:noun, 'bear'),
                 Pair.new(:noun, 'princess')])
  end

  def test_numbers()
    assert_equal(@@lexicon.scan("1234"), [Pair.new(:number, 1234)])
    result = @@lexicon.scan("3 91234")
    assert_equal(result, [Pair.new(:number, 3),
                 Pair.new(:number, 91234)])
  end

  def test_errors()
    assert_equal(@@lexicon.scan("ASDFADFASDF"), [Pair.new(:error, 'ASDFADFASDF')])
    result = @@lexicon.scan("bear IAS princess")
    assert_equal(result, [Pair.new(:noun, 'bear'),
                 Pair.new(:error, 'IAS'),
                 Pair.new(:noun, 'princess')])
  end

end

```

記住你要使用你的專案骨架來建立新專案項目，將這個 Test Case 寫下來（不許複製貼上！），然後編寫你的掃描器，直至所有的測試都能通過。注意細節並確認結果一切工作良好。

## 設計提示

集中一次實現一個測試，盡量保持簡單，只要把你的 `lexicon.rb` 詞彙表中所有的單詞放那裡就可以了。不要修改輸入的單詞表，不過你需要建立自己的新列表，裡邊包含你的語彙元組。另外，記得使用 `include?` 函式來檢查這些語彙陣列，以確認某個單詞是否在你的語彙表中。

## 加分習題

1.  改進單元測試，讓它覆蓋到更多的語彙。
2.  向語彙列表添加更多的語彙，並且更新單元測試程式碼。
3.  讓你的掃描器能夠識別任意大小寫的詞彙。更新你的單元測試以確認其功能。
4.  找出另外一種轉換為數字的方法。
5.  我的解決方案用了 37 行程式碼，你的是更長還是更短呢？