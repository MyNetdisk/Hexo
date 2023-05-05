---
title: Python 内置函数的分类和一些示例
date: 2023-05-05
categories:
  - Python
tags:
  - Python
---

## 这是 Python 内置函数的分类和一些示例：

### 数学相关

- abs(x)：返回 x 的绝对值
- divmod(x, y)：返回 x 除以 y 的商和余数
- pow(x, y[, z])：返回 x 的 y 次幂，如果指定了 z，则在求幂之前对结果取模
- round(number[, ndigits])：将 number 四舍五入到 ndigits 个小数位（默认为 0）
- min(iterable, \_[, key, default])：返回 iterable 中的最小值，可选地使用 key 函数和 default 值
- max(iterable, \_[, key, default])：返回 iterable 中的最大值，可选地使用 key 函数和 default 值
- sum(iterable[, start])：返回 iterable 中的所有元素的总和，可选地指定起始值 start

### 序列相关

- len(s)：返回序列 s 的长度
- range([start], stop[, step])：返回从 start 到 stop（不包括 stop）的整数序列，可选地指定步长 step
- next(iterator[, default])：返回迭代器 iterator 的下一项，如果没有更多项并且没有指定 default 值，则引发 StopIteration 异常
- filter(function, iterable)：返回一个迭代器，其中包含 iterable 中所有使 function 返回 True 的元素
- map(function, \_iterables)：返回一个迭代器，其中包含调用 function 函数并传递 iterables 中相应项作为参数所返回的结果
- sorted(iterable, \_, key=None, reverse=False)：返回一个排序后的可迭代对象，可选地指定 key 函数和 reverse 标志
- slice(stop)、slice(start, stop[, step])：返回一个切片对象，使用给定的 start、stop 和 step（可选）参数来切片序列
- reversed(seq)：返回一个反向迭代器，其中包含 seq 中所有元素的相反顺序

### 类型转换

- chr(i)：将整数 i 转换为对应的 Unicode 字符
- ord(c)：返回表示 Unicode 字符 c 的整数
- str(object='')：将对象转换为字符串。如果未提供任何值，则返回空字符串。
- bool([x])：将 x 转换为布尔值 True 或 False。如果 x 未提供，则返回 False。
- int(x=0)：将 x 转换为整数。如果 x 是字符串，则必须是表示整数的有效字符串。
- float(x=0)：将 x 转换为浮点数。如果 x 是字符串，则必须是表示浮点数的有效字符串。
- complex(real, imag=0)：返回具有实部 real 和虚部 imag 的复数。
- bin(x)：将整数 x 转换为二进制字符串
- oct(x)：将整数 x 转换为八进制字符串
- hex(x)：将整数 x 转换为十六进制字符串

### 数据结构

- dict()：创建一个新字典
- list()：创建一个新列表
- set()：创建一个新集合
- tuple()：创建一个新元组

### 其他函数

- all(iterable)：如果 iterable 中所有元素都为 True（或空迭代器），则返回 True；否则返回 False。
- any(iterable)：如果 iterable 中任何元素为 True，则返回 True；否则返回 False。
- id(object)：返回对象 object 的唯一标识符（整数）
- input([prompt])：读取用户输入作为字符串
- open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)：打开文件并返回文件对象
- print(\*objects, sep=' ', end='\n', file=sys.stdout, flush=False)：将对象输出到控制台
- type(object)：返回对象的类型。如果不提供参数，则返回 type 本身。

### 关于本文

> 作者：ChatGPT
>
> 本文链接：ChatGPT
