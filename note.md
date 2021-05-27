# 1.注册函数

**register函数原型**

> atexit.register(func, ***args**, ***\*kwargs**)

**register函数的作用**

Python的atexit模块定义了一个register函数，该函数会在Python解释器退出前执行的回调函数，**一般用作程序运行完成后，对内存等的清理工作**

**unregister函数**

作用：取消register注册的函数

**注意**

* 如果程序是非正常crash或通过os._exit()退出，注册的回调函数将不会被调用
* 也可以通过sys.exitfunc来注册回调，但通过它只能注册一个回调，而且还不支持参数
* 建议使用atexit来注册回调函数。

**特别注意**

* 不要在程序中同时使用这两种方式，否则通过atexit注册的回调可能不会被正常调用
* 如果使用的python版本是2.6及以后的版本，还可以用装饰器的语法来注册回调函数
* 注册函数执行的顺序为FILO：即注册顺序为A、B、C，则调用的顺序为：C、B、A

**函数调用方式**

* atexit.register(fun, *args, **kwargs)直接调用
* 通过装饰器调用：@atexit.register

**实例**

demo1.py

~~~python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Time : 2021/5/27/027 23:01
# @Author : H
# @File : demo1.py
import atexit
import os


def atexitFunc_1():
    '''
    the first register function:No arguments function
    :return:
    '''
    print('I am atexitFunc_1')


def atexitFunc_2(name, age):
    '''
    the second register function:Need arguments function
    :return:
    '''

    print('I am atexitFunc_2, %s is %d years old' % (name, age))


print('I am the first output')
atexit.register(atexitFunc_1)
# 通过atexit.unregiste取消注册函数
#atexit.unregister(atexitFunc_1)
atexit.register(atexitFunc_2, 'Katherine', 20)
print('I am the second output')


@atexit.register
def atexitFunc_3():
    '''
    the third register function:Decorator call
    :return:
    '''
    print('I am atexitFunc_3')


print('I am the third output')
>>>
I am the first output
I am the second output
I am the third output
I am atexitFunc_3
I am atexitFunc_2, Katherine is 20 years old
I am atexitFunc_1
~~~

​		注册的回调函数，在程序所有正常的函数执行完毕后，按照FIFO的方式执行。

~~~python
import atexit
import os


def atexitFunc_1():
    '''
    the first register function:No arguments function
    :return:
    '''
    print('I am atexitFunc_1')


def atexitFunc_2(name, age):
    '''
    the second register function:Need arguments function
    :return:
    '''

    print('I am atexitFunc_2, %s is %d years old' % (name, age))


print('I am the first output')
atexit.register(atexitFunc_1)

# atexit.unregister(atexitFunc_1)
atexit.register(atexitFunc_2, 'Katherine', 20)
print('I am the second output')
# 程序抛出异常
print(1 / 0)


@atexit.register
def atexitFunc_3():
    '''
    the third register function:Decorator call
    :return:
    '''
    print('I am atexitFunc_3')


print('I am the third output')
>>>
I am the first output
I am the second output
I am atexitFunc_2, Katherine is 20 years old
I am atexitFunc_1
Traceback (most recent call last):
  File "E:/pycharm_pro/EffectivePythonCode/item38/demo.py", line 36, in <module>
    print(1 / 0)
ZeroDivisionError: division by zero
~~~

​		在程序抛出异常时，后续注册的函数将不会被回调。

~~~python
import atexit
import os


def atexitFunc_1():
    '''
    the first register function:No arguments function
    :return:
    '''
    print('I am atexitFunc_1')


def atexitFunc_2(name, age):
    '''
    the second register function:Need arguments function
    :return:
    '''

    print('I am atexitFunc_2, %s is %d years old' % (name, age))


print('I am the first output')
atexit.register(atexitFunc_1)

# atexit.unregister(atexitFunc_1)
atexit.register(atexitFunc_2, 'Katherine', 20)
print('I am the second output')


@atexit.register
def atexitFunc_3():
    '''
    the third register function:Decorator call
    :return:
    '''
    print('I am atexitFunc_3')


print('I am the third output')

print(os._exit(status=0))
>>>
I am the first output
I am the second output
I am the third output
~~~

​		注册函数，遇到系统os._exit退出时，将不再执行

