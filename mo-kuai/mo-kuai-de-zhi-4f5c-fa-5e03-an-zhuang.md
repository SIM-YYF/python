# 模块制作 {#模块制作}

### &lt;1&gt;定义自己的模块

在Python中，每个Python文件都可以作为一个模块，模块的名字就是文件的名字。

比如有这样一个文件test.py，在test.py中定义了函数add

```
    def add(a,b):
        return a+b
```

### &lt;2&gt;调用自己定义的模块

那么在其他文件中就可以先import test，然后通过test.add\(a,b\)来调用了，当然也可以通过from test import add来引入

```
    import test
    result = test.add(11,22)
    print(result)
```



