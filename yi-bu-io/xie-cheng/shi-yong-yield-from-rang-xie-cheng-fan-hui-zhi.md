首先：

定义一个求平均值的协程，让它返回一个结果

```
 from collections import namedtuple
      Result = namedtuple('Result', 'count average')
      def averager():
          total = 0.0
          count = 0
          average = None
          while True:
              term = yield
              if term is None:
                    break ➊ 
              total += term
              count += 1
              average = total/count

          return Result(count, average) ➋
    
# 控制台打印      
>>> coro_avg = averager() 
>>> next(coro_avg)
>>> coro_avg.send(10) ➊ 
>>> coro_avg.send(30)
>>> coro_avg.send(6.5)
>>> coro_avg.send(None) ➋ 
Traceback (most recent call last):
            ...
StopIteration: Result(count=3, average=15.5)
```

➊为了返回值，协程必须正常终止;因此，这一版averager中有个条件判断，以便退出 累计循环。

➋返回一个namedtuple，包含count和average两个字段。



