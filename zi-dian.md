# 字典介绍

## 定义：

```
info = {'name':'班长', 'id':100, 'sex':'f', 'address':'地球亚洲中国北京'}
```

## 根据键访问值 {#根据键访问值}

```
    info = {'name':'班长', 'id':100, 'sex':'f', 'address':'地球亚洲中国北京'}

    print(info['name'])
    print(info['address'])
```

注意：在我们不确定字典中是否存在某个键而又想获取其值时，可以使用get方法，还可以设置默认值：

```
>>> age = info.get('age')
>>> age #'age'键不存在，所以age为None
>>> type(age)
<type 'NoneType'>
>>> age = info.get('age', 18) # 若info中不存在'age'这个键，就返回默认值18
>>> age
18
```

## 字典的常见操作

### &lt;1&gt;修改元素

字典的每个元素中的数据是可以修改的，只要通过key找到，即可修改

```
    info = {'name':'班长', 'id':100, 'sex':'f', 'address':'地球亚洲中国北京'}
    info['id'] = 200
```

### &lt;2&gt;添加元素

如果在使用**变量名\['键'\] = 数据**时，这个“键”在字典中，不存在，那么就会新增这个元素

```
info = {'name':'班长', 'sex':'f', 'address':'地球亚洲中国北京'}
info['id'] = 100
```

### &lt;3&gt;删除元素

对字典进行删除操作，有一下几种：

* del
* clear\(\)

```
    info = {'name':'班长', 'sex':'f', 'address':'地球亚洲中国北京'}
    del info['name'] # 删除指定元素
    del info # 删除整个字典
    info.clear() # 清空整个字典
```

### &lt;4&gt;len\(\) {#len}

测量字典中，键值对的个数

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}

In [134]: len(info)
Out[134]: 3

In [135]:
```

### &lt;5&gt;keys {#keys}

返回一个包含字典所有KEY的列表

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}

In [136]: info.keys()
Out[136]: dict_keys(['name', 'age', 'sex'])

In [137]:
```

### &lt;6&gt;values {#values}

返回一个包含字典所有value的列表

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}

In [137]: info.values()
Out[137]: dict_values(['ywf', 10, 1])

In [138]:
```

### &lt;7&gt;items {#items}

返回一个包含所有（键，值）元组的列表

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}
In [138]: info.items()
Out[138]: dict_items([('name', 'ywf'), ('age', 10), ('sex', 1)])

In [139]:
```

### &lt;8&gt; in 判断是否包含key {#haskey}

使用 in 判断是否包含key。

如：

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}

In [149]: 'name' in info.keys()
Out[149]: True

In [150]: 'addr' in info.keys()
Out[150]: False
```

### &lt;9&gt;clear\(\)清空整个字典

```
info = {'name':'班长', 'sex':'f', 'address':'地球亚洲中国北京'}
info.clear() # 清空整个字典
```

get\(\)

pop\(\)

popitem\(\)

update\(\)

copy\(\)

fromkeys\(\)

setdefault\(\)

