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

### &lt;2&gt; yeild 创建生成器\( \[ \] 改为 \(\) \)

```
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'
```



