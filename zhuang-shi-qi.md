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



