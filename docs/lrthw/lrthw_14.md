看看這段 code

```rb
      require 'open-uri'

open("http://www.ruby-lang.org/en") do |f|
  f.each_line {|line| p line}
  puts f.base_uri         # <URI::HTTP:0x40e6ef2 URL:http://www.ruby-lang.org/en/>
  puts f.content_type     # "text/html"
  puts f.charset          # "iso-8859-1"
  puts f.content_encoding # []
  puts f.last_modified    # Thu Dec 05 02:45:02 UTC 2002
end

```

在第一行是 require。這是一個 Ruby 中在你所寫的腳本中加入其他來源（如：Ruby Gems 或者是你寫的其他東西）的功能(features) 的方法。與其一次給你所有功能，Ruby 會問你你打算使用什麼。這可使你的程式保持輕薄，又可當做之後其他程式設計師閱讀你的程式時的參考。

## 等一下！功能 (Features) 還有另外一個名字

我在這裡稱呼他們為「功能(features)」。但實際上沒人這樣稱呼。我這樣做只是取了點巧，使你在學習時先不用理解「行話」。在繼續進行之前你得先知道它們的真名 `modules`（模組）。

從現在開始我們將把這些我們 require 進來的功能稱作 `modules`（模組）。我會這樣說：「你想要 require `open-uri` module。」也有人給它另外一個稱呼：「函式庫(libraries)」。但在這裡我們還是先叫它們 `modules` （模組）吧。

## 加分習題

1.  上網搜尋 `require` 與 `include` 的差異點。它們有什麼不同？
2.  你能 `require` 一段沒有特別包含 `module` 的腳本嗎？
3.  搞懂 Ruby 會去系統的哪裡找你 require 的 modules。