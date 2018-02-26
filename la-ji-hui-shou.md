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

执行f1\(\)会输出这样的结果，而且进程占用的内存基本不会变动。

```
object born,id:0x237cf58
object del,id:0x237cf58
```

`c1=ClassA()`会创建一个对象，放在`0x237cf58`内存中，c1变量指向这个内存，这时候这个内存的引用计数是1。

`del c1`后，c1变量不再指向`0x237cf58`内存，所以这块内存的引用计数减一，等于0，所以就销毁了这个对象，然后释放内存。



#### 导致引用计数+1的情况：

* 对象被创建，例如`a=23`
* 对象被引用，例如`b=a`
* 对象被作为参数，传入到一个函数中，例如`func(a)`
* 对象作为一个元素，存储在容器中，例如`list1=[a,a]`

  




