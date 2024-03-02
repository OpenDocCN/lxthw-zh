# 第三十章 解决冲突

## 30.1 目的

学习如何在合并时处理冲突。

## 30.2 合并 master 到 greet

现在回到 greet 分支，并尝试合并新的 master。

```
$ git checkout greet
$ git merge master
```

```
$ git checkout greet
Switched to branch 'greet'
$ git merge master
Auto-merging lib/hello.rb
CONFLICT (content): Merge conflict in lib/hello.rb
Automatic merge failed; fix conflicts and then commit the result.
```

如果你打开 `lib/hello.rb`，那么你将看到：

```
<<<<<<< HEAD
require 'greeter'

# Default is World
name = ARGV.first || "World"

greeter = Greeter.new(name)
puts greeter.greet
=======
# Default is World

puts "What's your name"
my_name = gets.strip

puts "Hello, #{my_name}!"
>>>>>>> master
```

第一部分是当前分支（greet）头的版本。第二部分是 master 分支的版本。

## 30.3 修复冲突

你需要手动解决冲突。根据下列内容来修改 `lib/hello.rb`。

```
require 'greeter'

puts "What's your name"
my_name = gets.strip

greeter = Greeter.new(my_name)
puts greeter.greet
```

## 30.4 提交冲突解决

```
$ git add lib/hello.rb
$ git commit -m "Merged master fixed conflict."
```

```
$ git add lib/hello.rb
$ git commit -m "Merged master fixed conflict."
Recorded resolution for 'lib/hello.rb'.
[greet 25f0e8c] Merged master fixed conflict.
```

## 30.5 高级合并

Git 没有提供任何图形化的合并工具，但如果你想要使用第三方合并工具来处理，它将十分乐意。参阅 [`onestepback.org/index.cgi/Tech/Git/UsingP4MergeWithGit.red`](http://onestepback.org/index.cgi/Tech/Git/UsingP4MergeWithGit.red) 了解 Git 使用 Perforce 合并工具的说明。