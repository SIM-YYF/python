# python是动态语言-动态绑定 {#python是动态语言}

```
动态语言： 程序在运行时可以改变其结构的语言
```

### &lt;1&gt;运行的过程中给对象绑定\(添加\)属性 {#2-运行的过程中给对象绑定添加属性}

```
>>> class Person(object):
    def __init__(self, name = None, age = None):
        self.name = name
        self.age = age

>>> P = Person("小明", "24")
>>> P.sex = "male"   # sex属性动态绑定
>>> P.sex
'male'
>>>
```



