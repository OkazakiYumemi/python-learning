## 5.1. 列表

`append(x)`：在末尾添加一个元素。相当于`a[len(a):] = [x]`

`extend(x)`：用可迭代对象的元素扩展列表。相当于`a[len(a):] = x`。

`insert(i, x)`：在制定位置插入元素，第一个参数为插入元素的索引。

`remove(x)`：从列表中删除第一个值为`x`的元素。未找到时返回`ValueError`异常。

`pop([i])`：删除指定位置的元素并返回，未指定时删除并返回列表的最后一个元素。

*方法签名中`i`两边的方括号表示该参数是可选的，不是要求输入方括号。这种表示法常见于 Python 参考库。*

`clear()`：字面意思。

`index(x[,start[,end]])`：返回列表中第一个值为`x`的元素的`0-based`索引。未找到指定元素时，触发`ValueError`异常。

可选参数`start`和`end`是切片符号，用于将搜索限制为列表的特定子序列。返回的索引是**相对于整个序列的开始计算的**。

`count(x)`：字面意思，返回`x`出现的次数。

`sort(*, key=None, reverse=False)`：就地排序列表中的元素。

未学习：[sorted()](https://docs.python.org/zh-cn/3/library/functions.html#sorted)

`reverse()`：字面意思。

`copy()`：返回列表的**浅拷贝**。相当于`a[:]`。

`insert`、`remove`、`sort`等方法只修改列表，不输出返回值——返回的默认值为`None`。

### 5.1.1. 用列表实现堆栈

有手就行。

### 5.1.2. 用列表实现队列

建议`collections.deque`，这是个双端队列，支持`appendleft`和`popleft`等。

### 5.1.3. 列表推导式

此章节 #important 。

列表推导式创建列表的方式更简洁。

例如创建平方值的列表：

```py
squares = list(map(lambda x: x**2, range(10)))
squares = [x ** 2 for x in range(10)]
```

下面这种方法更加简介与易读。

列表推导式的方括号内包含以下内容：**一个表达式**，后面为一个 for 子句，然后，是零个或多个 for 或 if 子句。

```py
>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
>>> freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
>>> [weapon.strip() for weapon in freshfruit]
['banana', 'loganberry', 'passion fruit']
```

### 5.1.4. 嵌套的列表推导式

列表推导式中的初始表达式可以是任何表达式，甚至可以是另一个列表推导式。

```py
>>> matrix = [
...     [1, 2, 3, 4],
...     [5, 6, 7, 8],
...     [9, 10, 11, 12],
... ]
>>> [[row[i] for row in matrix] for i in range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

比如我们可以转置行列。

当然实际应用中`zip()`用于上述情况效果更为方便简洁。

```py
>>> list(zip(*matrix))
[(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]
```

未学习：[zip()](https://docs.python.org/zh-cn/3/library/functions.html#zip)

### 5.2. del 语句

咕。