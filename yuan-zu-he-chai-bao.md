## 元组和拆包

元组其实是对数据的记录:元组中的每个元素都存放了记录中一个字段的数据，外加这个

字段的位置。

#### 把元组用作记录：

```
In [38]: coords = (2,3,-1,10) # 定义元组

In [39]: tras = [item for item in sorted(coords)] # 对元组中的元素排序，生成一个新的列表

In [40]: tras
Out[40]: [-1, 2, 3, 10]
```

#### 元组拆包



元组拆包可以应用到任何可迭代对象上，唯一的硬性要求是，被可迭代对象 中的元素数量必须要跟接受这些元素的元组的空档数一致



```
>>> lax_coordinates = (33.9425, -118.408056)
>>> latitude, longitude = lax_coordinates # 元组拆包 >>> latitude
33.9425
>>> longitude
-118.408056
```



还可以用\*运算符把一个可迭代对象拆开作为函数的参数:

```
     >>> t = (20, 8)
     >>> divmod(*t)
     (2, 4)
     >>> quotient, remainder = divmod(*t)
     >>> quotient, remainder
     (2, 4)
```



