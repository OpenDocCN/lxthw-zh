# 习题 50: 你的第一个网站

這節以及後面的習題中，你的任務是把前面建立的遊戲做成網頁版。這是本書的最後三個章節，這些內容對你來說難度會相當大，你要在上面花些時間才能做出來。在你開始這節練習以前，你必須已經成功地完成過了《習題 46》的內容，正確安裝了 **RubyGems**，而且學會瞭如何安裝軟體套件以及如何建立專案骨架。如果你不記得這些內容，就回到《習題 46》重新複習一遍。

## 安裝 Sinatra

在建立你的第一個網頁應用程式之前，你需要安裝一個「Web 框架」，它的名字叫 **Sinatra**。所謂的「框架」通常是指「讓某件事情做起來更容易的軟體套件」。在網頁應用的世界裡，人們建立了各種各樣的「網頁框架」，用來解決他們在建立網站時碰到的問題，然後把這些解決方案用軟體套件的方式發佈出來，這樣你就可以利用它們引導建立你自己的專案了。

可選的框架類型有很多很多，不過在這裡我們將使用 Sinatra 框架。你可以先學會它，等到差不多的時候再去接觸其它的框架，不過 Sinatra 本身挺不錯的，所以就算你一直使用也沒關係。

使用 `gem` 安裝 Sinatra:

```rb
      $ gem install sinatra
Fetching: tilt-1.3.2.gem (100%)
Fetching: sinatra-1.2.6.gem (100%)
Successfully installed tilt-1.3.2
Successfully installed sinatra-1.2.6
2 gems installed
Installing ri documentation for tilt-1.3.2...
Installing ri documentation for sinatra-1.2.6...
Installing RDoc documentation for tilt-1.3.2...
Installing RDoc documentation for sinatra-1.2.6...

```

## 寫一個簡單的「Hello World」專案

現在你將做一個非常簡單的「Hello World」專案出來，首先你要建立一個專案目錄：

```rb
      $ cd projects
$ bundle gem gothonweb

```

你最終的目的是把《習題 42》中的遊戲做成一個 web 應用，所以你的專案名稱叫做 `gothonweb`，不過在此之前，你需要建立一個最基本的 Sinatra 應用，將下面的代碼放到`lib/gothonweb.rb`中：

```rb
      require_relative "gothonweb/version"
require "sinatra"

module Gothonweb
  get '/' do
    greeting = "Hello, World!"
    return greeting
  end
end

```

然後使用下面的方法來運行這個 web 程式：

```rb
      $ ruby lib/gothonweb.rb
== Sinatra/1.2.6 has taken the stage on 4567 for development with backup from WEBrick
[2011-07-18 11:27:07] INFO  WEBrick 1.3.1
[2011-07-18 11:27:07] INFO  ruby 1.9.2 (2011-02-18) [x86_64-linux]
[2011-07-18 11:27:07] INFO  WEBrick::HTTPServer#start: pid=6599 port=4567

```

最後，使用你的網頁瀏覽器，打開 URL `http://localhost:4567/`，你應該看到兩樣東西，首先是瀏覽器裡顯示了 `Hello, world!`，然後是你的命令行終端顯示了如下的輸出：

```rb
      127.0.0.1 - - [18/Jul/2011 11:29:10] "GET / HTTP/1.1" 200 12 0.0015
localhost - - [18/Jul/2011:11:29:10 EDT] "GET / HTTP/1.1" 200 12
- -> /
127.0.0.1 - - [18/Jul/2011 11:29:10] "GET /favicon.ico HTTP/1.1" 404 447 0.0008
localhost - - [18/Jul/2011:11:29:10 EDT] "GET /favicon.ico HTTP/1.1" 404 447
- -> /favicon.ico

```

這些是 Sinatra 印出的 log 資訊，從這些資訊你可以看出服務器有在運行，而且能了解到程式在瀏覽器背後做了些什麼事情。這些資訊還有助於你發現程式的問題。例如在最後一行它告訴你瀏覽器試圖存取 `/favicon.ico`，但是這個文件並不存在，因此它返回的狀態碼是 `404 Not Found`。

到這裡，我還沒有講到任何 web 相關的工作原理，因為首先你需要完成準備工作，以便後面的學習能順利進行，接下來的兩節習題中會有詳細的解釋。我會要求你用各種方法把你的 Sinatra 應用程式弄壞，然後再將其重新構建起來：這樣做的目的是讓你明白運行 Sinatra 程式需要準備好哪些東西。

## 發生了什麼事情？

在瀏覽器訪問到你的網頁應用程式時，發生了下面一些事情：

