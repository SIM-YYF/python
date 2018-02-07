## python2中的输入

### 1.1 raw\_input\(\) {#11-rawinput}

在Python中，获取键盘输入的数据的方法是采用 raw\_input 函数。如：

```
password = raw_input("请输入内容:")
print ("您输入的内容是：%s"%password)
```

**注意**:

* raw\_input\(\)的小括号中放入的是，提示信息，用来在获取数据之前给用户的一个简单提示
* raw\_input\(\)在从键盘获取了数据以后，会存放到等号右边的变量中
* raw\_input\(\)会把用户输入的任何值都作为字符串来对待

### 1.2 input\(\) {#12-input}

input\(\)函数与raw\_input\(\)类似，但其接受的输入必须是**表达式**。

