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



