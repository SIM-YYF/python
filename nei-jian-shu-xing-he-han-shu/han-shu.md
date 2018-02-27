内建函数

启动python解释器，输入`dir(__builtins__)，` 可以看到很多python解释器启动后默认加载的属性和函数，这些函数称之为内建函数。

```
[
  'ArithmeticError',
  'AssertionError',
  'AttributeError',
  'BaseException',
  'BlockingIOError',
  'BrokenPipeError',
  'BufferError',
  'BytesWarning',
  'ChildProcessError',
  'ConnectionAbortedError',
  'ConnectionError',
  'ConnectionRefusedError',
  'ConnectionResetError',
  'DeprecationWarning',
  'EOFError',
  'Ellipsis',
  'EnvironmentError',
  'Exception',
  'False',
  'FileExistsError',
  'FileNotFoundError',
  'FloatingPointError',
  'FutureWarning',
  'GeneratorExit',
  'IOError',
  'ImportError',
  'ImportWarning',
  'IndentationError',
  'IndexError',
  'InterruptedError',
  'IsADirectoryError',
  'KeyError',
  'KeyboardInterrupt',
  'LookupError',
  'MemoryError',
  'ModuleNotFoundError',
  'NameError',
  'None',
  'NotADirectoryError',
  'NotImplemented',
  'NotImplementedError',
  'OSError',
  'OverflowError',
  'PendingDeprecationWarning',
  'PermissionError',
  'ProcessLookupError',
  'RecursionError',
  'ReferenceError',
  'ResourceWarning',
  'RuntimeError',
  'RuntimeWarning',
  'StopAsyncIteration',
  'StopIteration',
  'SyntaxError',
  'SyntaxWarning',
  'SystemError',
  'SystemExit',
  'TabError',
  'TimeoutError',
  'True',
  'TypeError',
  'UnboundLocalError',
  'UnicodeDecodeError',
  'UnicodeEncodeError',
  'UnicodeError',
  'UnicodeTranslateError',
  'UnicodeWarning',
  'UserWarning',
  'ValueError',
  'Warning',
  'ZeroDivisionError',
  '__build_class__',
  '__debug__',
  '__doc__',
  '__import__',
  '__loader__',
  '__name__',
  '__package__',
  '__spec__',
  'abs',
  'all',
  'any',
  'ascii',
  'bin',
  'bool',
  'bytearray',
  'bytes',
  'callable',
  'chr',
  'classmethod',
  'compile',
  'complex',
  'copyright',
  'credits',
  'delattr',
  'dict',
  'dir',
  'divmod',
  'enumerate',
  'eval',
  'exec',
  'exit',
  'filter',
  'float',
  'format',
  'frozenset',
  'getattr',
  'globals',
  'hasattr',
  'hash',
  'help',
  'hex',
  'id',
  'input',
  'int',
  'isinstance',
  'issubclass',
  'iter',
  'len',
  'license',
  'list',
  'locals',
  'map',
  'max',
  'memoryview',
  'min',
  'next',
  'object',
  'oct',
  'open',
  'ord',
  'pow',
  'print',
  'property',
  'quit',
  'range',
  'repr',
  'reversed',
  'round',
  'set',
  'setattr',
  'slice',
  'sorted',
  'staticmethod',
  'str',
  'sum',
  'super',
  'tuple',
  'type',
  'vars',
  'zip'
]
```

#### range {#range}

```
range(stop) -> list of integers
range(start, stop[, step]) -> list of integers
```

* start:计数从start开始。默认是从0开始。例如range（5）等价于range（0， 5）;

* stop:到stop结束，但不包括stop.例如：range（0， 5） 是\[0, 1, 2, 3, 4\]没有5

* step:每次跳跃的间距，默认为1。例如：range（0， 5） 等价于 range\(0, 5, 1\)

python2中range返回列表，python3中range返回一个迭代值。如果想得到列表,可通过list函数

```
a = range(5)
list(a)

或者

In [21]: testList = [x+2 for x in range(5)]
In [22]: testList
Out[22]: [2, 3, 4, 5, 6]
```

#### map函数 {#map函数}

map函数会根据提供的函数对指定序列做映射。

```
map(function, sequence[, sequence, ...]) -> list
```

* function:是一个函数

* sequence:是一个或多个序列,取决于function需要几个参数

* 返回值是一个list

```
#函数需要一个参数
map(lambda x: x*x, [1, 2, 3])
#结果为:[1, 4, 9]

#函数需要两个参数
map(lambda x, y: x+y, [1, 2, 3], [4, 5, 6])
#结果为:[5, 7, 9]


def f1( x, y ):  
    return (x,y)

l1 = [ 0, 1, 2, 3, 4, 5, 6 ]  
l2 = [ 'Sun', 'M', 'T', 'W', 'T', 'F', 'S' ]
l3 = map( f1, l1, l2 ) 
print(list(l3))
#结果为:[(0, 'Sun'), (1, 'M'), (2, 'T'), (3, 'W'), (4, 'T'), (5, 'F'), (6, 'S')]
```

参数序列中的每一个元素分别调用function函数，返回包含每次function函数返回值的list。

#### filter函数 {#filter函数}

```
filter(function or None, sequence) -> list, tuple, or string
```

参数说明：

* function:接受一个参数，返回布尔值True或False

* sequence:序列可以是str，tuple，list

特点：

filter函数会对序列参数sequence中的每个元素调用function函数，最后返回的结果包含调用结果为True的元素。

返回值的类型和参数sequence的类型相同

```
filter(lambda x: x%2, [1, 2, 3, 4])
[1, 3]

filter(None, "she")
'she'
```

#### reduce函数 {#reduce函数}

reduce函数，reduce函数会对参数序列中元素进行累积

```
reduce(function, sequence[, initial]) -> value
```

参数说明：

* function:该函数有两个参数

* sequence:序列可以是str，tuple，list

* initial:固定初始值

```
reduce(lambda x, y: x+y, [1,2,3,4])
10

reduce(lambda x, y: x+y, [1,2,3,4], 5)
15

reduce(lambda x, y: x+y, ['aa', 'bb', 'cc'], 'dd')
'ddaabbcc'
```

注意：

> 在Python3里,reduce函数已经被从全局名字空间里移除了, 它现在被`放置在fucntools模块里`用的话要先引入：
>
> `from functools import reduce`



