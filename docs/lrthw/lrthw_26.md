# 习题 24: 更多练习

你離這本書第一部分的結尾已經不遠了，你應該已經具備了足夠的 Ruby 基礎知識，可以繼續學習一些程式的原理了，但你應該做更多的練習。這個練習的內容比較長，它的目的是鍛煉你的毅力，下一個習題也差不多是這樣的，好好完成它們，做到完全正確，記得仔細檢查。

```rb
      puts "Let's practice everything."
puts "You\'d need to know \'bout escapes with \\ that do \n newlines and \t tabs."

poem = <<MULTI_LINE_STRING

\tThe lovely world
with logic so firmly planted
cannot discern \n the needs of love
nor comprehend passion from intuition
and requires an explanation
\n\t\twhere there is none.

MULTI_LINE_STRING

puts "--------------"
puts poem
puts "--------------"

five = 10 - 2 + 3 - 6
puts "This should be five: #{five}"

def secret_formula(started)
  jelly_beans = started * 500
  jars = jelly_beans / 1000
  crates = jars / 100
  return jelly_beans, jars, crates
end

start_point = 10000
beans, jars, crates = secret_formula(start_point)

puts "With a starting point of: #{start_point}"
puts "We'd have #{beans} beans, #{jars} jars, and #{crates} crates."

start_point = start_point / 10

puts "We can also do that this way:"
puts "We'd have %s beans, %s jars, and %s crates." % secret_formula(start_point)

```

## 你應該看到的結果

```rb
      $ ruby ex24.rb
Let's practice everything.
You'd need to know 'bout escapes with \ that do 
 newlines and    tabs.
--------------

    The lovely world
with logic so firmly planted
cannot discern 
 the needs of love
nor comprehend passion from intuition
and requires an explanation

        where there is none.

--------------
This should be five: 5
With a starting point of: 10000
We'd have 5000000 beans, 5000 jars, and 50 crates.
We can also do that this way:
We'd have 500000 beans, 500 jars, and 5 crates.
$

```

## 加分習題

1.  記得仔細檢查結果，從後往前倒著檢查，把程式碼朗讀出來，在不清楚的位置加上註釋。
2.  故意將程式碼改爛，執行並檢查會發生什麼樣的錯誤，並且確認你有能力改正這些錯誤。