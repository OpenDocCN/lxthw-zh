# 习题 9: 印出，印出，印出

```rb
      # Here's some new strange stuff, remember type it exactly.

days = "Mon Tue Wed Thu Fri Sat Sun"
months = "Jan\nFeb\nMar\nApr\nMay\nJun\nJul\nAug"

puts "Here are the days: ", days
puts "Here are the months: ", months

puts <<PARAGRAPH
There's something going on here.
With the three double-quotes.
We'll be able to type as much as we like.
Even 4 lines if we want, or 5, or 6.
PARAGRAPH

```

## 你應該看到的結果

```rb
      $ ruby ex9.rb
Here are the days:  
Mon Tue Wed Thu Fri Sat Sun
Here are the months:
Jan
Feb
Mar
Apr
May
Jun
Jul
Aug
There's something going on here.
With the three double-quotes.
We'll be able to type as much as we like.
Even 4 lines if we want, or 5, or 6.

```

## 加分習題

1.  自己檢查結果，記錄你犯過的錯誤，並且在下個練習中儘量不犯相同的錯誤。