# 习题 46: 一个专案骨架

這裡你將學會如何建立一個專案「骨架」目錄。這個骨架目錄具備讓專案跑起來的所有基本內容。它裡邊會包含你的專案檔案佈局、自動化測試程式碼，模組，以及安裝腳本。當你建立一個新專案的時候，只要把這個目錄複製過去，改改目錄的名字，再編輯裡面的檔案就行了。

## 骨架內容: Linux/OSX

首先使用下述命令創建你的骨架目錄：

```rb
      $ mkdir -p projects
$ cd projects/
$ mkdir skeleton
$ cd skeleton
$ mkdir bin lib lib/NAME test

```

我使用了一個叫 projects 的目錄，用來存放我自己的各個專案。然後我在裡邊建立了一個叫做 skeleton 的檔案夾，這就是我們新專案的基礎目錄。其中叫做 NAME 的檔案夾是你的專案的主檔案夾，你可以將它任意取名。

接下來我們要配置一些初始檔案：

```rb
      $ touch lib/NAME.rb
$ touch lib/NAME/version.rb

```

然後我們可以建立一個 `NAME.gemspec` 的檔案在我們的專案的根目錄，這個檔案在安裝專案的時候我們會用到它：

```rb
      # -*- encoding: utf-8 -*-
$:.push File.expand_path("../lib", __FILE__)
require "NAME/version"

Gem::Specification.new do |s|
  s.name        = "NAME"
  s.version     = NAME::VERSION
  s.authors     = ["Rob Sobers"]
  s.email       = ["rsobers@gmail.com"]
  s.homepage    = ""
  s.summary     = %q{TODO: Write a gem summary}
  s.description = %q{TODO: Write a gem description}

  s.rubyforge_project = "NAME"

  s.files         = `git ls-files`.split("\n")
  s.test_files    = `git ls-files -- {test,spec,features}/*`.split("\n")
  s.executables   = `git ls-files -- bin/*`.split("\n").map{ |f| File.basename(f) }
  s.require_paths = ["lib"]
end

```

編輯這個檔案，把自己的聯絡方式寫進去，然後放到那裡就行了。

最後你需要一個簡單的測試專用(我們將會在下一節中提到 Test )的骨架檔案叫 `test/test_NAME.rb`:

```rb
      require 'test/unit'

class MyUnitTests < Test::Unit::TestCase

  def setup
    puts "setup!"
  end

  def teardown
    puts "teardown!"
  end

  def test_basic
    puts "I RAN!"
  end

end

```

## 安裝 Gems

Gems 是 Ruby 的套件系統，所以你需要知道怎麼安裝它和使用它。不過問題就來了。我的本意是讓這本書越清晰越乾淨越好，不過安裝軟體的方法是在是太多了，如果我要一步一步寫下來，那 10 頁都寫不完，而且告訴你吧，我本來就是個懶人。

所以我不會提供詳細的安裝步驟了，我只會告訴你需要安裝哪些東西，然後讓你自己搞定。這對你也有好處，因為你將打開一個全新的世界，裡邊充滿了其他人發佈的軟體。

接下來你需要安裝下面的軟體套件：

*   git - [`git-scm.com/`](http://git-scm.com/)
*   rake - [`rake.rubyforge.org/`](http://rake.rubyforge.org/)
*   rvm - [`rvm.beginrescueend.com/`](https://rvm.beginrescueend.com/)
*   rubygems - [`rubygems.org/pages/download`](http://rubygems.org/pages/download)
*   bundler - [`gembundler.com/`](http://gembundler.com/)

不要只是手動下載並且安裝這些軟體套件，你應該看一下別人的建議，尤其看看針對你的操作系統別人是怎樣建議你安裝和使用的。同樣的軟體套件在不一樣的操作系統上面的安裝方式是不一樣的，不一樣版本的 Linux 和 OSX 會有不同，而 Windows 更是不同。

我要預先警告你，這個過程會是相當無趣。在業內我們將這種事情叫做「yak shaving(剃犛牛)」。它指的是在你做一件有意義的事情之前的一些準備工作，而這些準備工作又是及其無聊冗繁的。你要做一個很酷的 Ruby 專案，但是創建骨架目錄需要你安裝一些軟體到件，而安裝軟體套件之前你還要安裝 package installer (軟件套件安裝工具)，而要安裝這個工具你還得先學會如何在你的操作系統下安裝軟體，真是煩不勝煩呀。

無論如何，還是克服困難吧。你就把它當做進入程式俱樂部的一個考驗。每個程式設計師都會經歷這條道路，在每一段「酷」的背後總會有一段「煩」的。

## 使用這個骨架

剃犛牛的事情已經做的差不多了，以後每次你要新建一個專案時，只要做下面的事情就可以了：

1.  拷貝這份骨架目錄，把名字改成你新專案的名字。
2.  再將 `NAME`模組和 `NAME.rb` 更名為你需要的名字，它可以是你專案的名字，當然別的名字也行。
3.  編輯你的 `NAME.gemspec` 檔案，讓它包含你新專案的相關資訊。
4.  重命名 `test/test_NAME.rb`，讓它的名字匹配到你模組的名字。
5.  開始寫程式吧。

## 小測驗

這節練習沒有加分習題，不過需要你做一個小測驗：

1.  找文件閱讀，學會使用你前面安裝了的軟體套件。
2.  閱讀關於`NAME.gemspec` 的文件，看它裡邊可以做多少配置。
3.  建立一個專案，在 `NAME.rb` 裡寫一些程式碼。
4.  在 `bin` 目錄下放一個可以運行的腳本，找材料學習一下怎樣建立可以在系統下運行的 Ruby 腳本。
5.  確定你建立的 `bin` 教本，有在 `NAME.gemspec` 中被參照到，這這樣你安裝時就可以連它安裝進去。
6.  使用你的 `NAME.gemspec` 和 `gem build`、`gem install` 來安裝你寫的程式和確定它能用。然後使用`gem uninstall` 去移除它。
7.  弄懂如何使用 Bundler 來自動建立一個骨架目錄。