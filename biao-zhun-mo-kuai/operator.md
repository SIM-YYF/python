operator模块为**多个算术运算符提供了对应的函数**，从而避免编写lambda a, b: a\*b这种 平凡的匿名函数。

### operator.mul函数

示例：使用reduce和operator.mul函数计算阶乘

```
from functools import reduce
     from operator import mul
     def fact(n):
         return reduce(mul, range(1, n+1))
```



