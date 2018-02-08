## &lt;1&gt;写数据\(write\) {#写数据write}

使用write\(\)可以完成向文件写入数据

```
f = open('test.txt', 'w')
f.write('hello world, i am here!')
f.close()
```

注意：

* 如果文件不存在那么创建，如果存在那么就先清空，然后写入数据

## &lt;2&gt;读数据\(read\) {#读数据read}

使用read\(num\)可以从文件中读取数据，num表示要从文件中读取的数据的长度（单位是字节），如果没有传入num，那么就表示读取文件中所有的数据

```

f = open('test.txt', 'r')

content = f.read(5)

print(content)

print("-"*30)

content = f.read()

print(content)

f.close()
```



