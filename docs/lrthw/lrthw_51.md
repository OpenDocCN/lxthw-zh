從我們這個小遊戲的詞彙掃描器中，我們應該可以得到類似下面的列表（你的看起來可能格式會不太一樣）：

```rb
      ruby-1.9.2-p180 :003 > print Lexicon.scan("go north")
[#<struct Lexicon::Pair token=:verb, word="go">,
    #<struct Lexicon::Pair token=:direction, word="north">] => nil 
ruby-1.9.2-p180 :004 > print Lexicon.scan("kill the princess")
[#<struct Lexicon::Pair token=:verb, word="kill">,
    #<struct Lexicon::Pair token=:stop, word="the">,
    #<struct Lexicon::Pair token=:noun, word="princess">] => nil
ruby-1.9.2-p180 :005 > print Lexicon.scan("eat the bear")
[#<struct Lexicon::Pair token=:verb, word="eat">,
    #<struct Lexicon::Pair token=:stop, word="the">,
    #<struct Lexicon::Pair token=:noun, word="bear">] => nil 
ruby-1.9.2-p180 :006 > print Lexicon.scan("open the door and smack the bear in the nose")
[#<struct Lexicon::Pair token=:error, word="open">,
    #<struct Lexicon::Pair token=:stop, word="the">, 
    #<struct Lexicon::Pair token=:noun, word="door">, 
    #<struct Lexicon::Pair token=:error, word="and">, 
    #<struct Lexicon::Pair token=:error, word="smack">, 
    #<struct Lexicon::Pair token=:stop, word="the">, 
    #<struct Lexicon::Pair token=:noun, word="bear">, 
    #<struct Lexicon::Pair token=:stop, word="in">, 
    #<struct Lexicon::Pair token=:stop, word="the">, 
    #<struct Lexicon::Pair token=:error, word="nose">] => nil 
ruby-1.9.2-p180 :007 >

```

現在讓我們把它轉化成遊戲可以使用的東西，也就是一個 Sentence 類。

如果你還記得學校學過的東西的話，一個句子是由這樣的結構組成的：

> 主語(Subject) + 謂語(動詞 Verb) + 賓語(Object)

很顯然實際的句子可能會比這複雜，而你可能已經在英語的語法課上面被折騰得夠嗆了。我們的目的，是將上面的 struct 列表轉換為一個 Sentence 物件，而這個對象又包含主謂賓各個成員。

## 匹配(Match) And 窺視(Peek)

為了達到這個效果，你需要四樣工具：

1.  一個循環存取 struct 列表的方法，這挺簡單的。
2.  「匹配」我們的主謂賓設置中不同種類 struct 的方法。
3.  一個「窺視」潛在 struct 的方法，以便做決定時用到。
4.  「跳過(skip)」我們不在乎的內容的方法，例如形容詞、冠詞等沒有用處的詞彙。
5.  我們使用 peek 函式查看 struct 列表中的下一個成員，做匹配以後再對它做下一步動作。讓我們先看看這個 peek 函式：

```rb
      def peek(word_list)
  begin
    word_list.first.token
  rescue
    nil
  end
end

```

很簡單。再看看 match 函式：

```rb
      def match(word_list, expecting)
  begin
    word = word_list.shift
    if word.token == expecting
      word
    else
      nil
    end
  rescue
    nil
  end
end

```

還是很簡單，最後我們看看 skip 函式:

```rb
      def skip(word_list, word_type)
  while peek(word_list) == word_type
    match(word_list, word_type)
  end
end

```

以你現在的水準，你應該可以看出它們的功能來。確認自己真的弄懂了它們。

## 句子的語法

有了工具，我們現在可以從 struct 列表來構建句子(Sentence)對象了。我們的處理流程如下：

