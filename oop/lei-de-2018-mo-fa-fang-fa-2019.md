# 常见类的魔法方法

## `__init__()`

作用：

### &lt;1&gt;使用方式

```
def 类名:
    #初始化函数，用来完成一些默认的设定
    def __init__():
        pass
```

### &lt;2&gt;`__init__()`方法的调用

```
# 定义汽车类
class Car:

    def __init__(self):
        self.wheelNum = 4
        self.color = '蓝色'

    def move(self):
        print('车在跑，目标:夏威夷')

# 创建对象
BMW = Car()

print('车的颜色为:%s'%BMW.color)
print('车轮胎数量为:%d'%BMW.wheelNum)
```



