現在我們將做一批練習，在練習的過程中你需要鍵入程式碼，並且讓它們運行起來，我不會解釋太多，因為這節的內容都是以前熟悉的。這節練習的目的是鞏固你學到的東西，我們幾輪練習後再見。不要跳過這些習題，不要複製貼上！

```rb
      puts "Mary had a little lamb."
puts "Its fleece was white as %s." % 'snow'
puts "And everywhere that Mary went."
puts "." * 10  # what'd that do?

end1 = "C"
end2 = "h"
end3 = "e"
end4 = "e"
end5 = "s"
end6 = "e"
end7 = "B"
end8 = "u"
end9 = "r"
end10 = "g"
end11 = "e"
end12 = "r"

# notice how we are using print instead of puts here. change it to puts
# and see what happens.
print end1 + end2 + end3 + end4 + end5 + end6
print end7 + end8 + end9 + end10 + end11 + end12

# this just is polite use of the terminal, try removing it
puts

```

## 你應該看到的結果

```rb
      $ ruby ex7.rb
Mary had a little lamb.
Its fleece was white as snow.
And everywhere that Mary went.
..........
CheeseBurger
$

```

## 加分習題

接下來幾節的加分習題是一樣的。

1.  逆向閱讀，在每一行的上面加一行註釋。
2.  倒著閱讀出來，找出自己的錯誤。
3.  從現在開始，把你的錯誤記錄下來，寫在一張紙上。
4.  在開始下一節習題時，閱讀一遍你記錄下來的錯誤。並且儘量避免在下個練習中再犯相同的錯誤。
5.  記住，每個人都會犯錯。程式設計師和魔術師一樣，他們希望大家認為他們從不犯錯，不過這只是表象而已，他們每時每刻都在犯錯。