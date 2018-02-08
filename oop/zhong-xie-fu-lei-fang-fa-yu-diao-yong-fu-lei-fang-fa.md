# 重写父类方法与调用父类方法 {#重写父类方法与调用父类方法}

## 1. 重写父类方法 {#1-重写父类方法}

所谓重写，就是子类中，有一个和父类相同名字的方法，在子类中的方法会覆盖掉父类中同名的方法

```
class Cat(object):
    def sayHello(self):
        print("halou-----1")


class Bosi(Cat):

    def sayHello(self):
        print("halou-----2")

bosi = Bosi()

bosi.sayHello()

```



