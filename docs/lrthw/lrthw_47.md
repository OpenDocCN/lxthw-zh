# 习题 45: 物件、类和从属关系

有一個重要的概念你需要弄明白，那就是 `Class`「類」和 `Object`「物件」的區別。問題在於，class 和 object 並沒有真正的不同。它們其實是同樣的東西，只是在不同的時間名字不同罷了。我用禪語來解釋一下吧：

`魚(Fish)和鮭魚(Salmon)有什麼區別？`

這個問題有沒有讓你有點暈呢？說真的，坐下來想一分鐘。我的意思是說，魚和鮭魚是不一樣，不過它們其實也是一樣的是不是？泥鰍是魚的一種，所以說沒什麼不同，不過泥鰍又有些特別，它和別的種類的魚的確不一樣，比如鮭魚和比目魚就不一樣。所以鮭魚和魚既相同又不同。怪了。

這個問題讓人暈的原因是大部分人不會這樣去思考問題，其實每個人都懂這一點，你無須去思考魚和鮭魚的區別，因為你知道它們之間的關係。你知道鮭魚是魚的一種，而且魚還有別的種類，根本就沒必要去思考這類問題。

讓我們更進一步，假設你有一隻水桶，裡邊有三條鮭魚。假設你的好人卡多到沒地方用，於是你給它們分別取名叫 Frank，Joe，Mary。現在想想這個問題：

`Mary 和鮭魚有什麼區別？`

這個問題一樣的奇怪，但比起魚和鮭魚的問題來還好點。你知道 Mary 是一條鮭魚，所以他並沒什麼不同，他只是鮭魚的一個「實例(instance)」。Joe 和 Frank 一樣也是鮭魚的實例。我的意思是說，它們是由鮭魚創建出來的，而且代表著和鮭魚一樣的屬性。

所以我們的思維方式是（你可能會有點不習慣）：魚是一個「類(class)」，鮭魚是一個「類(class)」，而 Mary 是一個「物件(object)」。仔細想想，然後我再一點一點慢慢解釋給你。

魚是一個「類」，表示它不是一個真正的東西，而是一個用來描述具有同類屬性的實例的概括性詞彙。你有鰭？你有鰾？你住在水裡？好吧那你就是一條魚。

後來一個博士路過，看到你的水桶，於是告訴你：「小伙子，你這些魚是鮭魚。」 專家一出，真相即現。並且專家還定義了一個新的叫做​​「鮭魚」的「類」，而這個「類」又有它特定的屬性。長鼻子？紅肉？體型大？住在海裡或是乾淨新鮮的水裡？吃起來味道不錯？那你就是一條鮭魚。

最後一個廚師過來了，他跟博士說：「非也非也，你看到的是鮭魚，我看到的是 Mary，而且我要把 Mary 淋上美味醬料做一道小菜。 」於是你就有了一隻叫做 Mary 的鮭魚的「實例(instance)」（鮭魚也是魚的一個「實例」），並且你使用了它（把它塞到你的胃裡了），這樣它就是一個​​「物件(object)」。

這會你應該了解了：Mary 是鮭魚的成員，而鮭魚又是魚的成員。這裡的關係式：物件屬於某個類，而某個類又屬於另一個類。

## 寫成程式碼是什麼樣子

這個概念有點詭異，不過實話說，你只要在建立和使用 class 的時候操心一下就可以了。我來給你兩個區分 `Class` 和 `Object`的小技巧。

首先針對類和物件，你需要學會兩個說法，「is-a(是啥)」和「has-a(有啥)」。「是啥」要用在談論「兩者以類的關係互相關聯」的時候，而「有啥」要用在「兩者無共同點，僅是互為參照」的時候。

接下來，通讀這段程式碼，將每一個註解為`##??`的位置標明他是「is-a」還是「has-a」的關係，並講明白這個關係是什麼。在程式碼的開始我還舉了幾個例子，所以你只要寫剩下的就可以了。

記住，「是啥」指的是魚和鮭魚的關係，而「有啥」指的是鮭魚和烤肉架的關係。

```rb
      ## Animal is-a object (yes, sort of confusing) look at the extra credit
class Animal

end

## ??
class Dog < Animal

  def initialize(name)
    ## ??
    @name = name
  end

end

## ??
class Cat < Animal

  def initialize(name)
    ## ??
    @name = name
  end

end

## ??
class Person

  attr_accessor :pet

  def initialize(name)
    ## ??
    @name = name

    ## Person has-a pet of some kind
    @pet = nil
  end

end
## ??
class Employee < Person

  def initialize(name, salary)
    ## ?? hmm what is this strange magic?
    super(name)
    ## ??
    @salary = salary
  end

end

## ??
class Fish

end

## ??
class Salmon < Fish

end

## ??
class Halibut < Fish

end

## rover is-a Dog
rover = Dog.new("Rover")

## ??
satan = Cat.new("Satan")

## ??
mary = Person.new("Mary")

## ??
mary.pet = satan

## ??
frank = Employee.new("Frank", 120000)

## ??
frank.pet = rover

## ??
flipper = Fish.new

## ??
crouse = Salmon.new

## ??
harry = Halibut.new

```

## 加分習題

1.  有沒有辦法把 `Class` 當作 `Object` 使用呢？
2.  在習題中為 animals、fish、還有 people 添加一些函式，讓它們做一些事情。看看當函數在 Animal 這樣的「基類(base class)」裡和在 Dog 裡有什麼區別。
3.  找些別人的程式碼，理清裡邊的「是啥」和「有啥」的關係。
4.  使用 Array 和 Hash 建立一些新的一對應多的「has-many」的關係。
5.  你認為會有一種「has-many」的關係嗎？閱讀一下關於「多重繼承(multiple inheritance)」的資料，然後儘量避免這種用法。