# 习题 28: 布林（Boolean）表示式练习

上一節你學到的邏輯組合的正式名稱是「布林邏輯表示式(boolean logic expression)」。在程式中，布林邏輯可以說是無處不在。它們是電腦運算的基礎和重要組成部分，掌握它們就跟學音樂掌握音階一樣重要。

在這節練習中，你將在 IRB 裡使用到上節學到的邏輯表示式。先為下面的每一個邏輯問題寫出你認為的答案，每一題的答案要嘛為 True 要嘛為 False。寫完以後，你需要將 IRB 運行起來，把這些邏輯語句輸入進去，確認你寫的答案是否正確。

```rb
      1\. true and true
2\. false and true
3\. 1 == 1 and 2 == 1
4\. "test" == "test"
5\. 1 == 1 or 2 != 1
6\. true and 1 == 1
7\. false and 0 != 0
8\. true or 1 == 1
9\. "test" == "testing"
10\. 1 != 0 and 2 == 1
11\. "test" != "testing"
12\. "test" == 1
13\. not (true and false)
14\. not (1 == 1 and 0 != 1)
15\. not (10 == 1 or 1000 == 1000)
16\. not (1 != 10 or 3 == 4)
17\. not ("testing" == "testing" and "Zed" == "Cool Guy")
18\. 1 == 1 and not ("testing" == 1 or 1 == 0)
19\. "chunky" == "bacon" and not (3 == 4 or 3 == 3)
20\. 3 == 3 and not ("testing" == "testing" or "Ruby" == "Fun")

```

在本節結尾的地方我會給你一個理清複雜邏輯的技巧。

所有的布林邏輯式都可以用下面的簡單流程得到結果：

1.  找到相等判斷的部分 (== or !=)，將其改寫為其最終值(True 或 False)。
2.  找到括號裡的 and/or，先算出它們的值。
3.  找到每一個 not，算出他們反過來的值。
4.  找到剩下的 and/or，解出它們的值。
5.  等你都做完後，剩下的結果應該就是 True 或者 False 了。

下面我們以 #20 邏輯式示範一下：

`3 != 4 and not ("testing" != "test" or "Ruby" == "Ruby")`

接下來你將看到這個複雜表達式是如何逐級解析為一個單獨結果的：

1.  出每一個等值判斷:
    *   `3 != 4` 為 **True**: `true and not ("testing" != "test" or "Ruby" == "Ruby")`
    *   `"testing" != "test"` 為 **True**: `true and not (true or "Ruby" == "Ruby")`
    *   `"Ruby" == "Ruby"`: `true and not (true or true)`
2.  找到 `()` 中的每一個 and/or :
    *   `(true or true)` is **True**: `true and not (true)`
3.  找到每一個 not 並將其逆轉:
    *   `not (true)` is **False**: `true and false`
4.  找到剩下的 and/or，解出它們的值:
    *   `true and false` is **False**

這樣我們就解出了它最終的值為 False .

> **Warning:** 雜的邏輯表達式一開始看上去可能會讓你覺得很難。而且你也許已經碰壁過了，不過別灰心，這些「邏輯體操」式的訓練只是讓你逐漸習慣起來，這樣後面你可以輕易應對程式裡邊更酷的一些東西。只要你堅持下去，不放過自己做錯的地方就行了。如果你暫時不太能理解也沒關係，弄懂的時候總會到來的。

## 你應該看到的結果

以下內容是在你自己猜測結果以後，通過和 IRB 對話得到的結果：

```rb
      $ irb
ruby-1.9.2-p180 :001 > true and true
 => true 
ruby-1.9.2-p180 :002 > 1 == 1 and 2 == 2
 => true 

```

## 加分習題

1.  Ruby 裡還有很多和 `!=`、`==`類似的操作符號。試著盡可能多的列出 Ruby 中的「等價運算符號」。例如 `<` 或是 `<=`。
2.  寫出每一個等價運算符號的名稱。例如 `!=` 叫「not equal（不等於」。
3.  在 IRB 裡測試新的布林邏輯式。在敲 Enter 前你需要喊出它的結果。不要思考，憑自己的第一直覺就可以了。把表達式和結果用筆寫下來再敲 Enter，最後看自己做對多少，做錯多少。
4.  把習題 3 那張紙丟掉，以後你不再需要查詢它了。