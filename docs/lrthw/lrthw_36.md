# 习题 34: 存取阵列里的元素

陣列非常有用，但只有你存取裡面的內容時，它才能發揮出作用來。你已經學會了案順序讀出陣列中的內容，但如果你要得到第 5 個元素該怎麼辦呢？你需要知道如何存取陣列中的元素。存取第一個元素的方法是這樣的：

```rb
      animals = ['bear', 'tiger', 'penguin', 'zebra']
bear = animals[0]

```

你定義一個 animals 的陣列，然後你用 `0` 來存取第一個元素！？這是怎麼回事啊？因為數學裡面就是這樣，所以 Ruby 的陣列也是從 0 開始的。雖然看起來很奇怪，這樣定義其實有它的好處。

最好的解釋方式勢將你平常使用數字的方式和程式設計師使用數字的方式做比較。

假設你在觀看上面陣列中的四種動物：(`['bear', 'tiger', 'penguin', 'zebra']`) 的賽跑。而它們比賽的名次正好跟陣列中的順樹一樣。這是一場很刺激的比賽，因為這些動物沒打算吃掉對方，而且比賽還真的舉辦起來了。結果你的朋友來晚了，他想知道誰贏了比賽，他會問你「嘿，誰是第 0 名？」嗎？不會的，他會問「嘿，誰是第 1 名？」

這是因為動物的次序是很重要的。沒有第一個就沒有第二個，沒有第二個話也不會有第三個。第零個是不存在的，因為零的意思是什麼都沒有。「什麼都沒有」怎麼贏比賽嘛？完全不和邏輯。這樣的數字我們稱之為「序數(ordinal number)」

而程式設計師不能用這種方式思考問題，因為他們可以從陣列中的任何一個位置取出一個元素來。對程式設計師來說，上述的陣列更像是一疊卡片。如果他們想要 tiger，就抓它出來，如果想要 zeebra，也一樣抓出來。要隨機地抓陣列裡的內容，陣列的每一個元素都應該要有一個地址(address)，或者一個「索引(index)」，而最好的方式就是使用以 0 開頭的索引。相信我說的這一點吧，這種方式獲取元素會更容易。而這一類的數字被稱為「基數(cardinal number)」，它意味著你可以任意抓取元素，所以我們需要一個 0 號元素。

那麼，這些知識對你的陣列操作有什麼幫助呢？很簡單，每次你對自己說：「我要第 3 隻動物」時，你需要將「序數」轉換成「基數」，只要將前者減 1 就可以了。第 3 隻動物的索引是 2，也就是 penguin。由於你一輩子都在跟序數打交道，所以你需要這種方式來獲得基數，只要減 1 就都搞定了。

記住：ordinal == 有序，以 1 開始；cardinal == 隨機存取，以 0 開始。

讓我們練習一下。定義一個動物列表，然後跟著做後面的習題，你需要寫出所指位置的動物名稱。如果我用的是「first」、「second」等說法。那說明我用的是敘述，所以你需要減去 1。如果我給你的是基數 ( 0, 1, 2 )，你只要直接使用即可。

```rb
      animals = ['bear', 'python', 'peacock', 'kangaroo', 'whale', 'platypus']

```

The animal at 1\. The 3rd animal. The 1st animal. The animal at 3\. The 5th animal. The animal at 2\. The 6th animal. The animal at 4.

對於上述某一條，以這樣的格式寫出一個完整的句子：「The 1st animal is at 0 and is a bear.」然後倒過來念「 “The animal at 0 is the 1st animal and is a bear.」

使用 IRB 去檢查你的答案。

**Hint:** Ruby 還有一些便利的 method 是屬於在陣列中存取特定元素的用法。：`animals.first` 和 `animals.last`。

## 加分習題

1.  上網搜尋一下關於 序數 （ordinal number) 和基數 (cardinal number) 的知識並閱讀一下。
2.  以你對於這些數字類型的了解，解釋一下為什麼今年是 2010 年。呢是：你不能隨便挑選年份。
3.  再寫一些陣列，用一樣的方式做出索引，確認自己可以在兩種數字之間互相翻譯。
4.  使用 IRB 檢查自己的答案。

> **Warning:** 會有程式設計師告訴你，叫你去閱讀一個叫「Dijkstra」的人寫的關於數字的主題。我建議你還是不讀為妙，除非你喜歡聽一個在寫程式這一行剛興起時就停止了從事寫程式工作的人對你大吼大叫。