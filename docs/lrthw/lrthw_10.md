# 习题 8: 印出，印出

```rb
      formatter = "%s %s %s %s"

puts formatter % [1, 2, 3, 4]
puts formatter % ["one", "two", "three", "four"]
puts formatter % [true, false, false, true]
puts formatter % [formatter, formatter, formatter, formatter]
puts formatter % [
    "I had this thing.",
    "That you could type up right.",
    "But it didn't sing.",
    "So I said goodnight."
]

```

## 你應該看到的結果

```rb
      $ ruby ex8.rb
1 2 3 4
one two three four
true false false true
%s %s %s %s %s %s %s %s %s %s %s %s %s %s %s %s
I had this thing. That you could type up right. But it didn't sing. So I said goodnight.
$

```

## 加分習題

1.  自己檢查結果，記錄你犯過的錯誤，並且在下個練習中儘量不犯相同的錯誤。