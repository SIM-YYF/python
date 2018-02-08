# 类的概念

类：

```
将具有共同特征和行为的一组对象抽象定义。
具有相同属性和行为事物的统称
```

# 定义类

```
# 定义类
class Car(object):
    # 方法
    def getCarInfo(self):
        print('车轮子个数:%d, 颜色%s'%(self.wheelNum, self.color))

    def move(self):
        print("车正在移动...")
```

#### 说明： {#说明：}

* 定义类时有2种：新式类和经典类，上面的Car为经典类，如果是Car\(object\)则为新式类
* 类名 的命名规则按照"大驼峰"



# 对象概念



