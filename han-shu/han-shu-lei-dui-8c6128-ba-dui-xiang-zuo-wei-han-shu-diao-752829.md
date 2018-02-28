## 用户定义的可调用类型 

不仅Python函数是真正的对象，任何Python对象都可以表现得像函数。为此，只需实现实例方法\_\_call\_\_。  


```
import random
class BingoCage:
     def __init__(self, items): 
          self._items = list(items) ➊ 
          random.shuffle(self._items) ➋
          
     def pick(self): ➌ 
          try:
              return self._items.pop()
          except IndexError:
               raise LookupError('pick from empty BingoCage') ➍ 
               
     def __call__(self): ➎
          return self.pick()
```



