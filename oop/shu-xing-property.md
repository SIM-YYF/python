# 属性property {#属性property}

### 1. 私有属性添加getter和setter方法 {#1-私有属性添加getter和setter方法}

```
class Money(object):
    def __init__(self):
        self.__money = 0

    def getMoney(self):
        return self.__money

    def setMoney(self, value):
        if isinstance(value, int):
            self.__money = value
        else:
            print("error:不是整型数字")
```



