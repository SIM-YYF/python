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
```

➊为了返回值，协程必须正常终止;因此，这一版averager中有个条件判断，以便退出 累计循环。

➋返回一个namedtuple，包含count和average两个字段。

```
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

➊这一版不产出值。  
➋发送None会终止循环，导致协程结束，返回结果。一如既往，生成器对象会抛出StopIteration异常。异常对象的value属性保存着返回的值。

注意事项：

**return表达式的值会偷偷传给调用方，赋值给StopIteration异常的一个属性。这样做有点不合常理。**

如何获取协程返回的值？

解决： 捕获StopIteration异常，获取averager返回的值

