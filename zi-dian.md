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



