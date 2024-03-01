接下來我要教你另外一種讓你傷腦筋的容器型資料結構，因為一旦你學會這種資料結構，你將擁有超酷的能力。這是最有用的容器：Hash。

Ruby 將這種資料類型叫做「Hash」，有的語言裡它的名稱是「dictionaries」。這兩種名字我都會用到，不過這並不重要，重要的是它們和陣列的區別。你看，針對陣列你可以做這樣的事情：

```rb
      ruby-1.9.2-p180 :015 > things = ['a','b','c','d']
 => ["a", "b", "c", "d"]
ruby-1.9.2-p180 :016 > print things[1]
b => nil
ruby-1.9.2-p180 :017 > things[1] = 'z'
 => "z"
ruby-1.9.2-p180 :018 > print things[1]
z => nil
ruby-1.9.2-p180 :019 > print things
["a", "z", "c", "d"] => nil
ruby-1.9.2-p180 :020 >

```

你可以使用數字作為陣列的「索引」，也就是你可以通過數字找到陣列中的元素。而 Hash 所作的，是讓你可以通過任何東西找到元素，不只是數字。是的，Hash 可以將一個物件和另外一個東西關聯，不管它們的類型是什麼，我們來看看：

```rb
      ruby-1.9.2-p180 :001 > stuff = {:name => "Rob", :age => 30, :height => 5*12+10}
 => {:name=>"Rob", :age=>30, :height=>70}
ruby-1.9.2-p180 :002 > puts stuff[:name]
Rob
 => nil
ruby-1.9.2-p180 :003 > puts stuff[:age]
30
 => nil
ruby-1.9.2-p180 :004 > puts stuff[:height]
70
 => nil
ruby-1.9.2-p180 :005 > stuff[:city] = "New York"
 => "New York"
ruby-1.9.2-p180 :006 > puts stuff[:city]
New York
 => nil
ruby-1.9.2-p180 :007 >

```

你將看到除了通過數字以外，我們在 Ruby 還可以用字串來從 Hash 中獲取 `stuff`，我們還可以用字串來往 Hash 中添加元素。當然它支持的不只有字串，我們還可以做這樣的事情：

```rb
      ruby-1.9.2-p180 :004 > stuff[1] = "Wow"
 => "Wow"
ruby-1.9.2-p180 :005 > stuff[2] = "Neato"
 => "Neato"
ruby-1.9.2-p180 :006 > puts stuff[1]
Wow
 => nil
ruby-1.9.2-p180 :007 > puts stuff[2]
Neato
 => nil
ruby-1.9.2-p180 :008 > puts stuff
{:name=>"Rob", :age=>30, :height=>70, :city=>"New York", 1=>"Wow", 2=>"Neato"}
 => nil
ruby-1.9.2-p180 :009 >

```

在這裡我使用了數字。其實我可以使用任何東西，不過這麼說並不准確，不過你先這麼理解就行了。

當然了，一個只能放東西進去的 Hash 是沒啥意思的，所以我們還要有刪除物件的方法，也就是使用 `delete` 這個關鍵字：

```rb
      ruby-1.9.2-p180 :009 > stuff.delete(:city)
 => "New York"
ruby-1.9.2-p180 :010 > stuff.delete(1)
 => "Wow"
ruby-1.9.2-p180 :011 > stuff.delete(2)
 => "Neato"
ruby-1.9.2-p180 :012 > stuff
 => {:name=>"Rob", :age=>30, :height=>70}
ruby-1.9.2-p180 :013 >

```

接下來我們要做一個練習，你必須「非常」仔細，我要求你將這個練習寫下來，然後試著弄懂它做了些什麼。這個練習很有趣，做完以後你可能會有豁然開朗的感覺。

```rb
      cities = {'CA' => 'San Francisco',
  'MI' => 'Detroit',
  'FL' => 'Jacksonville'}

cities['NY'] = 'New York'
cities['OR'] = 'Portland'

def find_city(map, state)
  if map.include? state
    return map[state]
  else
    return "Not found."
  end
end

# ok pay attention!
cities[:find] = method(:find_city)

while true
  print "State? (ENTER to quit) "
  state = gets.chomp

  break if state.empty?

  # this line is the most important ever! study!
  puts cities[:find].call(cities, state)
end

```

## 你應該看到的結果

```rb
      $ ruby ex40.rb 
State? (ENTER to quit) > CA
San Francisco
State? (ENTER to quit) > FL
Jacksonville
State? (ENTER to quit) > O
Not found.
State? (ENTER to quit) > OR
Portland
State? (ENTER to quit) > VT
Not found.
State? (ENTER to quit) >

```

## 加分習題

1.  在 Ruby 文件中找到 Hash 相關的內容，學著對 Hash 做更多的操作。
2.  找出一些 Hash 無法做到的事情。例如比較重要的一個就是 Hash 的內容是無序的，你可以檢查一下看看是否真是這樣。
3.  試著把 `for` 迴圈執行到 Hash 上面，然後試著在 `for` 迴圈中使用 Hash 的 each 函式，看看會有什麼樣的結果。