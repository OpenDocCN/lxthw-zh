你應該在習題 0 中花了不少的時間，學會了如何安裝文字編輯器、執行文字編輯器、以及如何運行 Terminal，如果你還沒這麼做的話，請別繼續往前走，之後會有很多苦頭的。請不要跳過前一個習題的內容繼續前進，這也是本書唯一的一次在習題開頭就做這樣的警告。

```rb
      puts "Hello World!"
puts "Hello Again"
puts "I like typing this."
puts "This is fun."
puts 'Yay! Printing.'
puts "I'd much rather you 'not'."
puts 'I "said" do not touch this.'

```

將上面的內容寫到一個檔案中，取名為 `ex1.rb`。注意這樣的命名方式，Ruby 文件最好以 `.rb` 結尾。

然後你需要在 Terminal 中輸入以下內容來執行這段程式：

```rb
      ruby ex1.rb

```

如果你寫對了的話，你應該看到和下面一樣的內容。如果不一樣，那就是你弄錯了什麼東西。不是電腦有問題，電腦沒問題。

## 你應該看到的內容

```rb
      $ ruby ex1.rb
Hello World!
Hello Again
I like typing this.
This is fun.
Yay! Printing.
I'd much rather you 'not'.
I "said" do not touch this.
$ 

```

你也許會看到 `$` 前面會顯示你所在的目錄的名稱，這部是問題，但如果你的輸出不一樣的話，你需要找出為什麼會不一樣，然後把你的程式改對。

如果你看到類似如下的錯誤資訊:

```rb
      ruby ex1.rb
ex1.rb:4: syntax error, unexpected tCONSTANT, expecting $end
puts "This is fun."
          ^

```

看懂這些內容對你來說是很重要的。因為你以後還會犯類似的錯誤。就是我現在也會犯這樣的錯誤。讓我們一行一行來看。

1.  首先我們在 Terminal 輸入命令來執行 `ex1.rb` 腳本。
2.  Ruby 告訴我們 `ex1.rb` 檔案的第 4 行有一個錯誤。
3.  然後這一行的內容被印了出來。
4.  然後 Ruby 印出了一個 `^` (插入符號，caret) 符號，用來指示錯誤的位置。
5.  最後，它印出了一行「語法錯誤(SyntaxError)」告訴你究竟是發生了怎麼樣的錯誤。通常這些錯誤資訊都非常的難懂，不過你可以把錯誤資訊的內容複製到搜尋引擎裡，然後你就能看到別人也遇到過這樣的錯誤，而且你也許能搞清楚怎樣解決這個問題。

## 加分習題

你還會有加分習題需要完成。加分習題裡面的內容是供你嘗試的。如果你覺得做不出來，你可以暫時跳過， 過段時間再回來做。

在這個練習中，試試這些東西：

1.  讓你的腳本再多印一行。
2.  讓你的腳本只印其中的一行。
3.  在一行的開始位置放置一個 `#` (octothorpe) 符號。它的作用是什麼？自己研究一下。
4.  從現在開始，除非特別情況，我將不再解釋每個習題的運作原理了。

> **Note:** 井號有很多的英文代稱，例如「octothorpe ( 八角帽 )」」、「pound( 英镑符號 )」、「hash( 電話的 # 键 )」、「mesh ( 網 )」。