現在讓我們再學習幾種檔案操作。我們將編寫一個 Ruby 腳本，將一個檔案中的內容拷貝到另一個檔案中。這個腳本很短，不過它會讓你對於檔案操作有更多的了解。

```rb
      from_file, to_file = ARGV
script = $0

puts "Copying from #{from_file} to #{to_file}"

# we could do these two on one line too, how?
input = File.open(from_file)
indata = input.read()

puts "The input file is #{indata.length} bytes long"

puts "Does the output file exist? #{File.exists? to_file}"
puts "Ready, hit RETURN to continue, CTRL-C to abort."
STDIN.gets

output = File.open(to_file, 'w')
output.write(indata)

puts "Alright, all done."

output.close()
input.close()

```

你應該注意到了我們使用了一個很好用的函式 `File.exists?`。運作原理是將檔名字串當做一個參數傳入，如果檔案存在的話，它會傳回 `true`，如果不存在的話就傳回 `false`。之後在這本書中，我們將會使用這個函式做更多的事情。

## 你應該看到的結果

如同你前面所寫的腳本，運行該腳本需要兩個參數，一個是待拷貝的檔案位置，一個是要拷貝至的檔案位置。如果我們使用以前的 `test.txt` 我們將看到如下的結果：

```rb
      $ ruby ex17.rb test.txt copied.txt
Copying from test.txt to copied.txt
The input file is 81 bytes long
Does the output file exist? False
Ready, hit RETURN to continue, CTRL-C to abort.

Alright, all done.

$ cat copied.txt
To all the people out there.
I say I don't like my hair.
I need to shave it off.
$

```

該命令對於任何檔案應該都是有效的。試試操作一些別的檔案看看結果。不過當心別把你的重要檔案給弄壞了。

> **Warning:** 你看到我用 `cat` 這個指令了吧？它只能在 Linux 和 OX 下使用，Windows 用戶可以使用 `type` 做到相同效果。

## 加分習題

1.  再多讀讀和 `require` 相關的資料，然後將 IRB 跑起來，試試 require 一些東西看能不能摸出門到。當然，即使搞不清楚也沒關係。
2.  這個腳本實在有點煩人。沒必要再拷貝之前都問一遍吧，沒必要在螢幕上輸出那麼多東西。試著刪掉腳本的一些功能，使它用起來更友善。
3.  看看你能把這個腳本改到多短，我可以把它寫成一行。
4.  我使用了一個叫 `cat` 的東西，這個古老的命令用處是將兩個檔案「連接(con_cat_enate）」在一起，不過實際上它最大的用處是印出檔案內容到螢幕是。你可以通過 `man cat` 命令了解到更多資訊。
5.  使用 Windows 的人，你們可以給自己找一個 `cat` 的替代品。關於 `man` 的東西就別想太多了。Windows 下沒這個指令。
6.  找出為什麼需要在程式碼中寫 `output.close()` 的原因。