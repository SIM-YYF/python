### OrderedDict

OrderedDict：是collections模块提供的。

使用`dict`时，Key是无序的。在对`dict`做迭代时，我们无法确定Key的顺序。

如果要保持Key的顺序，可以用`OrderedDict`：

```
>>> from collections import OrderedDict
>>> d = dict([('a', 1), ('b', 2), ('c', 3)])
>>> d # dict的Key是无序的
{'a': 1, 'c': 3, 'b': 2}
>>> od = OrderedDict([('a', 1), ('b', 2), ('c', 3)])
>>> od # OrderedDict的Key是有序的
OrderedDict([('a', 1), ('b', 2), ('c', 3)])
```

注意，`OrderedDict`的Key会按照插入的顺序排列，不是Key本身排序：

