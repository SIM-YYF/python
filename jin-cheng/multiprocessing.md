由于Python是跨平台的，自然也应该提供一个跨平台的多进程支持。multiprocessing模块就是跨平台版本的多进程模块。

multiprocessing模块提供了一个Process类来代表一个进程对象，下面的例子就是启动一个子进程并等待其结束：

```
#coding=utf-8
from multiprocessing import Process
import os

# 子进程要执行的代码
def run_proc(name):
    print('子进程运行中，name= %s ,pid=%d...' % (name, os.getpid()))

if __name__=='__main__':
    print('父进程 %d.' % os.getpid())
    p = Process(target=run_proc, args=('test',))
    print('子进程将要执行')
    p.start()
    p.join()
    print('子进程已结束'
```

## 说明 {#说明}

* 创建子进程时，只需要传入一个执行函数和函数的参数，创建一个Process实例，用start\(\)方法启动，这样创建进程比fork\(\)还要简单。
* join\(\)方法可以等待子进程结束后再继续往下运行，通常用于进程间的同步。



