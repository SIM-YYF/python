# python是动态语言-动态绑定 {#python是动态语言}

```
动态语言： 程序在运行时可以改变其结构的语言
```

### &lt;1&gt;运行的过程中给类绑定\(添加\)`实例`属性 {#2-运行的过程中给对象绑定添加属性}

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

### &lt;2&gt;运行的过程中给类绑定\(添加\)`类`属性 {#3-运行的过程中给类绑定添加属性}

```
>>> class Person(object):
    def __init__(self, name = None, age = None):
        self.name = name
        self.age = age

>>>> Person.sex = None #给类Person添加一个属性
>>> P1 = Person("小丽", "25")
>>> print(P1.sex) #如果P1这个实例对象中没有sex属性的话，那么就会访问它的类属性
None #可以看到没有出现异常
>>>
```

### &lt;3&gt;运行的过程中给类绑定\(添加\)&lt;实例/静态/类&gt;方法 {#4-运行的过程中给类绑定添加方法}



