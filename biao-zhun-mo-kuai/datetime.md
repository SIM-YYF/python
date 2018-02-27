datetime是Python处理日期和时间的标准库。

### 获取当前日期和时间

我们先看如何获取当前日期和时间

```
>>> from datetime import datetime
>>> now = datetime.now() # 获取当前datetime
>>> print(now)
2015-05-18 16:28:07.198690
>>> print(type(now))
<class 'datetime.datetime'>
```

`datetime.now()`返回当前日期和时间，其类型是`datetime`。

