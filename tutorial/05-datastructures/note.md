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

