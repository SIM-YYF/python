# 列表介绍

### 列表格式：

```
namesList = ['xiaoWang','xiaoZhang','xiaoHua']
namesList2 = ['xiaoWang','xiaoZhang',12]
```

注意：**列表中的元素可以是不同类型的**

### 列表元素输入：

```
namesList = ['xiaoWang','xiaoZhang','xiaoHua']
print(namesList[0])
print(namesList[1])
print(namesList[2])
```

### 列表的循环遍历

```
    namesList = ['xiaoWang','xiaoZhang','xiaoHua']
    for name in namesList:
        print(name)
```

```
    namesList = ['xiaoWang','xiaoZhang','xiaoHua']
    length = len(namesList)
    i = 0
    while i<length:
        print(namesList[i])
        i+=1
```

### 列表常见操作

#### &lt;1&gt;添加元素\(append, extend, insert\)

#### append {#append}

通过append可以向列表添加元素.

注意：只能在列表的最后面追击元素

```
In [126]: names=['xiaowang', 'mingming','tom']

In [127]: names
Out[127]: ['xiaowang', 'mingming', 'tom']

In [128]: names.append('fly')

In [129]: names
Out[129]: ['xiaowang', 'mingming', 'tom', 'fly']

In [130]:
```



