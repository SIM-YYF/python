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
...   yield from 'AB' # yield from 后面链接的是可迭代对象
...   yield from range(1, 3) # yield from 后面链接的是可迭代对象

...
>>> list(gen())
['A', 'B', 1, 2]
```

强调：

```
yield from 后面链接的是可迭代对象
```

使用yield from链接可迭代的对象：

```
     >>> def chain(*iterables):
     ...     for it in iterables:
     ...         yield from it # ’ABC‘ 和 （0,1,2）两个可迭代对象
     ...
     >>> s = 'ABC'
     >>> t = tuple(range(3))
     >>> list(chain(s, t))
     ['A', 'B', 'C', 0, 1, 2]
```

##### yield from 后面链接不仅可以是可迭代对象，同时可以是可迭代的生成器函数。

##### 因此，yield from 大致的语言结构为：

![](/assets/Snip20180228_2.png)

委派生成器在yield from表达式处暂停时，调用方可以直接把数据发给子生成器，子生成 器再把产出的值发给调用方。子生成器返回之后，解释器会抛出StopIteration异常，并 把返回值附加到异常对象上，此时委派生成器会恢复。

```
from collections import namedtuple

Result = namedtuple('Result', 'count average')
# 子生成器
def averager(): ➊
         total = 0.0
         count = 0
         average = None
         while True:
            term = yield ➋
            if term is None: ➌
                 break
             total += term
             count += 1
             average = total/count

        return Result(count, average) ➍
        
        
# 委派生成器
def grouper(results, key): ➎
    while True: ➏
        results[key] = yield from averager() ➐
        
        
# 客户端代码，即调用方 
def main(data): ➑
     results = {}
     for key, values in data.items():
            group = grouper(results, key) ➒ 
            next(group) ➓
            for value in values:
                group.send(value) group.send(None) # 重要!
                
    # print(results) # 如果要调试，去掉注释 

    
    
data = {
         'girls;kg':
             [40.9, 38.5, 44.3, 42.2, 45.2, 41.7, 44.5, 38.0, 40.6, 44.5],
         'girls;m':
             [1.6, 1.51, 1.4, 1.3, 1.41, 1.39, 1.33, 1.46, 1.45, 1.43],
         'boys;kg':
             [39.0, 40.8, 43.2, 40.8, 43.1, 38.6, 41.4, 40.6, 36.3],
         'boys;m':
             [1.38, 1.5, 1.32, 1.25, 1.37, 1.48, 1.25, 1.49, 1.46],
}

if __name__ == '__main__':
         main(data)
```













