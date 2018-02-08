# 异常

### 定义**:**

> 当Python检测到一个错误时，解释器就无法继续执行了，反而出现了一些错误的提示，这就是所谓的"异常"

### 捕获异常

异常捕获格式：

```
try:
    pass # 执行代码块
except expression as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    pass
else: # 没有异常信息
    pass
finally: # 是否有异常，最终都会执行finally语句
    pass
```

### 捕获多个异常

```
try:
     # 执行代码块     
     num = 100/0
except (NameError, ValueError,ZeroDivisionError) as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    print('异常信息:%s'%identifier)
else: # 没有异常信息
     print('未发现异常信息')
finally: # 是否有异常，最终都会执行finally语句
   print('finally')
```

### 全局异常捕获

```
try:
     # 执行代码块     
     num = 100/0
except Exception as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    print('异常信息:%s'%identifier)
else: # 没有异常信息
     print('未发现异常信息')
finally: # 是否有异常，最终都会执行finally语句
   print('finally')
```

### 异常传递

