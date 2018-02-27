hashlib模块



```
import hashlib
m = hashlib.md5()   #创建hash对象，md5:(message-Digest Algorithm 5)消息摘要算法,得出一个128位的密文
print m             #<md5 HASH object>
m.update('itcast')  #更新哈希对象以字符串参数
print m.hexdigest() #返回十六进制数字字符串
```



