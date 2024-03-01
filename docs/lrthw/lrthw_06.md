# Exercise 4: Variables And Names

你已經學會了印出東西和數學運算。下一步你要學的是「變數」。在開發程式中，變數只不過是用來代表某個東西的名稱。程式設計師通過使用變數名稱可以讓他們的程式讀起來更像英語。而且因為程式設計師的記性都不怎樣，變數名稱可以讓他們更容易記住程式的內容。如果他們沒有在寫程式時使用好的變數名稱，在下一次讀到原來寫的程式碼時對他們會大為頭疼的。

如果你被這章習題難住了的話，記得我們之前教過的：找到不同點、注意細節:

1.  在每一行的上面寫一行註釋，給自己解釋一下這一行的作用。
2.  倒著讀你的 `.rb` 檔案。
3.  朗讀你的 `.rb` 檔案，將每個字符也朗讀出來。

```rb
      cars = 100
space_in_a_car = 4.0
drivers = 30
passengers = 90
cars_not_driven = cars - drivers
cars_driven = drivers
carpool_capacity = cars_driven * space_in_a_car
average_passengers_per_car = passengers / cars_driven

puts "There are #{cars} cars available."
puts "There are only #{drivers} drivers available."
puts "There will be #{cars_not_driven} empty cars today."
puts "We can transport #{carpool_capacity} people today."
puts "We have #{passengers} passengers to carpool today."
puts "We need to put about #{average_passengers_per_car} in each car."

```

> **Note:** `space_in_a_car` 中的 `_` 是 `底線(underscore)` 符號。你要自己學會怎樣打出這個符號來。這個符號在變數裡通常被用作假想的空隔，用來隔開單詞。

## 你應該看到的結果

```rb
      $ ruby ex4.rb
There are 100 cars available.
There are only 30 drivers available.
There will be 70 empty cars today.
We can transport 120.0 people today.
We have 90 passengers to carpool today.
We need to put about 3 in each car.
$

```

## 加分習題

當我剛開始寫這個程式時我犯了個錯誤，Ruby 告訴我這樣的錯誤資訊：

```rb
      ex4.rb:8:in `<main>': undefined local variable or method `car_pool_capacity' for main:Object (NameError)

```

用你自己的話解釋一下這個錯誤資訊，解釋時記得使用行號，而且要說明原因。

## 更多的加分習題

1.  解釋一下為什麼程式裡面用了 4.0 而不是 4。
2.  記住 4.0 是一個「浮點數」，自己研究一下這是什麼意思。
3.  在每一個變數賦值的上一行加上一行註釋。
4.  記住 `=` 的名稱是等於(equal)，它的作用是為東西取名。
5.  記住 `_` 是底線(underscore)。
6.  將 IRB 作為計算機跑起來，就跟以前一樣，不過這一次在計算過程中使用變數名稱來做計算，常見的變數名稱有 `i` 、 `x` 、 `j` 等等。