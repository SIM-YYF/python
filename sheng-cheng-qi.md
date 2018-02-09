# 生成器

列表元素可以按照某种算法推算出来，并且可以在循环的过程中不断推算出后续的元素，这种一边循环一边计算的机制，称为生成器：generator。

### &lt;1&gt; 创建生成器\( \[ \] 改为 \(\) \)

```
>>> L = [x * x for x in range(10)] # 列表
>>> L
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> g = (x * x for x in range(10))  # 生成器
>>> g
<generator object <genexpr> at 0x1022ef630>
```

以上创建的生成器，需要通过next\(\)方法，来获取每个元素。

如：

```
>>> next(g)
0
>>> next(g)
1
>>> next(g)
4
>>> next(g)
9
>>> next(g)
16
>>> next(g)
25
>>> next(g)
36
>>> next(g)
49
>>> next(g)
64
>>> next(g)
81
>>> next(g)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

**特殊强调：**

**将列表 \[\] 改为 \(\) 这种方式创建的生成器，存在一些缺陷：**

1. **获取元素，必须要使用next\(\)方法。开发中不使用**
2. **当next\(\)方法读取下一个元素时，如果元素不存在，就会报错。**

为了解决以上带来的缺陷，我们需要采用`yeild语句来创建生成器`。并且该生成器可以迭代。

### &lt;2&gt; yield 创建生成器

```
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b    # 通过yield语句，创建生成器
        a, b = b, a + b
        n = n + 1
    return 'done'
```

可以看出，通过fib函数，创建了定义`斐波拉契数列的推算`规则，可以从第一个元素开始，推算出后续任意的元素，这样的生成器。想这样的函数生成器，可以通过for循环，遍历每个元素。

**遍历yield生成器每个元素**

```
In [38]: for n in fib(5):
   ....:     print(n)
   ....:     
1
1
2
3
5

In [39]:
```

### &lt;3&gt;遍历生成器的方式

遍历生成器的方式有以下几种：

1. 使用next\(生成器对象\)方法
2. 生成器对象.\_\__next_\_\_\(\)方法
3. 生成器对象.send\(‘ parma’\)方法

```
In [10]: def gen():
   ....:     i = 0
   ....:     while i<5:
   ....:         temp = yield i
   ....:         print(temp)
   ....:         i+=1
   ....:

In [11]: f = gen()

In [12]: next(f) # 使用next(生成器对象)方法
Out[12]: 0

In [13]: next(f)
None
Out[13]: 1

In [21]: f.__next__() # 生成器对象.__next__()方法
None
Out[21]: 2

In [47]: f.send('haha') # 生成器对象.send(‘ parma’)方法
haha
Out[47]: 3
```

注意事项：

1. 使用f.send\('haha'\) 方式获取元素时，在获取第一个元素时，send\(\)方法中一定传递None作为参数。反之报错！
2. 使用f.send\('haha'\) 方式获取元素时，方法中参数，会作为   `yield i `整个语句的返回值赋值给`temp`变量，

参考代码：

```
In [2]: def gen():
   ...:     i=0
   ...:     while i < 5:
   ...:         temp = yield i
   ...:         print(temp)
   ...:         i+=1
   ...:

In [3]: f = gen()

In [4]: f.send('aa')
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-4-f5a31797d2d7> in <module>()
----> 1 f.send('aa')

TypeError: can't send non-None value to a just-started generator

In [5]: f.send(None)
Out[5]: 0
```