1.  瀏覽器通過網路連接到你自己的電腦，它的名字叫做 `localhost`，這是一個標準稱謂，表示的誰就是網路中你自己的這台電腦，不管它實際名字是什麼，你都可以使用 `localhost`來訪問。它使用到`port 4567`。
2.  連接成功以後，瀏覽器對 lib/gothonweb.rb`這個應用程式發出了 HTTP 請求(request)，要求訪問 URL`/`，這通常是一個網站的第一個 URL。
3.  在`lib/gothonweb.rb` 裡，我們有一個程式碼區段，裡面包含了 URL 的匹配關係。我們這裡只定義了一組匹配，那就是「/」。它的含義是：如果有人使用瀏覽器訪問 `/` 這一級目錄，Sinatra 將找到它，從而用它處理這個瀏覽器請求。
4.  Sinatra 呼叫匹配到的程式碼區段，這段程式碼只簡單的回傳了一個字串傳回給瀏覽器。
5.  最後 Sinatra 完成了對於瀏覽器請求的處理將響應(response)回傳給瀏覽器，於是你就看到了現在的頁面。

確定你真的弄懂了這些，你需要畫一個示意圖，來理清資訊是如何從瀏覽器傳遞到 Sinata，再到 `/`區段，再回到你的瀏覽器的。

## 修正錯誤

第一步，把第 6 行的 `greeting` 變數刪掉，然後重新刷瀏覽器。你應該會看到一個錯誤畫面，你可以通過這一頁豐富的資訊看出你的程式崩潰的原因。當然你已經知道出錯的原因是 `greeting`的賦值遺失了，不過 Sinatra 還是會給你一個挺好的錯誤頁面，讓你能找到出錯的具體位置。試試在這個錯誤頁面上做以下操作：

1.  看看 `sinatra.error` 變數。
2.  看看 `REQUEST_` 變數裡的資訊。裡面哪些知識是你已經熟悉了的。這是瀏覽器發給你的 gothonweb 應用程式的資訊。這些知識對於日常網頁瀏覽沒有什麼用處，但現在你要學會這些東西，以便寫出 web 應用程式來。

## 建立基本的模板

你已經試過用各種方法把這個 Sinatra 程式改錯，不過你有沒有注意到「Hello World」不是一個好 HTML 網頁呢？這是一個 web 應用，所以需要一個合適的 HTML 響應頁面才對。為了達到這個目的，下一步你要做的是將「Hello World」以較大的綠色字體顯示出來。

第一步是建立一個 `lib/views/index.erb` 檔案，內容如下：

```rb
      <html>
    <head>
        <title>Gothons Of Planet Percal #25</title>
    </head>
<body>

  <% if greeting %>
    <p>I just wanted to say <em style="color: green; font-size: 2em;"><%= greeting %></em>.
  <% else %>
    <em>Hello</em>, world!
  <% end %>

</body>
</html>

```

什麼是一個 `.erb` 的檔案？ERB 的全名是 **E**mbedded **R**u**b**y。`.erb` 檔案其實是一個內嵌一點 Ruby 程式碼的 HTML。如果你學過 HTML 的話，這些內容你看上去應該很熟悉。如果你沒學過 HTML，那你應該去研究一下，試著用 HTML 寫幾個網頁，從而知道它的運作原理。既然這是一個 `erb` 模版，Sinatra 就會在模板中找到對應的位置，將參數的內容填充到模板中。例如每一個出現 ` 的位置，內容都會被替換成對應這個變數名的參數。

為了讓你的 `lib/gothonweb.rb` 處理模板，你需要寫一寫程式碼，告訴 Sinatra 到哪裡去找到模板進行加載，以及如何渲染(render)這個模板，按下面的方式修改你的檔案：

```rb
      require_relative "gothonweb/version"
require "sinatra"
require "erb"

module Gothonweb
  get '/' do
    greeting = "Hello, World!"
    erb :index, :locals => {:greeting => greeting}
  end
end

```

特別注意我改了 `/` 這個程式碼區段最後一行的內容，這樣它就可以呼叫 `erb` 然後把 greeting 變數傳給它。

改好上面的程式後，刷新一下瀏覽器中的網頁，你應該會看到一條和之前不同的綠色資訊輸出。你還可以在瀏覽器中通過「查看原始碼(View Source)」看到模板被渲染成了標準有效的 HTML 原始碼。

這麼講也許有些太快了，我來詳細解釋一下模板的運作原理吧：

1.  在 `lib/gothonweb.rb` 你添加了一個 `erb` 函式呼叫。
2.  這個 `erb` 函式知道怎麼載入 `lib/views` 目錄夾裡的 `.erb` 的檔案。它知道去抓哪些檔案（在這個例子裡是 `index.erb`)。因為你傳了一個參數進去（`erb :index …`)。
3.  現在，當瀏覽器讀取 `/` 且 `lib/gothonweb.eb` 匹配然後執行 `get '/' do` 區段，它再也沒有只是回傳字串 `greeting`，而是呼叫 `erb` 然後傳入 `greeting` 作為一個變數。
4.  最後，你讓 `lib/views/index.erb` 去檢查 `greeting` 這個變數，如果這個變數存在的話，就印出變數裡的內容。如果不存在的話，就會印出一個預設的訊息。

要深入理解這個過程，你可以修改 `greeting 變數以及 HTML ，看看會友什麼效果。然後也創作另外一個叫做`lib/views/foo.erb`的模板。然後把`erb :index`改成`erb :foo`。從這個過程中你也可以看到，你傳入給`erb`的第一個參數只要匹配到`lib/views`下的`.erb` 檔案名稱，就可以被渲染出來了。

## 加分習題

1.  到 [Sinatra](http://www.sinatrarb.com/) 這個框架的官方網站去閱讀更多文件。
2.  實驗一下你在上述網站中看到的所有東西，包括他們的範例程式碼。
3.  閱讀有關於 HTML5 和 CSS3 相關的東西，自己練習寫幾個 `.html` 和 `.css` 文件。
4.  如果你有一個懂 **Rails** 的朋友可以幫你的畫，你可以自己試著使用 Rails 完成一下習題 50,51,52，看看結果會是什麼樣子。