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

##### append

通过append可以向列表添加元素.

**注意：添加的元素，作为最后一个元素添加列表中**

```
In [126]: names=['xiaowang', 'mingming','tom']

In [127]: names
Out[127]: ['xiaowang', 'mingming', 'tom']

In [128]: names.append('fly')

In [129]: names
Out[129]: ['xiaowang', 'mingming', 'tom', 'fly']

In [130]:
```

##### extend

通过extend可以将另一个集合中的元素逐一添加到列表中

```
>>> a = [1, 2]
>>> b = [3, 4]
>>> a.append(b)
>>> a
[1, 2, [3, 4]]
>>> a.extend(b)
>>> a
[1, 2, [3, 4], 3, 4]
```

##### insert

insert\(index, object\) 在指定位置index前插入元素object

```
>>> a = [0, 1, 2]
>>> a.insert(1, 3)
>>> a
[0, 3, 1, 2]
```

#### &lt;2&gt;修改元素\("改"\)

修改元素的时候，要通过下标来确定要修改的是哪个元素，然后才能进行修改

```
In [126]: names=['xiaowang', 'mingming','tom']
In [130]: names[0]='xiaowang2' # 修改第一个元素
In [131]: names
Out[131]: ['xiaowang2', 'mingming', 'tom']

In [132]:
```

#### &lt;3&gt;查找元素\("查"in, not in, index, count\)

所谓的查找，就是看看指定的元素是否存在

##### in, not in

python中查找的常用方法为：

* in（存在）,如果存在那么结果为true，否则为false
* not in（不存在），如果不存在那么结果为true，否则false



