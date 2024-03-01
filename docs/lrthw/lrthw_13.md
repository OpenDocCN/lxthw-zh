我已經出過很多有關於印出的習題，讓你習慣寫出簡單的東西，但簡單的東西都有點無聊，我們現在要做的的事是把資料(data)讀到你的程式裡面去。這對你可能會有點難度，你可能一下子搞不明白，不過相信我，無論如何先把習題做了再說。只要做幾道練習你就明白了。

一般軟體做的事情主要就是下面幾件：

1.  接受人的輸入。
2.  改變輸入值。
3.  印出改變了的值。

到目前為止你只做了印出，但還不會接受或修改人的輸入。你還不知道「輸入(input)」是什麼意思。閒話少說，我們還是開始做點習題看你能不能明白，下一道習題裡面我們將會有更詳細的解釋。

```rb
      print "How old are you? "
age = gets.chomp()
print "How tall are you? "
height = gets.chomp()
print "How much do you weigh? "
weight = gets.chomp()

puts "So, you're #{age} old, #{height} tall and #{weight} heavy."

```

> **Note:** 注意到我們是使用 `print` 而非 `puts` 嗎？ `print` 不會自動產生新行。這樣你的答案就可以跟問題在同一行了。換句話說，`puts` 會自動產生新行。

## 你應該看到的結果

$ ruby ex11.rb How old are you? 35 How tall are you? 6’2” How much do you weigh? 180lbs So, you’re ‘35’ old, ‘6'2”’ tall and ‘180lbs’ heavy. $

## 加分習題

1.  上網搜尋一下 Ruby 的 `gets` 和 `chomp` 的功能是什麼？
2.  你能找到 `gets.chomp` 別的用法嗎？測試一下你上網找到的例子。
3.  用類似的格式再寫一段，把問題改成你自己的問題。