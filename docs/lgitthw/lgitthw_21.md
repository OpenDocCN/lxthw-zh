# 第二十一章 再谈结构

## 21.1 目的

添加其它的文件到我们的仓库。

## 21.2 现在添加 Rakefile

让我们添加 `Rakefile` 到我们的仓库。

```
#!/usr/bin/ruby -wKU

task :default => :run

task :run do
  require './lib/hello'
end
```

添加并提交更改。

```
$ git add Rakefile
$ git commit -m "Added a Rakefile."
```

现在你应当能够使用 Rake 来执行 `hello` 程序了。

```
$ rake
```

```
$ rake
Hello, World!
```