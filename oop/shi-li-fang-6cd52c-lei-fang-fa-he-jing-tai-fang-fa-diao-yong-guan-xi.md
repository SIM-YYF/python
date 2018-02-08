# 实例方法,类方法和静态方法调用关系

调用关系：

1. 在实例方法中，可以通过self调用静态方法和类方法
2. 在类方法中，可以通过cls调用静态方法，但不可以调用实例方法
3. 在静态方法中，通过类对象调用类方法，但不可以调用实例方法

```
class Person(object):
    number = 100

    def func_instance_methon(self):
        print('实例方法')
        # self.func_static_method() # 在实例方法中调用静态方法
        # self.func_class_method() # 在实例方法中调用类方法

    @staticmethod
    def func_static_method():
        print('静态方法')
        Person.func_class_method() # 在静态方法中，通过类对象调用类方法

    @classmethod
    def func_class_method(cls):
        print('类方法')
        cls.func_static_method() # 在类方法中，通过cls调用静态方法

person = Person()
person.func_instance_methon()
person.func_class_method()
person.func_static_method()
```



