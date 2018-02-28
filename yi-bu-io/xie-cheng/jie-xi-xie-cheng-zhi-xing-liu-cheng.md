## 产出两个值的协程



```
>>> def simple_coro2(a):
     ...     print('-> Started: a =', a)
... b = yield a
     ...     print('-> Received: b =', b)
     ...     c = yield a + b
     ...     print('-> Received: c =', c)
     ...
     >>> my_coro2 = simple_coro2(14)
     >>> from inspect import getgeneratorstate
>>> getgeneratorstate(my_coro2) ➊ 'GEN_CREATED'
>>> next(my_coro2) ➋
-> Started: a = 14
14
>>> getgeneratorstate(my_coro2) ➌ 'GEN_SUSPENDED'
>>> my_coro2.send(28) ➍
-> Received: b = 28
42
>>> my_coro2.send(99) ➎
-> Received: c = 99
Traceback (most recent call last):
File "<stdin>", line 1, in <module> StopIteration
>>> getgeneratorstate(my_coro2) ➏ 'GEN_CLOSED'
```



