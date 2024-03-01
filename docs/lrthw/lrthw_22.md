回憶一下函式的要點，然後一邊做這節練習，一邊注意一下函式和檔案是如何一起協作發揮作用的。

```rb
      input_file = ARGV[0]

def print_all(f)
  puts f.read()
end

def rewind(f)
  f.seek(0, IO::SEEK_SET)
end

def print_a_line(line_count, f)
  puts "#{line_count} #{f.readline()}"
end

current_file = File.open(input_file)

puts "First let's print the whole file:"
puts # a blank line

print_all(current_file)

puts "Now let's rewind, kind of like a tape."

rewind(current_file)

puts "Let's print three lines:"

current_line = 1
print_a_line(current_line, current_file)

current_line = current_line + 1
print_a_line(current_line, current_file)

current_line = current_line + 1
print_a_line(current_line, current_file)

```

特別注意一下，每次運行 `print_a_line` 時，我們是怎樣傳遞當前的行號資訊的。

## 你應該看到的結果

```rb
      $ ruby ex20.rb test.txt
First let's print the whole file:

To all the people out there.
I say I don't like my hair.
I need to shave it off.

Now let's rewind, kind of like a tape.
Let's print three lines:
1 To all the people out there.
2 I say I don't like my hair.
3 I need to shave it off.

$

```

## 加分習題

1.  通讀腳本，在每行之前加上註解，以理解腳本裡發生的事情。
2.  每次 `print_a_line` 運行時，你都傳遞了一個叫 `current_line`的變數。在每次呼叫函數時，印出 `current_line` 的值，跟踪一下它在 `print_a_line` 中是怎樣變成 `line_count` 的。
3.  找出腳本中每一個用到函式的地方。檢查 `def` 一行，確認參數沒有用錯。
4.  上網研究一下 file 中的 `seek` 函數是做什麼用的。試著運行 `ri file` 看看能不能從 `rdoc` 中學到更多。
5.  研究一下 `+=` 這個簡寫操作符號的作用，寫一個腳本，把這個操作符號用在裡邊試一下。