# 装饰器

#### 定义

在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）。

#### 使用场景\(功能\)：

1. 引入日志
2. 函数执行时间统计
3. 执行函数前预备处理
4. 执行函数后清理功能
5. 权限校验等场景
6. 缓存
7. 用户登录验证机制

#### 装饰器分类：

1. 函数装饰器
2. 类装饰器



## 函数装饰器

### &lt;1&gt; 被装饰的有参函数 {#例2被装饰的函数有参数}

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc(a, b):
        print("%s called at %s"%(func.__name__, ctime()))
        print(a, b)
        func(a, b)
    return wrappedfunc

@timefun
def foo(a, b):
    print(a+b)

foo(3,5)
```

强调：装饰器的调用过程：

```
foo = timefun(foo)
#foo函数先作为实参赋值给timefun函数的func后。
#foo变量接收指向timefun函数返回的wrappedfunc
foo()
#调用foo(),即等价调用wrappedfunc()
#内部函数wrappedfunc被引用，所以外部函数的func变量(自由变量)并没有释放
#func里保存的是原foo函数对象
```

### &lt;2&gt; 被装饰的不定长参数函数 {#例2被装饰的函数有参数}

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc(*args, **kwargs):
        print("%s called at %s"%(func.__name__, ctime()))
        func(*args, **kwargs)
    return wrappedfunc

@timefun
def foo(a, b, c):
    print(a+b+c)

foo(3,5,7)
```

### &lt;3&gt;装饰器中的return {#例4装饰器中的return}

装饰器\(内部函数\),没有使用return 返回函数：

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc():
        print("%s called at %s"%(func.__name__, ctime()))
        func()
    return wrappedfunc

@timefun
def getInfo():
    return '----hahah---'


print(getInfo()) # 调用被装饰的函数
```

打印结果：

```
getInfo called at Fri Nov  4 21:55:37 2016
None  # 如果没有return 并不会打印出内容
```

装饰器\(内部函数\),使用`return func()` 返回函数：

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc():
        print("%s called at %s"%(func.__name__, ctime()))
        return func()
    return wrappedfunc

@timefun
def getInfo():
    return '----hahah---'

print(getInfo()) # 调用被装饰的函数
```

打印结果：

```
getInfo called at Fri Nov  4 21:55:59 2016
----hahah---   #修改装饰器为return func()，就可以打印出相应的内容
```

#### 总结： {#总结：}

* 一般情况下为了让装饰器更通用，可以有return

### &lt;3&gt;含有参数的装饰器 {#例4装饰器中的return}

```
from time import ctime, sleep

def timefun_arg(pre="hello"):
    def timefun(func):
        def wrappedfunc():
            print("%s called at %s %s"%(func.__name__, ctime(), pre))
            return func()
        return wrappedfunc
    return timefun

@timefun_arg("python")
def too():
    print("I am too")

foo() # 调用(可以理解为：foo()==timefun_arg("python")(foo)())
```

## 类装饰器



