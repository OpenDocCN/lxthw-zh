雖然能讓瀏覽器顯示「Hello World」是很有趣的一件事情，但是如果能讓用戶通過表單(form)向你的應用程序提交資訊就更有趣了。這節習題中，我們將使用 form 改進你的 web 程式，並且搞懂如何為一個網站程式寫自動化測試。

## Web 運作原理

該學點無趣的東西了。在建立 form 前你需要先多學一點關於 web 的運作原理。這裡講的並不完整，但是相當準確，在你的程式出錯時，它會幫你找到出錯的原因。另外，如果你理解了 form 的應用，那麼建立 form 對你來說就會更容易了。

我將以一個簡單的圖示講起，它向你展示了 web 請求的各個不同的部分，以及資訊傳遞的大致流程：

為了方便講述 HTTP 請求(request) 的流程，我在每條線上面加了字母標籤以作區別。

1.  你在瀏覽器中輸入網址 http://learnpythonthehardway.org/，然後瀏覽器會通過你的電腦的網路設備發出 request（`線路 A`）。
2.  你的 request 被傳送到網際網路（`線路 B`），然後再抵達遠端服務器（`線路 C`），然後我的伺服器將接受這個 request。
3.  我的伺服器接受 request 後，我的 web 應用程式就去處理這個請求（`線路 D`），然後我的軮頁應用程式就會去運行 `/` (index) 這個「處理程序(handler)」。
4.  在程式碼 return 的時候，我的伺服器就會發出響應(response)，這個響應會再通過`線路 D`傳遞到你的瀏覽器。
5.  這個網站所在的伺服器將響應由`線路 D`獲取，然後通過`線路 C`傳至網際網路。
6.  響應通過網路網路由`線路 B`傳至你的電腦，電腦的網路卡再通過`線路 A`將響應傳給你的瀏覽器。
7.  最後，你的瀏覽器顯示了這個響應的內容。

這段詳解中用到了一些術語。你需要掌握這些術語，以便在談論你的 web 應用時你能明白而且應用它們：

### 瀏覽器(browser)

