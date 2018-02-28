operator模块为**多个算术运算符提供了对应的函数**，从而避免编写lambda a, b: a\*b这种 平凡的匿名函数。

### operator.mul函数

示例：使用reduce和operator.mul函数计算阶乘

```
from functools import reduce
     from operator import mul
     def fact(n):
         return reduce(mul, range(1, n+1))
```

使用reduce函数和一个匿名函数计算阶乘：

```
from functools import reduce
def fact(n):
         return reduce(lambda a, b: a*b, range(1, n+1))
```

### operator.itemgetter函数

operator.itemgetter函数：能够从序列中取出元素。

itemgetter的常见用途:根据元组的某个字段给元组列表排序。

示例：使用itemgetter排序一个元组列表：

```
     >>> metro_data = [
     ...     ('Tokyo', 'JP', 36.933, (35.689722, 139.691667)),
     ...     ('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889)),
     ...     ('Mexico City', 'MX', 20.142, (19.433333, -99.133333)),
     ...     ('New York-Newark', 'US', 20.104, (40.808611, -74.020386)),
     ...     ('Sao Paulo', 'BR', 19.649, (-23.547778, -46.635833)),
     ... ]
     >>>
     >>> from operator import itemgetter
     >>> for city in sorted(metro_data, key=itemgetter(1)):
     ...     print(city)
     ...
     ('Sao Paulo', 'BR', 19.649, (-23.547778, -46.635833))
     ('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889))
     ('Tokyo', 'JP', 36.933, (35.689722, 139.691667))
     ('Mexico City', 'MX', 20.142, (19.433333, -99.133333))
     ('New York-Newark', 'US', 20.104, (40.808611, -74.020386))
```

在这个示 例中，按照国家代码\(第2个字段\)的顺序打印各个城市的信息。

其实，itemgetter\(1\)的 作用与lambda fields: fields\[1\]一样:创建一个接受集合的函数，返回索引位1上的元 素。

如果把多个参数传给itemgetter，它构建的函数会返回提取的值构成的元组:

```
     >>> cc_name = itemgetter(1, 0)
     >>> for city in metro_data:
     ...     print(cc_name(city))
     ...
     ('JP', 'Tokyo')
     ('IN', 'Delhi NCR')
     ('MX', 'Mexico City')
     ('US', 'New York-Newark')
     ('BR', 'Sao Paulo')
     >>>
```

### operator.attrgetter函数

attrgetter与itemgetter作用类似，它创建的函数根据名称提取对象的属性。

如果把 多个属性名传给attrgetter，它也会返回提取的值构成的元组。

