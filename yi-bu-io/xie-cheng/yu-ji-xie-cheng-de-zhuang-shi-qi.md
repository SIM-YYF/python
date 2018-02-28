如果不预激，那么协程没什么用。调用coroutine.send\(x\)之前，记住一定要调用next\(coroutine \)。为了简化协程的用法，有时会使用一个预激装饰器。

示例中的coroutine装 饰器是一例：

    from functools import wraps

    def coroutine(func):
        """装饰器:向前执行到第一个`yield`表达式，预激`func`"""

        @wraps(func) #wraps修饰器作用：就是将 被修饰的函数(func) 的一些属性值赋值给 修饰器函数(coroutine) ，最终让属性的显示更符合我们的直觉。
        def primer(*args,**kwargs): ➊
            gen = func(*args,**kwargs) ➋ next(gen) ➌
            return gen ➍

        return primer

➊把被装饰的生成器函数替换成这里的primer函数;调用primer函数时，返回预激后的 生成器。

➋调用被装饰的函数，获取生成器对象。

➌预激生成器。  
➍返回生成器

