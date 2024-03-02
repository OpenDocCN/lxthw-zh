# 第二十四章 创建分支

## 24.1 目的

学习如何在仓库中创建本地分支。

是时候重写“hello world”的主要功能了。因为这可能会花一会儿时间，所以你可能想要把这些更改放到一个独立的分支，以便与 master 中的更改隔开。

## 24.2 创建分支

让我们叫新的分支为 `greet`。

```
$ git checkout -b greet
$ git status
```

注意：`git checkout -b <branchname>` 是 `git branch <branchname>` 及 `git checkout <branchname>` 的简写。

注意 `git status` 命令报告你在 `greet` 分支。

## 24.3 更改 Greet：添加 Greeter 类

文件：lib/greeter.rb

```
class Greeter
  def initialize(who)
    @who = who
  end
  def greet
    "Hello, #{@who}"
  end
end
```

```
$ git add lib/greeter.rb
$ git commit -m "Added greeter class"
```

## 24.4 更改 Greet：修改主程序

更新 `hello.rb` 文件来使用 `greeter`。

```
require 'greeter'

# Default is World
name = ARGV.first || "World"

greeter = Greeter.new(name)
puts greeter.greet
```

```
$ git add lib/hello.rb
$ git commit -m "Hello uses Greeter"
```

## 24.5 更改 Greet：更新 Rakefile

更新 `Rakefile` 来使用外部的 Ruby 进程。

```
#!/usr/bin/ruby -wKU

task :default => :run

task :run do
  ruby '-Ilib', 'lib/hello.rb'
end
```

```
$ git add Rakefile
$ git commit -m "Updated Rakefile"
```

## 24.6 下一步

我们现在已经有了包含 3 个新提交的 greet 新分支。接下来我们将学习如何导航及切换分支。