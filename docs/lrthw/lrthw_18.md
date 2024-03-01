# 习题 16: 读写档案

如果你做了上一個練習的加分習題，你應該已經了解了個個種文件相關的命令（方法/函式）。你應該記住的命令如下：

*   close – 關閉檔案。跟你編輯器的 `文件->儲存..` 是一樣的意思。
*   read – 讀取檔案內容。你可以把結果賦給一個變數。
*   readline – 讀取檔案文字中的一行。
*   truncate – 清空文件，請小心使用該命令。
*   write(stuff) – 將 stuff 寫入檔案。

這是你現在應該知道的重要命令。有些命令需要接收參數，但這對我們並不重要。你只要記住 write 的用法就可以了。 `write` 需要接收一個字串作為參數，從而將該字串寫入檔案。

讓我們來使用這些命令做一個簡單的文字編輯器吧：

```rb
      filename = ARGV.first
script = $0

puts "We're going to erase #{filename}."
puts "If you don't want that, hit CTRL-C (^C)."
puts "If you do want that, hit RETURN."

print "? "
STDIN.gets

puts "Opening the file..."
target = File.open(filename, 'w')

puts "Truncating the file.  Goodbye!"
target.truncate(target.size)

puts "Now I'm going to ask you for three lines."

print "line 1: "; line1 = STDIN.gets.chomp()
print "line 2: "; line2 = STDIN.gets.chomp()
print "line 3: "; line3 = STDIN.gets.chomp()

puts "I'm going to write these to the file."

target.write(line1)
target.write("\n")
target.write(line2)
target.write("\n")
target.write(line3)
target.write("\n")

puts "And finally, we close it."
target.close()

```

這是一個大檔案，大概是你鍵入過的最大的檔案。所以慢慢來，仔細檢查，讓它能夠跑起來。有一個小技巧就是你可以讓你的腳本一部分一部分地跑起來。先寫 1-8 行，讓它能跑起來，再多做 5 行，再接著幾行，以此類推，直到整個腳本都可以跑起來為止。

## 你應該看到的結果

你將看到兩樣東西，一樣是你新腳本的輸出：

```rb
      $ ruby ex16.rb test.txt
We're going to erase 'test.txt'.
If you don't want that, hit CTRL-C (^C).
If you do want that, hit RETURN.
?
Opening the file...
Truncating the file.  Goodbye!
Now I'm going to ask you for three lines.
line 1: To all the people out there.
line 2: I say I don't like my hair.
line 3: I need to shave it off.
I'm going to write these to the file.
And finally, we close it.
$

```

這是一個大檔案，大概是你鍵入過的最大的檔案。所以慢慢來，仔細檢查，讓它能夠跑起來。有一個小技巧就是你可以讓你的腳本一部分一部分地跑起來。先寫 1-8 行，讓它能跑起來，再多做 5 行，再接著幾行，以此類推，直到整個腳本都可以跑起來為止。

## 加分習題

1.  如果你覺得自己沒有弄懂的話，用我們的老方法，在每一行之前加上註釋，為自己理清思路。就算不能理清思路，你也可以知道自己究竟具體哪裡沒弄清楚。
2.  寫一個和上一個習題類似的腳本，使用 `read` 和 `ARGV` 讀取你剛才新建立的文件。
3.  檔案中重複的地方太多了。試著用一個 `target.write()` 將 `line1` ， `line2` ， `line3` 印出來，你可以使用字串、格式化字串以及跳脫字串。
4.  找出為什麼我們打開檔案時要使用 `w` 模式，而你真的需要 `target.truncate()` 嗎？去看 Ruby 的 `File.open` 函式找答案吧。