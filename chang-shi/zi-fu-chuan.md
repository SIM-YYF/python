### 字符串的输出

```
    name = '新锐'
    print('--------------------------------------------------')
    print("姓名：%s"%name)
    print('--------------------------------------------------')
```

### 字符串的输入

```
    userName = input('请输入用户名:')
    print("用户名为：%s"%userName)
```

注意：input获取的数据，都以字符串的方式进行保存，即使输入的是数字，那么也是以字符串方式保存

### 字符串的小标和切片

#### "下标"的使用

**字符串：实际上就是字符的数组，所以也支持下标索引。**

如：

```
   name = 'abcdef'
   print(name[0])
   print(name[1])
   print(name[2])
```

#### 切片的使用

切片是指对操作的对象截取其中一部分的操作。**字符串、列表、元组**都支持切片操作。

#### 切片的语法：\[起始:结束:步长\] {#切片的语法：起始结束步长}

**注意：选取的区间属于左闭右开型，即从"起始"位开始，到"结束"位的前一位结束（不包含结束位本身\)。**

如：

```
>>> name = 'abcdef'
>>> print(name[0:3]) # 取 下标0~2 的字符
```

```
 >>> a = "abcdef"
 >>> a[:3] #下标0开始，去0-3的字符
 'abc'
```

```
 >>> a = "abcdef"
 >>> a[::2] #取0-最后的字符，且步长为2
 'ace'
```

```
 >>> a = "abcdef"
 >>> a[::-2] # 取 从右边 下标为：-1 到 最左边 ，且步长为2的值 
 'fdb'
```

```
>>> a='abcdfe'
>>> a[::-1] # 反转字符串
'efdcba'
```

### 字符串常见的操作函数

#### &lt;1&gt;find {#find}

作用：检测 str 是否包含在 mystr中，如果是返回开始的索引值，否则返回-1

```
In [10]: name='hellow fly'

In [11]: name.find('fly',0, len(name))
Out[11]: 7

In [12]: name.find('ywf',0, len(name))
Out[12]: -1
```

#### &lt;2&gt;index {#index}

跟find\(\)方法一样，只不过如果str不在 mystr中会报一个异常.

如：

```
In [10]: name='hellow fly'

In [13]: name.index('ywf',0, len(name))
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-13-584e280768fb> in <module>()
----> 1 name.index('ywf',0, len(name))

ValueError: substring not found

In [14]:
```

#### &lt;3&gt;count {#count}

返回 str在字符串start和end之间出现的次数

```
In [10]: name='hellow fly'
In [14]: name.count('ywf',0, len(name))
Out[14]: 0
In [15]: name.count('fly',0, len(name))
Out[15]: 1
```

#### &lt;4&gt;replace {#replace}

把 mystr 中的 str1 替换成 str2,如果 count 指定，则替换不超过 count 次.

```
In [10]: name='hellow fly'
In [16]: name.replace('fly','ywf', name.count('fly'))
Out[16]: 'hellow ywf'
```



