# 类的私有属性和方法的定义

```
class Animal(object):

    def __init__(self, name='动物', color='白色'):
        self.__name = name # 私有属性
        self.color = color

    def __test(self): # 私有方法
        print(self.__name)
        print(self.color)

    def test(self):
        print(self.__name)
        print(self.color)
```

注意事项：

**私有属性和方法，不可以通过对象来访问，否则会报错**

