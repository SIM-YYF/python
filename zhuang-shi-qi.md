# 装饰器

### 定义

在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）。

### 使用场景\(功能\)：

1. 引入日志
2. 函数执行时间统计
3. 执行函数前预备处理
4. 执行函数后清理功能
5. 权限校验等场景
6. 缓存
7. 用户登录验证机制

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

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc():
        print("%s called at %s"%(func.__name__, ctime()))
        return func()
    return wrappedfunc

@timefun
def foo():
    print("I am foo")
```



