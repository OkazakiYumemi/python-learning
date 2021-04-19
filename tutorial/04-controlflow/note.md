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

函数内的第一条语句是字符串时，该字符串就是文档字符串，见`4.7.`

没有`return`语句的函数也返回值，为`None`。（疑问：是不是意味着 Python 没有「过程」只有「函数」？）

## 4.7. 函数定义详解

此章节 #important 。

### 4.7.1. 默认值参数

```py
i = 5
def f(a = i):
    print(a)

i = 6
f()
```

注意**默认值只计算一次。**所以上例输出为`5`。

默认值为列表、字典或类实例等可变对象时，会产生与该规则不同的结果。

```py
def f(a, L=[]):
    L.append(a)
    return L
print(f(1))
print(f(2))
print(f(3))
```

输出如下：

```plain
[1]
[1, 2]
[1, 2, 3]
```

不想在后续调用之间共享默认值时，应以如下方式编写函数：

```py
def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L
print(f(1))
print(f(2))
print(f(3))
```

### 4.7.2. 关键字参数

**函数调用时，关键字参数必须跟在位置参数后面。关键字参数的顺序并不重要。不能对同一个参数多次赋值。**

例如，下面的调用是失败的（`TypeError`）：

```py
def f(a): pass
f(0, a = 0)
```

### 4.7.3. 特殊参数

此章节 #important。

```py
def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
    pass
```

`/`与`*`是可选的，`/`前的参数**不能按关键字传递**，`*`后的参数**不能按位置传递**。
若未出现，则认为`*`在所有参数之前，`/`在所有参数之后。

下面的函数定义中，`kwds`把`name`当作键，因此，可能与位置参数`name`产生潜在冲突：

```py
def foo(name, **kwds):
    return 'name' in kwds
```

调用该函数不可能返回`True`，因为关键字 'name' 总与第一个形参绑定。

例如，尝试调用`foo(1, **{'name': 2})`（或者`foo(1, name = 2)`）会调用失败（`TypeError`）。

加上`/`后，就可以了。此时`'name'`也可以作为关键字参数的键。

```py
def foo(name, /, **kwds):
    return 'name' in kwds

print(foo(1, **{'name': 2}))
print(foo(1, name = 2))
```

运行上述代码将输出两个`True`。

换句话说，仅限位置形参的名称可以在`**kwds`中使用，而不产生歧义。

### 4.7.4. 任意实参列表

使用任意数量的实参比较少见，这些实参将包含在元组中。

实参之前可能有若干个普通参数。

```py
def f(a, *b):
    print(b)
f(1, 2, 3)
f(1, *(2, 3))
f(1, b = (2, 3))
```

此时需要注意的是，第三个调用将失败（`TypeError`）。即，任意实参列表不能作为关键字参数。
前两个调用均将输出`(2, 3)`。

```py
def f(*a, b):
    print(a)
f(1, 2, 3)
f(2, 3, b = 1)
f(b = 1, *(2, 3))
f(b = 1, 2, 3)
```
注意`*a`后的所有参数都为关键字参数，故仅有第二和第三个调用是成功的，第一个返回`TypeError`，第四个返回`SyntaxError`。

咕。