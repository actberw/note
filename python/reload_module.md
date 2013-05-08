## 重新加在被修改过得模块

1\. 如果在import得是一个模块对象, 直接reload模块对象(不是字符串)  

    >>> reload(module_name)
2\. 如果import得是模块内部的对象  

    >>> import sys  
    >>> reload(sys.modules[`module_name_str`])  
然后在重新import.
