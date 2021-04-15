## 4.1. if 语句

`elif`是`else if`的缩写。

Python 没有`switch`或`case`。

## 4.2. for 语句

只迭代列表或字符串等任意序列。

最好不要在迭代时对该序列进行操作。

## 4.3. range() 函数

未学习：[enumerate()](https://docs.python.org/zh-cn/3/tutorial/datastructures.html#tut-loopidioms)

`range()`是可迭代对象，基于所需序列返回连续项，并不生成真正的列表，节省空间。

因此使用`print(range(1145141919810))`不会爆空间，但是`list(range(1145141919810))`会
！

## 4.4. 循环中的 break、continue 语句及 else 字句

循环语句的`else`在`for`循环中可迭代对象的元素全都循环完毕，或`while`循环的条件为假时，执行该字句；`break`语句终止循环时，不执行该字句。

未学习：[try 语句和异常](https://docs.python.org/zh-cn/3/tutorial/errors.html#tut-handling)

## 4.5. pass 语句

`pass`语句不执行任何操作。

最小的类：#trick

```py
class C:
    pass
```

## 4.6. 定义函数

咕。