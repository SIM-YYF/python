## hashlib模块

Python的hashlib提供了常见的摘要算法，如MD5，SHA1等等。

摘要算法又称哈希算法、散列算法。它通过一个函数，把任意长度的数据转换为一个长度固定的数据串（通常用16进制的字符串表示）。

```
import hashlib
m = hashlib.md5()   #创建hash对象，md5:(message-Digest Algorithm 5)消息摘要算法,得出一个128位的密文
print m             #<md5 HASH object>
m.update('how to use md5 in python hashlib?')  #更新哈希对象以字符串参数
print m.hexdigest() #返回十六进制数字字符串
```

计算结果：

```
d26a53750bc40b38b65a520292f69306
```



