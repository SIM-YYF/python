# 匿名函数 {#匿名函数}

## 定义和基本使用

用lambda关键词能创建小型匿名函数。这种函数得名于省略了用def声明函数的标准步骤。

lambda函数的语法只包含一个语句，如下：

```
lambda [arg1 [,arg2,.....argn]]:expression
```

如下实例：

```
    sum = lambda arg1, arg2: arg1 + arg2
    #调用sum函数
    print "Value of total : ", sum( 10, 20 )
    print "Value of total : ", sum( 20, 20 )
```

注意事项：

**Lambda函数能接收任何数量的参数但只能返回一个表达式的值**

## 应用场景

#### 匿名函数作为参数传递

```
>>> def fun(a, b, opt):
...     print "a =", a
...     print "b =", b
...     print "result =", opt(a, b)
...
>>> fun(1, 2, lambda x,y:x+y) # 匿名函数作为参数传递
a = 1
b = 2
result = 3
```



### 使用匿名函数对复杂数据结构排序





