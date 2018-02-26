python采用的是`引用计数机制`为主，`标记-清除`和`分代收集`两种机制为辅的垃圾回收策略。



### 引用计数机制

```
class ClassA():
    def __init__(self):
        print 'object born,id:%s'%str(hex(id(self)))
    def __del__(self):
        print 'object del,id:%s'%str(hex(id(self)))

def f1():
   
    c1=ClassA()
    del c1
```



