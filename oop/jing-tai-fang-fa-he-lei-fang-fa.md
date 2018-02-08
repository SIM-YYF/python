# 静态方法和类方法 {#静态方法和类方法}

## 1. 类方法 {#1-类方法}

是类对象所拥有的方法，需要用修饰器`@classmethod`来标识其为类方法，对于类方法，第一个参数必须是**类对象**，一般以`cls`作为第一个参数（当然可以用其他名称的变量作为其第一个参数，但是大部分人都习惯以'cls'作为第一个参数的名字，就最好用'cls'了），能够通过实例对象和类对象去访问。

```
class People(object):
    country = 'china'

    #类方法，用classmethod来进行修饰
    @classmethod
    def getCountry(cls):
        return cls.country

p = People()
print p.getCountry()    #可以用过实例对象引用
print People.getCountry()    #可以通过类对象引用
```



