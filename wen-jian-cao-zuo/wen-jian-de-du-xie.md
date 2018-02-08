## &lt;1&gt;写数据\(write\) {#写数据write}

使用write\(\)可以完成向文件写入数据

```
f = open('test.txt', 'w')
f.write('hello world, i am here!')
f.close()
```

注意：

* 如果文件不存在那么创建，如果存在那么就先清空，然后写入数据



