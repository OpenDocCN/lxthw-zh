## 练习 26：字典和模块

在这个练习中，你将探索`dict`如何与模块一起工作。每当你使用`import`将“功能”添加到你自己的 Python 源代码时，你都在使用模块。你在练习 17 中使用得最多，所以在开始这个练习之前，最好回顾一下那个练习。

### 步骤 1: `import`的回顾

第一步是回顾`import`的工作方式并进一步发展这方面的知识。花点时间将这段代码输入到一个名为`ex26.py`的 Python 文件中。你可以在 Jupyter 中通过创建一个文件（左侧，蓝色`[+]`按钮）来做到这一点：

列表 26.1: ex26.py

```py
1   name = "Zed"
2   height = 74
```

创建了这个文件后，你可以用这个导入它：

列表 26.2: ex26_code.py

```py
1   **import** ex26
```

这将把`ex26.py`的内容带入你的 Jupyter lab 中，这样你就可以像这样访问它们：

列表 26.3: ex26_code.py

```py
1   print("name", ex26.name)
2   print("height", ex26.height)
```

尽可能多地尝试玩这个。尝试添加新变量并再次导入以查看其工作原理。

### 步骤 2: 找到`__dict__`

一旦你理解了`import`是将`ex26.py`的内容导入到你的 lab 中，你就可以开始像这样调查`__dict__`变量：

列表 26.4: ex26_code.py

```py
1   **from** pprint **import** pprint
2
3   pprint**(**ex26.**__dict__)**
```

`pprint`函数是一个“漂亮打印机”，将以更好的格式打印`__dict__`。

使用`pprint`，你会突然发现`ex26`有一个名为`__dict__`的“隐藏”变量，它*实际上*是一个包含模块中所有内容的`dict`。你会在 Python 中的各个地方找到这个`__dict__`和许多其他秘密变量。`__dict__`的内容包含了许多不是你的代码的东西，但这只是 Python 需要处理模块的东西。

这些变量是如此隐藏，以至于即使顶级专业人员也会忘记它们的存在。许多这样的程序员认为模块与`dict`*完全*不同，而实际上模块使用了`__dict__`，这意味着它*与*`dict`相同。唯一的区别是 Python 有一些语法，让你使用`.`运算符而不是`dict`语法来访问模块，但你*仍然*可以像访问`dict`一样访问内容：

列表 26.5: ex26_code.py

```py
1   print("height is", ex26.height)
2   print("height is also", ex26\. dict ['height'])
```

对于这两种语法，你会得到相同的输出，但`.`模块语法肯定更容易。

### 步骤 3: 改变`__dict__`

如果一个模块确实是内部的`dict`，那么这意味着改变`__dict__`的内容也应该改变模块中的变量。让我们试一试：

列表 26.6: ex26_code.py

```py
1   print(f"I am currently {ex26.height} inches tall.")
2
3   ex26\. dict ['height'] = 1000
4   print(f"I am now {ex26.height} inches tall.")
5
6   ex26.height = 12
7   print(f"Oops, now I'm {ex26\. dict ['height']} inches tall.")
```

正如你所看到的，当你改变`ex26.__dict__['height']`时，变量`ex26.height`也会改变，这证明了模块确实是`__dict__`。

这意味着`.`运算符被转换为`__dict__[]`访问操作。我希望你记住这一点，因为很多初学者看到`ex26.height`时，他们认为这是一个单独的代码单元。实际上，这实际上是三个或四个单独的操作：

1.  找到`ex26`。

2.  找到`ex26.__dict__`。

3.  使用`"height"`索引到`__dict__`。

4.  返回该值。

一旦你建立了这种联系，你就会开始理解`.`是如何工作的。

### 学习练习：找到“Dunders”

`__dict__` 变量通常被称为“双下划线”变量，但程序员们很懒，所以我们只是称它们为“dunder 变量”。在学习关于 dunder 变量的最后一步中，你将访问 Python 文档中描述数据模型的部分，其中描述了许多这些 dunder 的用法。

这是一个很大的文档，其写作风格非常枯燥，所以最好的学习方法是搜索`__`（双下划线），然后根据其描述找到访问这个变量的方法。例如，你可以尝试在几乎任何地方访问`__doc__`：

列表 26.7: ex26_code.py

```py
1   **from** pprint **import** pprint
2   print(pprint. doc )
```

这将为你提供与`pprint`函数相关联的一点文档。你可以使用`help`函数访问相同的信息：

列表 26.8: ex26_code.py

```py
1   **help(**pprint)
```

尝试用你能找到的所有其他 dunder 进行这些实验。你很可能不会直接使用它们，但了解 Python 内部工作原理是很有好处的。
