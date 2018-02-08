# 单继承

定义：子类只能继承一个父类

如：

```
# 定义一个父类，如下:
class Cat(object):

    def __init__(self, name, color="白色"):
        self.name = name
        self.color = color

    def run(self):
        print("%s--在跑"%self.name)

# 定义一个子类，继承Cat类如下:
class Bosi(Cat):

    def setNewName(self, newName):
        self.name = newName

    def eat(self):
        print("%s--在吃"%self.name)
```

#### 总结 {#总结}

* 子类在继承的时候，在定义类时，小括号\(\)中为父类的名字
* 父类的属性、方法，会被继承给子类



