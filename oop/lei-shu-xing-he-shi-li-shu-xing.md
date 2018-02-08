# 类属性、实例属性 {#类属性、实例属性}

在前面的例子中我们接触到的就是实例属性（对象属性），顾名思义，类属性就是`类对象`所拥有的属性，它被所有`类对象`的`实例对象`所共有，在内存中只存在一个副本，这个和C++中类的静态成员变量有点类似。对于公有的类属性，在类外可以通过`类对象`和`实例对象`访问

## 类属性 {#类属性}

```
class People(object):
    name = 'Tom'  #公有的类属性
    __age = 12     #私有的类属性

p = People()

print(p.name)           #正确
print(People.name)      #正确
print(p.__age)            #错误，不能在类外通过实例对象访问私有的类属性
print(People.__age)        #错误，不能在类外通过类对象访问私有的类属性
```

## 实例属性\(对象属性\) {#实例属性对象属性}

```
class People(object):
    address = '山东' #类属性
    def __init__(self):
        self.name = 'xiaowang' #实例属性
        self.age = 20 #实例属性

p = People()
p.age =12 #实例属性
print(p.address) #正确
print(p.name)    #正确
print(p.age)     #正确

print(People.address) #正确
print(People.name)    #错误
print(People.age)     #错误
```



