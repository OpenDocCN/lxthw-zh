# 习题 13: 参数、解包、参数

在這節習題中，我們將涵蓋另外一種將變數傳遞給腳本的方法（所謂腳本，就是你寫的 `.rb` 檔案）。你已經知道，如果要執行 `ex13.rb`，只要在命令列中執行 `ruby ex13.rb` 就可以了。這句命令中的 `ex13.rb` 部分就是所謂的「參數(argument)」，我們現在要做的就是寫一個可以接受參數的腳本。

將下面的程式寫下來，後來我將詳細解釋

```rb
      first, second, third = ARGV

puts "The script is called: #{$0}"
puts "Your first variable is: #{first}"
puts "Your second variable is: #{second}"
puts "Your third variable is: #{third}"

```

`ARGV` 就是「參數變數(argument variable)」，是一個非常標準的程式術語。在其他的程式語言你也可以看到它全大寫的原因是因為它是一個「常數(constant)」，意思是當它被賦值之後你就不應該去改變它了。這個變數會接收當你運行 Ruby 腳本時所傳入的參數。通過後面的習題你將對它有更多的了解。 你将对它有更多的了解。

第 1 行將 `ARGV` 「解包(unpack)」，與其將所有參數放到同一個變數下面，我們將每個參數賦予一個變數名稱 `first` 、 `second` 以及 `third`。腳本本身的名稱被存在一個特殊變數 `$0` 裡，這是我們不需要解包的部份。也許看來有些詭異，但「解包」可能是最好的描述方式了。它的涵義很簡單：「將 `ARGV` 中的東西解包，然後將所有的參數依次賦予左邊的變數名稱」。

接下來就是正常的印出了。

## 你應該看到的結果

用下面的方法執行你的程式：

```rb
      ruby ex13.rb first 2nd 3rd

```

如果你每次使用不同的參數執行，你將看到下面的結果：

```rb
      $ ruby ex13.rb first 2nd 3rd
The script is called: ex13.rb
Your first variable is: first
Your second variable is: 2nd
Your third variable is: 3rd

$ ruby ex13.rb cheese apples bread
The script is called: ex13.rb
Your first variable is: cheese
Your second variable is: apples
Your third variable is: bread

$ ruby ex13.rb Zed A. Shaw
The script is called: ex13.rb
Your first variable is: Zed
Your second variable is: A.
Your third variable is: Shaw

```

你其實可以將「first」、「2nd」、「3rd」替換成任意三樣東西。你可以將它們換成任意你想要的東西。

```rb
      ruby ex13.rb stuff I like
ruby ex13.rb anything 6 7

```

## 加分習題

1.  傳三個以下的參數給你的腳本。當有缺少參數時哪些數值會被使用到？
2.  再寫兩個腳本，其中一個接收更少的參數，另一個接收更多的參數。在參數解包時給它們取一些有意義的變數名稱。
3.  結合 `gets.chomp` 和 `ARGV` 一起使用，讓你的腳本從用戶手上得到更多輸入。