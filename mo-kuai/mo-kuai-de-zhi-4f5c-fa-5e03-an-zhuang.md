# 模块制作 {#模块制作}

### &lt;1&gt;定义自己的模块

在Python中，每个Python文件都可以作为一个模块，模块的名字就是文件的名字。

比如有这样一个文件Test.py，在Test.py中定义了函数add

```
    def add(a,b):
        return a+b
```

### &lt;2&gt;调用自己定义的模块

那么在其他文件中就可以先import test，然后通过test.add\(a,b\)来调用了，当然也可以通过from test import add来引入

```
    import Test
    result = Test.add(11,22)
    print(result)
```

## &lt;3&gt;测试模块 {#测试模块}

Test.py: 模块

```
def add(a, b): # 模块中的函数
    return a+b


def main(): # 测试模块中函数是否正确
    ret = add(10, 20)
    print('a+b = %d'%ret)

if __name__ == '__main__': # 测试入口函数。只有开发者进行测试时执行，发布之后，不会执行
    main()
```

## &lt;3&gt;发布模块 {#测试模块}



