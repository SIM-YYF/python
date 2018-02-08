# 匿名函数 {#匿名函数}

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