這是你幾乎每天都會用到的軟件。大部分人不知道它真正的原理，他們只會把它叫作「網際網路」。它的作用其實是接收你輸入到地址欄網址(例如[`learnpythonthehardway.org`](http://learnpythonthehardway.org))，然後使用該資訊向該網址對應的伺服器提出請求(request)。

### IP 位址 ( Address )

通常這是一個像 [`learnpythonthehardway.org/`](http://learnpythonthehardway.org/) 一樣的 URL (Uniform Resource Locator，統一資源定位符 )，它告訴瀏覽器該打開哪個網站。前面的 `http` 指出了你要使用的協議(protocol)，這裡我們用的是「超文本傳輸協議(Hyper-Text Transport Protocol)」。你還可以試試 ftp://ibiblio.org/，這是一個「FTP 文件傳輸協議(File Transport Protocol)‘的例子。`learnpythonthehardway.org` 這部分是「主機名(hostname)」，也就是一個便於人閱讀和記憶的字串，主機名會被匹配到一串叫作「IP 位址」的數字上面，這個「IP 位址」就相當於網路中一台電腦的電話號碼，通過這個號碼可以訪問到這台電腦。最後，URL 中還可以尾隨一個「路徑「，例如 http://learnpythonthehardway.org/book/ 中的 `/book/`，它對應的是伺服器上的某個文件或者某些資源，通過訪問這樣的網址，你可以向伺服器發出請求，然後獲得這些資源。網站地址還有很多別的組成部分，不過這些是最主要的。

### 連接(connection)

一旦瀏覽器知道了協議(http)、伺服器(learnpythonthehardway.org)、以及要獲得的資源，它就要去建立一個連接。這個過程中，瀏覽器讓操作系統(Operating System, OS) 打開計算機的一個「埠號(port)」（通常是 80 埠號），埠號準備好以後，操作系統會回傳給你的程式一個類似檔案的東西，它所做的事情就是通過網路傳輸和接收資料，讓你的電腦和 learnpythonthehardway.org 這個網站所屬的伺服器之間實現資料交流。當你使用 [`localhost:4567/`](http://localhost:4567/) 訪問你自己的站點時，發生的事情其實是一樣的，只不過這次你告訴了瀏覽器要訪問的是你自己的電腦(localhost)，要使用的端口不是默認的 80，而是 4567 。你還可以直接訪問 http://learnpythonthehardway.org:80/，這和不輸入埠號效果一樣，因為 HTTP 的默認埠號本來就是 80。

### 請求(request)

你的瀏覽器通過你提供的地址建立了連接，現在它需要從遠端伺服器要到它（或你）想要的資源。如果你在 URL 的結尾加了 `/book/`，那你想要的就是`/book/` 對應的檔案或資源，大部分的伺服器會直接為你呼叫`/book/index.html` 這個檔案，不過我們就假裝不存在好了。瀏覽器為了獲得伺服器上的資源，它需要向伺服器發送一個「請求」。這裡我就不講細節了，為了得到伺服器上的內容，你必須先向伺服器發送一個請求才行。有意思的是，「資源」不一定非要是檔案。例如當瀏覽器向你的應用程序提出請求的時候，伺服器返回的其實是你的程式碼生成的一些東西。

### 伺服器(server)

伺服器指的是瀏覽器另一端連接的電腦，它知道如何回應瀏覽器請求的檔案和資源。大部分的 web 伺服器只要發送檔案就可以了，這也是伺服器流量的主要部分。不過你學的是使用 Ruby 組建一個伺服器，這個伺服器知道如何接受請求，然後返回用 Ruby 處理過的字符串。當你使用這種處理方式時，你其實是假裝把檔案發給了瀏覽器，其實你用的都只是程式碼而已。就像你在《習題 50》中看到的，要構建一個「響應」其實也不需要多少程式碼。

### 響應(response)

這就是你的伺服器回覆給你的請求，傳回至瀏覽器的 HTML，它裡邊可能有 css、javascript、或者圖像等內容。以檔案響應為例，伺服器只要從磁碟讀取檔案，發送給瀏覽器就可以了，不過它還要將這些內容包在一個特別定義的「header]」中，這樣瀏覽器就會知道它獲取的是什麼類型的內容。以你的 web 應用程式為例，你發送的其實還是一樣的東西，包括 header 也一樣，只不過這些資料是你用 Ruby 程式碼即時生成的。

這個可以算是你能在網上找到的關於瀏覽器如何訪問網站的最快的快速課程了。這節課程應該可以幫你更容易地理解本節的習題，如果你還是不明白，就到處找資料多多了解這方面的資訊，知道你明白為止。有一個很好的方法，就是你對照著上面的圖示，將你在《習題 50》中創建的 web 程式中的內容分成幾個部分，讓其中的各部分對應到上面的圖示。如果你可以正確地將程式的各部分對應到這個圖示，你就大致開始明白它的運作原理了。

## 表單(form)的運作原理

熟悉「表單」最好的方法就是寫一個可以接收表單資料的程式出來，然後看你可以對它做些什麼。先將你的`lib/gothonsweb.rb` 修改成下面的樣子：

```rb
      require_relative "gothonweb/version"
require "sinatra"
require "erb"

module Gothonweb
  get '/' do
    greeting = "Hello, World!"
    erb :index, :locals => {:greeting => greeting}
  end

  get '/hello' do
    name = params[:name] || "Nobody"
    greeting = "Hello, #{name}"
    erb :index, :locals => {:greeting => greeting}
  end
end

```

重啟你的 Sinatra（按 CTRL-C 後重新運行），確認它有運行起來，然後使用瀏覽器訪問 [`localhost:4567/hello，這時瀏覽器應該會顯示`](http://localhost:4567/hello，這時瀏覽器應該會顯示) “I just wanted to say Hello , Nobody.”，接下來，將瀏覽器的地址改成 [`localhost:4567/hello?name=Frank，然後你可以看到頁面顯示為`](http://localhost:4567/hello?name=Frank，然後你可以看到頁面顯示為) “Hello, Frank.”，最後將 `name=Frank` 修改為你自己的名字，你就可以看到它對你說 Hello 了。

讓我們研究一下你的程式裡做過的修改。

1.  我們沒有直接為 greeting 賦值，而是使用了 `params` Hash 從瀏覽器獲取數據。這 Sinatra 個函數會將一組在 URL `?` 後面的部份的 key / value 組加進 `prarms` Hash 裡。
2.  然後我從 `params[:name]` 中找到 `name` 的值，並為 `greeting` 賦值，這部份相信你已經很熟悉了。
3.  其他的內容和以前是一樣的，我們就不再分析了。

URL 中該還可以包含多個參數。將本例的 URL 改成這樣子： `http://localhost:4567/hello?name=Frank&greet=Hola`。然後修改程式碼，讓它去存取 `prarams[:name]` 和 `params[:greet]`，如下所示：

```rb
      greeting = "#{greet}, #{name}"

```

## 創建 HTML 表單

你可以通過 URL 參數實現表單提交，不過這樣看上去有些醜陋，而且不方便一般人使用，你真正需要的是一個「POST 表單」，這是一種包含了`<form>`標籤的特殊 HTML 檔案。這種表單收集使用者輸入並將其傳遞給你的 web 程式，這和你上面實現的目的基本是一樣的。

讓我們來快速建立一個，從中你可以看出它的運作原理。你需要創建一個新的 HTML 文件，叫做 `lib/views/hello_form.erb`：

```rb
      <html>
    <head>
        <title>Sample Web Form</title>
    </head>
<body>

<h1>Fill Out This Form</h1>

<form action="/hello" method="POST">
    A Greeting: <input type="text" name="greet">
    <br/>
    Your Name: <input type="text" name="name">
    <br/>
    <input type="submit">
</form>

</body>
</html>

```

然後將 `lib/gothonsweb.rb`改成這樣：

```rb
      require_relative "gothonweb/version"
require "sinatra"
require "erb"

module Gothonweb

  get '/' do
    greeting = "Hello, World!"
    erb :index, :locals => {:greeting => greeting}
  end

  get '/hello' do
    erb :hello_form
  end

  post '/hello' do
    greeting = "#{params[:greet] || "Hello"}, #{params[:name] || "Nobody"}"
    erb :index, :locals => {:greeting => greeting}
  end

end

```

都寫好以後，重啟 web 程式，然後通過你的瀏覽器訪問它。

這回你會看到一個表單，它要求你輸入「一個問候語句(A Greeting)」和「你的名字(Your Name)」，等你輸入完後點擊「提交(Submit)」按鈕，它就會輸出一個正常的問候頁面，不過這一次你的 URL 還是 [`localhost:4567/hello，並沒有添加參數進去`](http://localhost:4567/hello，並沒有添加參數進去)。

在`hello_form.erb` 裡面關鍵的一行是`<form action="/hello" method="POST">`，它告訴你的瀏覽器以下內容：

1.  從表單中的各個欄位收集使用者輸入的資料。
2.  讓瀏覽器使用一種 POST 類型的請求，將這些資料發送給服務器。這是另外一種瀏覽器請求，它會將表單欄位「隱藏」起來。
3.  將這個請求發送至`/hello` URL，這是由`action="/hello"`告訴瀏覽器的。
4.  你可以看到兩段`<input>`標籤的名字屬性(name)和程式碼中的變數是對應的，另外我們在 class index 中使用的不再只是 GET 方法，而是另一個 POST 方法。

這個新程式的運作原理如下：

1.  瀏覽器訪問到 web 程式的 `/hello` 目錄，它發送了一個 GET 請求，於是我們的 `get '/hello/` 就運行了並傳回了 hello_form。
2.  你填好了瀏覽器的表單，然後瀏覽器依照`<form>`中的要求，將資料通過 POST 請求的方式發給 web 程式。
3.  Web 程式運行了 `post '/hello'` 而不是不是 `get '/hello/`來處理這個請求。
4.  這個 `post '/hello'`完成了它正常的功能，將 `hello` 頁面返回，這裡並沒有新的東西，只是一個新函式名稱而已。

作為練習，在 `lib/views/index.erb` 中添加一個鏈接，讓它指向 `/hello`，這樣你可以反覆填寫並提交表單查看結果。確認你可以解釋清楚這個鏈接的工作原理，以及它是如何讓你實現在 `lib/views/index.erb` 和`lib/views/hello_form.erb`之間循環跳轉的，還有就是要明白你新修改過的 Ruby 程式碼，你需要知道在什麼情況下會運行到哪一部分程式碼。

## Creating A Layout Template

在你下一節練習建立遊戲的過程中，你需要建立很多的小 HTML 頁面。如果你每次都寫一個完整的網頁，你會很快感覺到厭煩的。幸運的是你可以建立一個「外觀 (layout」模板，也就是一種提供了通用的 headers 和 footers 的外殼模板，你可以用它將你所有的其他網頁包裹起來。好程式設計師會盡可能減少重複動作，所以要做一個好程式設計師，使用外觀模板是很重要的。

將 `lib/views/index.erb` 修改成這樣：

```rb
      <% if greeting %>
  <p>I just wanted to say <em style="color: green; font-size: 2em;"><%= greeting %></em>.
<% else %>
  <em>Hello</em>, world!
<% end %>

```

然後把 `lib/views/hello_form.erb` 修改成這樣：

```rb
      <h1>Fill Out This Form</h1>

<form action="/hello" method="POST">
    A Greeting: <input type="text" name="greet">
    <br/>
    Your Name: <input type="text" name="name">
    <br/>
    <input type="submit">
</form>

```

面這些修改的目的，是將每一個頁面頂部和底部的反覆用到的「樣板 (boilerplate)」程式碼剝掉。這些被剝掉的程式碼會被放到一個單獨的`lib/views/layout.erb` 檔案中，從此以後，這些反覆用到的程式碼就由`lib/views/layout.erb` 來提供了。

上面的都改好以後，建立一個 `lib/views/layout.erb` 檔案，內容如下：

```rb
      <html>
  <head>
    <title>Gothons From Planet Percal #25</title>
  </head>
  <body>
    <%= yield %>
  </body>
</html>

```

Sinatra 預設會自動去找名字為 `layout` 的外觀模板，並且使用它作為其他模板的「基礎」模板。你也可以修改已經用作任何頁面的基礎模板的 template。重啟你的程式觀察一下，然後試著用各種方法修改你的 layout 模板，不要修改你別的模板，看看輸出會有什麼樣的變化。

## 為表單撰寫自動測試程式碼

使用瀏覽器測試 web 程式是很容易的，只要點刷新按鈕就可以了。不過畢竟我們是程式設計師嘛，如果我們可以寫一些程式碼來測試我們的程式，為什麼還要重複手動測試呢？接下來你要做的，就是為你的 web 程式寫一個小測試。這會用到你在《習題 47》學過的一些東西，如果你不記得的話，可以回去複習一下。

我已經為此建立了一個簡單的小函式，讓你判斷(assert) web 程序的響應，這個函數有一個很合適的名字，就叫 `assert_response`。創建一個 `tests/tools.rb` 檔案，內容如下：

```rb
      require 'test/unit'

def assert_response(resp, contains=nil, matches=nil, headers=nil, status=200)

  assert_equal(resp.status, status, "Expected response #{status} not in #{resp}")

  if status == 200
    assert(resp.body, "Response data is empty.")
  end

  if contains
    assert((resp.body.include? contains), "Response does not contain #{contains}")
  end

  if matches
    reg = Regexp.new(matches)
    assert reg.match(contains), "Response does not match #{matches}"
  end

  if headers
    assert_equal(resp.headers, headers)
  end

end

```

最後，執行 `test/test_gothonsweb.rb` 去測試你的程式：

```rb
      $ ruby test/test_gothonweb.rb 
Loaded suite test/test_gothonweb
Started
.
Finished in 0.023839 seconds.

1 tests, 9 assertions, 0 failures, 0 errors, 0 skips

Test run options: --seed 57414

```

`rack/test` 函式庫包含了一串很簡單的 API 可以讓你處理請求。他們是 `get`, `put`, `post`, `delete`和 `head` 函式，模擬程式會遇到的各類類型請求。

所有假的 (mock) request 函式會有一樣的參數模式：

```rb
      get '/path', params={}, rack_env={}

```

*   `/path` 是 request 路徑，而且可以選擇性的包含一個 query string。
*   `params` 是一組 query/post 的 Hash 參數，一個 request body 字串，或者是 nil
*   `rack_env` 是一個 Rack 環境值 Hash。這可以用來設置 request 的 header 和其他 request 相關的資訊，例如 session 內的資料。

這樣的運作方式就不用實際運作一個真的 web 伺服器，如此一來你就可以使用自動化測試程式碼去測試，當然同時你也可以使用瀏覽器去測試一個執行中的伺服器。

為了驗證(validate) 函式的響應，你需要使用 `test/tools.rb` 中定義的`assert_response` 函式，裡面內容是：

To validate responses from this function, use the `assert_response` function from `test/tools.rb`which has:

```rb
      assert_response(resp, contains=nil, matches=nil, headers=nil, status=200)

```

把你呼叫 `get` 或 `post` 得到的響應傳遞給這個函數，然後將你要檢查的內容作為參數傳遞給這個函數。你可以使用 `contains`參數來檢查響應中是否包含指定的值，使用 `status` 參數可以檢查指定的響應狀態。這個小函式其實包含了很多的資訊，所以你還是自己研究一下的比較好。

在 `test/test_gothonsweb.rb` 自動測試腳本中，我首先確認 `/foo` URL 傳回了一個「404 Not Found」響應，因為這個 URL 其實是不存在的。然後我檢查了`/hello` 在 GET 和 POST 兩種請求的情況下都能正常運作。就算你沒有弄明白測試的原理，這些測試程式碼應該是很好讀懂的。

花一些時間研究一下這個最新版的 web 程式，重點研究一下自動測試的運作原理。

## 加分習題

1.  閱讀和 HTML 相關的更多資料，然後為你的表單設計一個更好的輸出格式。你可以先在紙上設計出來，然後用 HTML 去實現它。
2.  這是一道難題，試著研究一下如何進行檔案上傳，通過網頁上傳一張圖像，然後將其保存到磁碟中。
3.  更難的難題，找到 HTTP RFC 文件（講述 HTTP 運作原理的技術文件），然後努力閱讀一下。這是一篇很無趣的文件，不過偶爾你會用到裡邊的一些知識。
4.  又是一道難題，找人幫你設置一個 web 伺服器，例如 Apache、Nginx、或者 thttpd。試著讓伺服器伺服一下你建立的.html 和.css 文件。如果失敗了也沒關係，web 服務器本來就都有點爛。
5.  完成上面的任務後休息一下，然後試著多建立一些 web 程式出來。你應該仔細閱讀 Sinatra 中關於會話(session)的內容，這樣你可以明白如何存留使用者的狀態資訊。