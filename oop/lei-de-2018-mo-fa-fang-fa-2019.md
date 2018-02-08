# 常见类的魔法方法

## &lt;1&gt;  `__init__()方法`

特征和作用：

* `__init__(self)`方法，在创建一个对象时默认被调用，不需要手动调用
* `__init__(self)`中，默认有1个参数名字为self，如果在创建对象时传递了2个实参，那么`__init__(self)`中出了self作为第一个形参外还需要2个形参，例如`__init__(self,x,y)`
* `__init__(self)`中的self参数，不需要开发者传递，python解释器会自动把当前的对象引用传递进去

### 使用方式

```
def 类名:
    #初始化函数，用来完成一些默认的设定
    def __init__():
        pass
```

### `__init__()`方法的调用

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



