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