1.  使用 `peek` 識別下一個單詞。
2.  如果這個單詞和我們的語法匹配，我們就調用一個函式來處理這部分語法。假設函式的名字叫 `parse_subject` 好了。
3.  如果語法不匹配，我們就 `raise` 一個錯誤，接下來你會學到這方面的內容。
4.  全部分析完以後，我們應該能得到一個 Sentence 物件，然後可以將其應用在我們的遊戲中。

演示這個過程最簡單的方法是把程式碼展示給你讓你閱讀，不過這節習題有個不一樣的要求，前面是我給你測試程式碼，你照著寫出程式碼來，而這次是我給你的程序，而你要為它寫出測試程式碼來。

以下就是我寫的用來解析簡單句子的程式碼，它使用了 `ex48` 這個 Lexicon class。

```rb
      class ParserError < Exception

end

class Sentence

  def initialize(subject, verb, object)
    # remember we take Pair.new(:noun, "princess") structs and convert them
    @subject = subject.word
    @verb = verb.word
    @object = object.word
  end

end

def peek(word_list)
  begin
    word_list.first.token
  rescue
    nil
  end
end

def match(word_list, expecting)
  begin
    word = word_list.shift
    if word.token == expecting
      word
    else
      nil
    end
  rescue
    nil
  end
end

def skip(word_list, token)
  while peek(word_list) == token
    match(word_list, token)
  end
end

def parse_verb(word_list)
  skip(word_list, :stop)

  if peek(word_list) == :verb
    return match(word_list, :verb)
  else
    raise ParserError.new("Expected a verb next.")
  end
end

def parse_object(word_list)
  skip(word_list, :stop)
  next_word = peek(word_list)

  if next_word == :noun
    return match(word_list, :noun)
  end
  if next_word == :direction
    return match(word_list, :direction)
  else
    raise ParserError.new("Expected a noun or direction next.")
  end
end

def parse_subject(word_list, subj)
  verb = parse_verb(word_list)
  obj = parse_object(word_list)

  return Sentence.new(subj, verb, obj)
end

def parse_sentence(word_list)
  skip(word_list, :stop)

  start = peek(word_list)

  if start == :noun
    subj = match(word_list, :noun)
    return parse_subject(word_list, subj)
  elsif start == :verb
    # assume the subject is the player then
    return parse_subject(word_list, Pair.new(:noun, "player"))
  else
    raise ParserError.new("Must start with subject, object, or verb not: #{start}")
  end
end

```

## 關於異常(Exception)

你已經簡單學過關於異常的一些東西，但還沒學過怎樣拋出(raise)它們。這節的程式碼示範了如何 raise。首先在最前面，你要定義好 `ParserException`這個類，而它又是 `Exception` 的一種。另外要注意我們是怎樣使用 `raise`這個關鍵字來拋出異常的。

你的測試程式碼應該也要測試到這些異常，這個我也會示範給你如何實現。

## 你應該測試的東西

為《習題 49》寫一個完整的測試方案，確認程式碼中所有的東西都能正常工作，其中異常的測試——輸入一個錯誤的句子它會拋出一個異常來。

使用 `assert_raises` 這個函式來檢查異常，在 Test::Unit 的文件裡查看相關的內容，學著使用它寫針對「執行失敗」的測試，這也是測試很重要的一個方面。從文件中學會使用 `assert_raises`，以及一些別的函式。

寫完測試以後，你應該就明白了這段程式碼的運作原理，而且也學會了如何為別人的程式碼寫測試程式碼。相信我，這是一個非常有用的技能。

## 加分習題

1.  修改 `parse_` method，將它們放到一個類裡邊，而不僅僅是獨立的方法函式。這兩種設計你喜歡哪一種呢？
2.  提高 parser 對於錯誤輸入的抵禦能力，這樣即使使用者輸入了你預定義語彙之外的詞語，你的程式碼也能正常運行下去。
3.  改進語法，讓它可以處理更多的東西，例如數字。
4.  想想在遊戲裡你的 Sentence 類可以對使用者輸入做哪些有趣的事情。