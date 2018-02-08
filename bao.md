# 包

包将有联系的模块组织在一起，即放到同一个文件夹下，并且在这个文件夹创建一个名字为`__init__.py`

文件，那么这个文件夹就称之为`包`

### &lt;1&gt;`__init__.py`文件作用

1.1`__init__.py`控制导包的导入行为

1.2`__init__.py`为空:仅仅是把这个包导入，不会导入包中的模块

1.3 `__all__变量`

在`__init__.py`文件中，定义一个`__all__`变量，它控制着 from 包名 import \*时导入的模块

### &lt;2&gt; 包的结构

假定我们的包的例子有如下的目录结构：

```
Phone/
    __init__.py
    common_util.py
    Voicedta/
        __init__.py
        Pots.py
        Isdn.py
    Fax/
        __init__.py
        G3.py
    Mobile/
        __init__.py
        Analog.py
        igital.py
    Pager/
        __init__.py
        Numeric.py
```



