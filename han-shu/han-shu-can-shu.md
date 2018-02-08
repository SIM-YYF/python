## &lt;1&gt; 定义带有参数的函数 {#定义带有参数的函数}

```
    def add2num(a, b):
        c = a+b
        print c
```

## &lt;2&gt; 调用带有参数的函数 {#调用带有参数的函数}

```
    def add2num(a, b):
        c = a+b
        print c

    add2num(11, 22) #调用带有参数的函数时，需要在小括号中，传递数据
```

## 注意 {#小总结}

* 定义时小括号中的参数，用来接收参数用的，称为 “形参”
* 调用时小括号中的参数，用来传递给函数用的，称为 “实参”

## &lt;3&gt; 缺省参数 {#1-缺省参数}

**调用函数时，缺省参数的值如果没有传入**，则被认为是默认值。

下例会打印默认的age，如果age没有被传入：

```
def printinfo( name, age = 35 ):
   # 打印任何传入的字符串
   print "Name: ", name
   print "Age ", age

# 调用printinfo函数
printinfo(name="miki" )
printinfo( age=9,name="miki" )
```

#### 注意：带有默认值的参数一定要位于参数列表的最后面。 {#注意：带有默认值的参数一定要位于参数列表的最后面。}

```
>>> def printinfo(name, age=35, sex):
...     print name
...
  File "<stdin>", line 1
SyntaxError: non-default argument follows default argument
```

## &lt;4&gt;不定长参数 {#2不定长参数}

函数能处理比当初声明时更多的参数且声明时不会命名，这些参数叫做不定长参数

基本语法：

```
    def functionname([formal_args,] *args, **kwargs):
       "函数_文档字符串"
       function_suite
       return [expression]
```

#### 强调说明：

**加了星号（\*）的变量args会存放所有未命名的变量参数，args为元组**；

**而加\*\*的变量kwargs会存放命名参数，即形如key=value的参数， kwargs为字典**。









