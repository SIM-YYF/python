#### 获取返回值第一种方式：捕获StopIteration异常，获取averager返回的值

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

```
     >>> coro_avg = averager()
     >>> next(coro_avg)
     >>> coro_avg.send(10)
     >>> coro_avg.send(30)
     >>> coro_avg.send(6.5)
     >>> try:
     ...     coro_avg.send(None)
     ... except StopIteration as exc: # 捕获异常
     ...     result = exc.value # 获取返回结果
     ...
     >>> result
     Result(count=3, average=15.5)
```

通过捕获StopIteration异常，最终获取了协程了返回值。

除了以上方式，python提供了yield from结构会在内部自动捕获StopIteration异常，并返回值。

#### 使用yield from结构获取返回值

yield from是全新的语言结构，yield from可用于简化for循环中的yield表达式。

比如：

```
>>> def gen():
...   for c in 'AB':
          yield c
      for i in range(1,3):
          yield i
...
>>> list(gen())
['A', 'B', 1, 2]

# 可以改写为:

>>> def gen():
...   yield from 'AB'
...   yield from range(1, 3)
...
>>> list(gen())
['A', 'B', 1, 2]
```



