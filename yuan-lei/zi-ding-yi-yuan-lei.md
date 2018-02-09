# 自定义元类

如果在创建一个类时，想要用自动地改变类或希望可以创建符合当前上下文的类，可以在定义一个类的时候为其添加\_\_metaclass\_\_属性。在内存中类创建的过程中，Python会在类的定义中寻找\_\_metaclass\_\_属性，如果找到了，Python就会用它来创建类Foo，如果没有找到，就会用内建的type来创建这个类。这样的过程就是使用自定义元类来创建类。

举例：

```
你决定在你的模块里所有的类的属性都应该是大写形式，可以通过在模块级别设定__metaclass__。
采用这种方法，这个模块中的所有类都会通过这个元类来创建，我们只需要告诉元类把所有的属性都改成大写形式就万事大吉了。
```

代码如下：

```
def upper_attr(future_class_name, future_class_parents, future_class_attr):
    #遍历属性字典，把不是__开头的属性名字变为大写
    newAttr = {}
    for name,value in future_class_attr.items():
        if not name.startswith("__"):
            newAttr[name.upper()] = value

    #调用type来创建一个类
    return type(future_class_name, future_class_parents, newAttr)

class Foo(object, metaclass=upper_attr): # 在定义的类中添加自定义元类
    bar = 'bip'

print(hasattr(Foo, 'bar'))
print(hasattr(Foo, 'BAR'))

f = Foo()
print(f.BAR)
```



