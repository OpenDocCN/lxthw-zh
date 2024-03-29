# 习题 18: 命名、变数、程式码、函式

好大的一個標題。接下來我要教你「函式 (function)」了！咚咚鏘！說到函式，不一樣的人會對它有不一樣的理解和使用方法，不過我只會教你現在能用到的最簡單的使用方式。

函式可以做三件事情：

1.  它們可以給程式碼片段取名，就跟「變數」給字串和數字命名一樣。
2.  它們可以接受參數，就跟你的腳本接受 `ARGV` 一樣。
3.  通過使用 #1 和 #2 ，他們可以讓你創造出「迷你腳本」或者「微命令」。

你可以在 Ruby 中使用 `def` 新建函式，我將讓你創造四個不同的函式，它們運作起來和你的腳本一樣。然後我會示範給你各個函式之間的關係。

```rb
      # this one is like your scripts with argv
def puts_two(*args)
  arg1, arg2 = args
  puts "arg1: #{arg1}, arg2: #{arg2}"
end

# ok, that *args is actually pointless, we can just do this
def puts_two_again(arg1, arg2)
  puts "arg1: #{arg1}, arg2: #{arg2}"
end

# this just takes one argument
def puts_one(arg1)
  puts "arg1: #{arg1}"
end

# this one takes no arguments
def puts_none()
  puts "I got nothin'."
end

puts_two("Zed","Shaw")
puts_two_again("Zed","Shaw")
puts_one("First!")
puts_none()

```

讓我們把你一個函式 `puts_two` 肢解一下，這個函式和你寫腳本的方式差不多，因此看上去你應該會覺得比較眼熟：

1.  首先我們告訴 Ruby 創造一個函式，使用 `def` 去「定義(define)」一個函式。
2.  緊跟著 `def` 的是函式的名稱。本例中它的名稱是「puts_two」，但名字可以 隨便取，就叫「peanuts」也沒關係。但函式的名稱最好能夠表達出它的功能來。
3.  然後我們告訴函式我們需要 `args` (asterisk args)，這和腳本的 `ARGV` 非常相似，參數必須放在小括號 `()` 中才能正常運作。
4.  在定義(definition)之後，後面的行都必須以 2 個空格縮排。其中縮排的第一行的作用是將參數解包，就像我們在腳本中做的事一樣。
5.  為了示範它的運作原理，我們把解包後的每個參數都印出來。`puts_two` 的問題是它不是建立一個函式最簡單的方法。在 Ruby 中我們可以直接跳過解包參數的過程直接使用 `()` 裡面的名稱作為變數名。就像 `puts_two_again` 實現的功能。

接下來的例子是 `print_one` ，它像你示範了函式如何接收單個參數。

最後一個例子是 `print_none` ，它向你示範了函式可以不接收任何參數。

> **Warning:** 如果你不太能看懂上面的內容也別氣餒。這是非常重要的。後面我們還有更多的習題向你示範如何創造和使用函式。現在你只要把函式理解成「迷你腳本」就可以了

## 你應該看到的結果

執行上面的腳本會看到如下結果：

```rb
      $ ruby ex18.rb
arg1: 'Zed', arg2: 'Shaw'
arg1: 'Zed', arg2: 'Shaw'
arg1: 'First!'
I got nothin'.
$

```

你應該看出來函式是怎樣運作的了。注意到函式的用法和你以前見過的 `File.exist?` 、 `File.open`以及別的「命令」有點類似了吧？其實我只是為了讓你容易禮節才叫他們「命令」。它們的本質其實就是函式。也就是說，你也可以在你自己的腳本中創造你自己的「命令」。

## 加分習題

為自己寫一個函式檢查清單以供後續參考。你可以寫在一個索引卡片上隨時閱讀，直到你記住所有的要點為止。注意事項如下：

1.  函式定義是以 `def` 開始的嗎？
2.  函式名稱是以字串和底線 `_` 組成的嗎？
3.  函式名稱是不是緊跟著括號 `(` ？
4.  括號裡是否包含參數？多個參數是否以逗號隔開？
5.  參數名稱是否有重複？（不能使用重複的參數名）
6.  緊跟著參數的最後是否括號 `)` ？
7.  緊跟著函式定義的程式碼是否用了 2 個空格的縮排 ( `indent` )？
8.  函式結束的位置是不是「end」

當你執行（或者說「使用(use)」或者「呼叫(call)」一個函數時，記得檢查下列幾項事情：

1.  呼叫函式時是否使用了函式的名稱？
2.  函式名稱是否緊跟著`()`？（非必要，理想性的話應該要加）
3.  參數是否以逗號隔開？
4.  函式是否以`)`結尾？

按照這兩份檢查清單裡的內容檢查你的習題，直到你不需要檢查清單為止。

最後，將下面這句話閱讀幾遍：

> 「執行(run)函式」、「呼叫(call)函式」和「使用(use)函式」是同一個意思。