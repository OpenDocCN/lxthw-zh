# 习题 14: 提示和传递

讓我們使用 `ARGV` 和 `gets.chomp` 一起來向使用者提一些特別的問題。下一節習題你將會學習到如何讀寫檔案，這節習題是下節的基礎。在這道習題裡我們將用一個簡單的 `>` 作為提示符號。這和一些遊戲中的方法類似，例如 Zork 或者 Adventure 這兩款遊戲。

```rb
      user = ARGV.first
prompt = '> '

puts "Hi #{user}, I'm the #{$0} script."
puts "I'd like to ask you a few questions."
puts "Do you like me #{user}?"
print prompt
likes = STDIN.gets.chomp()

puts "Where do you live #{user}?"
print prompt
lives = STDIN.gets.chomp()

puts "What kind of computer do you have?"
print prompt
computer = STDIN.gets.chomp()

puts <<MESSAGE
Alright, so you said #{likes} about liking me.
You live in #{lives}.  Not sure where that is.
And you have a #{computer} computer.  Nice.
MESSAGE

```

注意到我們將用戶提示符號設置為 `prompt`，這樣我們就不用每次都要重打一遍了。如果你要將提示符號和修改成別的字串，你只要改一個地方就可以了。

非常順手吧。

> **Important:** 同時必須注意的是，我們也用了 `STDIN.gets` 取代了 `gets`。這是因為如果有東西在 `ARGV` 裡，標準的`gets` 會認為將第一個參數當成檔案而嘗試從裡面讀東西。在要從使用者的輸入（如`stdin`）讀取資料的情況下我們必須明確地使用 `STDIN.gets`。

## 你應該看到的結果

當你執行這個腳本時，記住你需要把你的名字傳給這個腳本，讓 `ARGV` 可以接收到。

```rb
      $ ruby ex14.rb Zed
Hi Zed, I'm the ex14.rb script.
I'd like to ask you a few questions.
Do you like me Zed?
> yes
Where do you live Zed?
> America
What kind of computer do you have?
> Tandy

Alright, so you said 'yes' about liking me.
You live in 'America'.  Not sure where that is.
And you have a 'Tandy' computer.  Nice.

```

## 加分習題

1.  查一下 Zork 和 Adventure 是兩個怎樣的遊戲。看能不能抓到，然後玩玩看。
2.  將 `prompt` 變數改為完全不同的內容再執行一遍。
3.  給你的腳本再新增一個參數，讓你的程式用到這個參數。
4.  確認你弄懂了我如何結合 `<<SOMETHING` 形式的多行字串與 `#{}` 字串注入做的印出。