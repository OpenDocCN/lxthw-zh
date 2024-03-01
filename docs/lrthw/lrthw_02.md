這道習題並沒有程式碼。它的主要目的是讓你在電腦上安裝好 Ruby，你應該儘量照著指示操作。

這份教學已經預設你將使用 Ruby 1.9.2

你的系統裡面可能已經裝好了 Ruby。打開 console 並嘗試運行:

```rb
      $ ruby -v
ruby 1.9.2

```

如果你的系統內並沒有 Ruby，不論你使用的是哪一套作業系統，我都高度建議你使用 [Ruby Version Manager (RVM)](https://rvm.beginrescueend.com/) 安裝 Ruby。

## Mac OSX

你需要做下列任務來完成這個習題：

1.  用瀏覽器打開 [`learnpythonthehardway.org/wiki/ExerciseZero`](http://learnpythonthehardway.org/wiki/ExerciseZero) 下載並安裝 `gedit` 文字編輯器。
2.  把 `gedit` 放到桌面或者快速啟動列，這樣以後你就可以方便使用它了。這兩個選項在安裝時可以看到。
    1.  執行 gedit （也就是你的編輯器），我們要先改掉一些愚蠢的預設值。
    2.  從 `gedit menu` 中打開 `Preferences` ，選擇 `Editor` 頁面。
    3.  將 `Tab width:` 改為 2。
    4.  選擇(確認有勾選到該選項) `Insert spaces instead of tabs` 。
    5.  然後打開 「Automatic indentation」 選項。
    6.  轉到 `View` 頁面，打開 「Display line numbers」 選項。
3.  找到 「Terminal」 程式。它的名字是 `Command Promot` ，或者你可以直接執行 `cmd` 。
4.  為它建立一個捷徑，放到桌面或者是快速啟動列中以方便使用。
5.  執行 Terminal，這個程式看上去不怎麼地。
6.  在 Termnal 程式裡執行 `irb` 。在 Terminal 中執行程式的方式是輸入程式的名稱然後再敲一下 Return (Enter)。
    1.  如果你執行 `irb` 但發現不存在(不認得 `irb` 這個指令)。請用 [Ruby Version Manager (RVM)](https://rvm.beginrescueend.com/) 安裝 Ruby。
7.  敲擊 CTRL-Z (Z) 退出 `irb` 。
8.  這樣你就應該能回到敲 `irb` 前的提示介面了。如果沒有的話自己研究一下為什麼。
9.  學著使用 Terminal 創造一個目錄，你可以上網搜尋怎麼做。
10.  學著使用 Terminal 進入一個目錄，同樣你可以上網搜尋。
11.  使用你的編輯器在你進入的目錄下建立一個檔案。你將建立一個檔案。使用 「Save」 或者 「Save As…」 選項，然後選擇這個目錄。
12.  使用鍵盤切回到 Terminal 視窗，如果不知道怎樣使用鍵盤切換，你一樣可以上網搜尋。
13.  回到 Terminal，看看你能不能使用命令列列出你在目錄裡新建立的檔案，在網路上搜尋怎麼列出檔案夾裡的資料。

> **Note:** 如果你在使用 gedit 上有問題，很有可能這是 non-English keyboards layout 造成的，那麼我會建議你改使用 [`www.barebones.com/products/textwrangler/`](http://www.barebones.com/products/textwrangler/)。

## OSX: 你應該看到的結果

以下是我在自己電腦的 Terminal 中練習上述習題時看到的內容。可能會跟你在自己電腦中看的到結果有些不同，所以看看你能不能搞清楚兩者的差異。

```rb
      Last login: Sat Apr 24 00:56:54 on ttys001
~ $ irb
ruby-1.9.2-p180 :001 >
ruby-1.9.2-p180 :002 > ^D
~ $ mkdir mystuff
~ $ cd mystuff
mystuff $ ls
# ... Use Gedit here to edit test.txt....
mystuff $ ls
test.txt
mystuff $

```

## Windows

> **Note:** Contributed by zhmark.

1.  用瀏覽器打開 [`learnpythonthehardway.org/wiki/ExerciseZero`](http://learnpythonthehardway.org/wiki/ExerciseZero) 下載並安裝 `gedit` 文字編輯器。
2.  把 `gedit` 放到桌面或者快速啟動列，這樣以後你就可以方便使用它了。這兩個選項在安裝時可以看到。 a. 執行 gedit （也就是你的編輯器），我們要先改掉一些愚蠢的預設值。 b. 從 `gedit menu` 中打開 `Preferences` ，選擇 `Editor` 頁面。 c. 將 `Tab width:` 改為 2。 d. 選擇(確認有勾選到該選項) `Insert spaces instead of tabs` 。 e. 然後打開 「Automatic indentation」 選項。 f. 轉到 `View`頁面，打開 「Display line numbers」 選項。
3.  找到 「Terminal」 程式。它的名字是 `Command Promot` ，或者你可以直接執行 `cmd` 。
4.  為它建立一個捷徑，放到桌面或者是快速啟動列中以方便使用。
5.  執行 Terminal，這個程式看上去不怎麼地。
6.  在 Termnal 程式裡執行 `irb` 。在 Terminal 中執行程式的方式是輸入程式的名稱然後再敲一下 Return (Enter)。
    1.  如果你執行 `irb` 但發現不存在(不認得 `irb` 這個指令)。請用 [Ruby Version Manager (RVM)](https://rvm.beginrescueend.com/) 安裝 Ruby。
7.  敲擊 CTRL-Z (Z) 退出 `irb` 。
8.  這樣你就應該能回到敲 `irb` 前的提示介面了。如果沒有的話自己研究一下為什麼。 .. _Ruby Version Manager (RVM): [`rvm.beginrescueend.com/`](https://rvm.beginrescueend.com/)
9.  學著使用 Terminal 創造一個目錄，你可以上網搜尋怎麼做。
10.  學著使用 Terminal 進入一個目錄，同樣你可以上網搜尋。
11.  使用你的編輯器在你進入的目錄下建立一個檔案。你將建立一個檔案。使用 「Save」 或者 「Save As…」 選項，然後選擇這個目錄。
12.  使用鍵盤切回到 Terminal 視窗，如果不知道怎樣使用鍵盤切換，你一樣可以上網搜尋。
13.  回到 Terminal，看看你能不能使用命令列列出你在目錄裡新建立的檔案，在網路上搜尋怎麼列出檔案夾裡的資料。

> **Warning:** 對於 Ruby 來說 Windows 是個大問題。有時候你在一台電腦上裝得好好的，但在另外一台電腦上卻會漏掉一堆重要功能。如果遇到問題的話，你可以訪問： [`rubyinstaller.org/`](http://rubyinstaller.org/)。

## Windows: 你應該看到的結果

```rb
      C:\Documents and Settings\you>irb
ruby-1.9.2-p180 :001 >
ruby-1.9.2-p180 :001 > ^Z

C:\Documents and Settings\you>mkdir mystuff

C:\Documents and Settings\you>cd mystuff

... Here you would use gedit to make test.txt in mystuff ...

C:\Documents and Settings\you\mystuff>
   <bunch of unimportant errors if you istalled it as non-admin - ignore them - hit Enter>
C:\Documents and Settings\you\mystuff>dir
 Volume in drive C is
 Volume Serial Number is 085C-7E02

 Directory of C:\Documents and Settings\you\mystuff

04.05.2010  23:32    <DIR>          .
04.05.2010  23:32    <DIR>          ..
04.05.2010  23:32                 6 test.txt
               1 File(s)              6 bytes
               2 Dir(s)  14 804 623 360 bytes free

C:\Documents and Settings\you\mystuff>

```

你會看到的提示介面、Ruby 資訊，以及一些其他東西可能非常不一樣，不過應該大致上不會差多少。如果你的系統差太多的話，反映給我們，我們會修正過來。

# Linux

Linux 系統可謂五花八門，安裝軟體的方式也個有不同。我們假設作為 Linux 使用者的你應該知道如何安裝軟體了，以下是給你的操作指示：

1.  用瀏覽器打開 [`learnpythonthehardway.org/wiki/ExerciseZero`](http://learnpythonthehardway.org/wiki/ExerciseZero) 下載並安裝 `gedit` 文字編輯器。
2.  把 `gedit` 放到 Window Manager 明顯的位置，以方便之後使用。
    1.  執行 gedit （也就是你的編輯器），我們要先改掉一些愚蠢的預設值。
    2.  從 `gedit menu` 中打開 `Preferences` ，選擇 `Editor` 頁面。
    3.  將 `Tab width:` 改為 2。
    4.  選擇(確認有勾選到該選項) `Insert spaces instead of tabs` 。
    5.  然後打開 「Automatic indentation」 選項。
    6.  轉到 `View` 頁面，打開 「Display line numbers」 選項。
3.  找到 「Terminal」 程式。它的名字可能是 `GNOME Terminal`\、\ `Konsole`\、或者 `xterm`\。
4.  把 Terminal 也放到 Dock 上。
5.  執行 Terminal，這個程式看上去不怎麼地。
6.  在 Termnal 程式裡執行 `irb` 。在 Terminal 中執行程式的方式是輸入程式的名稱然後再敲一下 Return (Enter)。
    1.  如果你執行 `irb` 但發現不存在(不認得 `irb` 這個指令)。請用 [Ruby Version Manager (RVM)](https://rvm.beginrescueend.com/) 安裝 Ruby。
7.  敲擊 CTRL-D (D) 退出 `irb` 。
8.  這樣你就應該能回到敲 `irb` 前的提示介面了。如果沒有的話自己研究一下為什麼。
9.  學著使用 Terminal 創造一個目錄，你可以上網搜尋怎麼做。
10.  學著使用 Terminal 進入一個目錄，同樣你可以上網搜尋。
11.  使用你的編輯器在你進入的目錄下建立一個檔案。你將建立一個檔案。使用 「Save」 或者 「Save As…」 選項，然後選擇這個目錄。
12.  使用鍵盤切回到 Terminal 視窗，如果不知道怎樣使用鍵盤切換，你一樣可以上網搜尋。
13.  回到 Terminal，看看你能不能使用命令列列出你在目錄裡新建立的檔案，在網路上搜尋怎麼列出檔案夾裡的資料。

## Linux: 你應該看到的結果

```rb
      $ irb
ruby-1.9.2-p180 :001 > 
ruby-1.9.2-p180 :002 > ^D
$ mkdir mystuff
$ cd mystuff
# ... Use gedit here to edit test.txt ...
$ ls
test.txt
$

```

你會看到的提示介面、Ruby 資訊，以及一些其他東西可能非常不一樣，不過應該大致上不會差多少。如果你的系統差太多的話，反映給我們，我們會修正過來。

## 給新手的告誡

你已經完成了這節習題，取決於你對電腦的熟悉程度，這個練習對你而言可能會有些難。如果你覺得有難度的話，你要自己克服困難，多花點時間學習一下。因為如果你不會這些基礎操作的話，寫程式對你來說將會是相當艱難的一件事。

如果有程式設計師叫你去使用 `vim` 或者 `emacs` ，你應該拒絕他們。當你成為一個更好的程式設計師的時候，這些編輯器才會適合你使用。你現在需要的一個可以編輯文字的編輯器。我們使用 `gedit` 是因為它很簡單，而且在不同的系統上面使用起來也是一樣的。就連專業程式設計師也用 `gedit` ，所以對於初學者而言它已經夠用了。

總有一天你會聽到有程式設計師建議你使用 Mac OSX 或者 Linux。如果他喜歡字體美觀，他會叫你弄台 Mac OSX 電腦，如果他們喜歡操作控制而且留了一把大鬍子，他會叫你安裝 Linux。這裡再度向你說明，只要是一台手上能用的電腦就夠了。你需要的只有三樣東西`gedit` 、一個 Terminal、還有 `IRB`。

Finally the purpose of this setup is so you can do three things very reliably while you work on the exercises:

最後要說的是這節習題的準備工作的目的，也就是讓你可以在以後的習題中順利做到下面的這些事情：

1.  使用 `gedit` 編寫程式碼。
2.  _ 執行 _ 你寫的習題答案。
3.  _ 修改 _ 錯誤的習題答案。
4.  重複上述步驟。

其他的事情只會讓你更困惑，所以還是堅持照著這個計畫進行吧。