# 第一章 培养Python思维

​		编程语言的用法习惯是由用户定义的。这么多年来，Python社区使用Pythonic来形容Python这种独特的风格。这种风格并非受编译器的约束或强制形成的，而是在大家使用Python语言及合作的过程中积累下丰富经验，逐渐形成的。Python开发者并不喜欢复杂的代码，他们更喜欢选择简单、高可读，而非复杂的代码。（在你的解析器中输入import this，就可以查看The Zen of Python。）

​		熟悉其他编程语言的程序员可能会尝试按照c++、Java或者他们熟悉的任何语言的编码风格去书写Python代码。对于Python小白来说，可能就需要花些时间去熟悉Python所能表达的众多概念。因此，了解Python中最常用的方法（即Python方法）是很重要的，这些模式将影响你编写的每一个程序。

## 第1条 了解你所使用的Python版本



​		本书的巨大多数代码都将遵循Python3.7（发布于2018年6月）。此外，本书也会给出一些按照Python3.8（发布于2019年10月）语言规范编写的实例，用以突出展示即将广泛使用的Python3.8新特性。本书将不再包含Python2.

​		很多电脑都会搭建包含多个版本的标准CPython运行环境。这就导致，在命令行中运行Python时，默认运行的Python版本并不清除，它有可能启动的是Python2.7，有时也会默认启动一些旧Python版本，例如Python2.6或Python2.5. 你可以使用--version参数，准确的找到所使用的版本号。

$ python --version

Python 2.7.10

​		Python3可以直接用Python3启动：

$ python3 --version

Python 3.8.0

​		你还可以通过检查sys内置模块中的值来确定你在运行时使用的Python版本

>>> print(sys.version_info)
>>> sys.version_info(major=3, minor=8, micro=1, releaselevel='final', serial=0)
>>> print(sys.version)
>>> 3.8.1 (tags/v3.8.1:1b293b6, Dec 18 2019, 23:11:46) [MSC v.1916 64 bit (AMD64)]

​		Python 3由Python核心开发人员和社区积极维护，并不断得到改进。本书中介绍Python3的各种强大的新特性。大多数最常见的Python开源库都与Python 3兼容，并专注于Python 3。我强烈建议您在所有Python项目中使用ython 3。

​		Python2将于2020年1月1日停止维护，所有的bug修复、安全补丁，以及特性特性都会停止维护。在此之后，再使用Python2进行编码将会是一件痛苦的事，因为官方已经不再维护。深度依赖Python2代码库的开发者可以考虑使用2to3（Python预装工具）和six（社区报，参将项目82）工具进行迁移。

**要点**

* Python3 是最新版本的Python，受到了很好的支持，你应该在你的项目中使用Python3进行开发。
* 在命令行运行Python时，一定要确认启动的Python版本是不是你说需要的。
* 避免再使用Python2进行开发，因为它已经于2020年1月1日停止维护。

## 第2条 遵循PEP8 风格指南

​		Python Enhancement Proposal #8，叫作PEP8，它是针对Python代码风格而编订的风格指南。只要你使用正确的语法，代码随便怎么写都可以，但是采用统一的编码风格能够使你的代码更易读、易懂。如果采用和其他Python开发者相同的代码风格，那么你就可以在社区中很顺利与大家完成协作项目。但是，即使您是唯一一个阅读您的代码的人，遵循样式指南也会使您以后更容易更改内容，并可以帮助您避免许多常见错误。

​		PEP 8提供了关于如何编写清晰Python代码的丰富细节。它会随着Python语言的发展而不断更新。值得在网上(https://www.python.org/dev/peps/pep-0008/)阅读完整的指南。以下是一些你应该一定要遵守的规则。

**空格**

​		在Python中，空格在语法上是有意义的。Python程序员对空格对代码清晰度的影响特别敏感。遵循以下与空格相关的指导原则:

* 使用空格（space）表示缩进，而不是制表符（tab）
* 和语法相关的每一层缩进都要用4个空格表示
* 每行最多不超多79个字符
* 针对较长的表达式，当延伸到其他行时，应在正常缩进的基础上缩进额外的4个空格
* 在同一个py文件中，方法和类之间间隔两个空行
* 在同一个类中，方法间间隔一个空行
* 在字典中，在每个键和冒号之间不放空格，如果对应的值在同一行，则在其前面放一个空格
* 在变量赋值时，等号左右各放且仅放一个空格
* 对于类型注释，确保变量名和冒号之间没有分隔，并且在类型信息之前使用空格

**命名**

​		PEP 8建议对代码中的不同部分采用独特的命名风格。这些约定使得在阅读代码是很容易区分哪个类型对应哪个名称。遵循下面的指导规则：

* 函数、变量及属性采用小写字母来拼写，各单词之间采用下划线连接，例如：lowercase_underscore
* 受保护的实例属性，采用一个下划线开头，例如：_leading_underscore
* 私有实例属性，采用两个下划线开头，例如：__double_leading_underscore
* 类（包括异常）命名时，每个单词的首字母大写，例如：CapitalizedWord
* 模块级别的常量，所有字母大写，各单词之间用下换线连接，例如：all_caps
* 类中的实例方法，应该把第一个参数命名为self，用来表示对象本身
* 类方法的第一个参数，应该命名为cls，用来表示类本身

**表达式与语句**

​		The Zen of Python中讲到“每件事都应该有简单的方法，而且最好只有一种”。PEP 8就采用这个理念，来贵方表达式和语句的写法。

* 使用内联否定(如果a不是b)代替肯定表达式的否定(如果a不是b)
* 不要通过将长度与0比较来检查空容器或序列(如[]或")(如果len(somelist) == 0)。使用if not somelist这样的写法，因为Python会将空值自动表示为False
* 避免单行if语句、for和while循环，以及除复合语句之外的语句。为了清晰起见，将这些内容分散到多个行中
* 如果不能将表达式放在一行中，可以用圆括号将其括起来，并添加换行符和缩进，以使其更易于阅读
* 多行的表达式，应该用括号括起来，而不是使用\符号续行

**import**

​		PEP 8对于怎么在代码中引入模块，给出下面的建议

* 把import 语句（包含from x import y）放嘴文件开头
* 引入模块是，应该使用绝对名称，而不应该根据相对路径引入。例如，引入bar包中的foo模块，应该完整地写出from bar import foo，即便当前路径为bar包中，也不应该简写成import foo
* 如果一定要用相对名称来编写impot语句，应该明确的写出from . import foo
* 文件中的import语句应该按顺序分成三部分：首先引入标准库中的模块，然后引入第三方模块，最后引入自定义模块。每一种都要按照字母表顺序引入。

*提示*

​		Pylint（https://www.pylint.org）是一款流行的Python源码静态分析工具。他可以自动检查手册是的代码是否符合PEP 8风格指南，而且还能找出很多常见错误。很多IDE与编译器，也都办好这样的linting工具或者支持类似的插件。

*要点*

* coding时，应当遵循PEP 8风格指南
* 与广大Python coder采用相同的代码风格，以便可以协作完成项目
* 使用一直的代码风格，代码的后续维护更容易

## 第3条 了解bytes与str的区别

​		在Python中有两种类型表示字符序列：bytes、str。bytes实例包含的是原始数据，即8位的无符号值（通常按照ASCII编码规范显示）

>>> a = b'h\x65llo'
>>> print(list(a))
>>> [104, 101, 108, 108, 111]
>>> print(a)
>>> b'hello'

​		str实例包含的是Unicode码点（code point，也叫代码点），这些码点与人类语言中的文字字符对应。

>>> a = 'a\u0300 propos'
>>> print(list(a))
>>> ['a', '̀', ' ', 'p', 'r', 'o', 'p', 'o', 's']
>>> print(a)
>>> à propos

​		需要注意的是，str实例并不一定非要用固定的方案编码成二进制数据，bytes实例也不一定非要按照某种固定的方案解码成字符串。要不Unicode数据转换成二进制数据，必须调用str的encode方法。要把二进制数据转换成Unicode数据，必须调用byres的decode方法。调用这些方法的时候，可以明确自己要使用的编码方案，也可以采用系统默认的方案，通常为UTF-8(有时候也不一定，下面会讲)。

​		由于两种字符类型的不同，在Python代码中一般分为两种情况：

* 开发者需要操作包含UTF-8编码（或其他编码）的8 bit的原始序列
* 开发者需要操作不含特殊编码的Unicode字符串

​		开发者通常需要两个辅助函数来完成不同情况下的转换，并确保输入值的类型与预期类型相符。

​		第一个辅助函数接受一个bytes 或 str 类型的实例，并返回一个str类型值“

```python
def to_str(bytes_or_str):
    if isinstance(bytes_or_str, bytes):
        value = bytes_or_str.decode('utf-8')
    else:
        value = bytes_or_str
    return value  # Instance of str


if __name__ == '__main__':
    print(repr(to_str(b'foo')))
    print(repr(to_str('bar')))
 
>>>
'foo'
'bar'
```

​		第二个辅助函数接受一个bytes 或 str实例，并返回一个bytes类型值：

```python
def to_bytes(bytes_or_str):
    if isinstance(bytes_or_str, str):
        value = bytes_or_str.encode('utf8')
    else:
        value = bytes_or_str
    return value  # Instance of bytes


if __name__ == '__main__':
    print(repr(to_bytes(b'foo')))
    print(repr(to_bytes('bar')))
    
>>>
b'foo'
b'bar'
```

​		在Python中处理原始8 bit值和Unicode字符串时，有两个需要注意的大问题。

​		第一个问题是，bytes和str看起来以相同的方式工作，但是他们的实例却相互不兼容，所以在传递字符串序列时，必须要注意其类型。

​		通过“+”操作，可以连接bytes和bytes类型，或者str和str类型，但是要分别连接两种类型：

```python
print(b'one' + b'two')
print('one' + 'two')

>>>
b'onetwo'
onetwo
```

​		不可将str实例与bytes实例进行拼接操作“

```python
print(b'one' + 'two')

>>>
TypeError: can't concat str to bytes
```

​		同样，不能讲bytes实例和str实例进行拼接操作”

```python
print('one' + b'two')

>>>
TypeError: can only concatenate str (not "bytes") to str
```

​		通过二进制操作，你也可以比较bytes和bytes实例，或者str和str类型实例：

```python
assert b'red' > b'blue'
assert 'red' > 'blue'
```

​		但是，不能比较str实例和bytes实例：

```python
assert 'red' > b'blue'

>>>
TypeError: '>' not supported between instances of 'str' and 'bytes'

```

​		同样，不能比较bytes实例和str实例：

```python
assert b'red' > 'blue'

>>>
TypeError: '>' not supported between instances of 'bytes' and 'str'
```

​		比较两个字符串完全相同（他们的ASCII编码均表示“foo”），但分别属于bytes类型和str类型的实例时，通常会返回False：

```python
print(b'foo' == 'foo')

>>>
False
```

​		两种类型的实例都可以出现在%操作符的右侧，用来替换左侧那个格式化字符串（format string）里面的%s：

```python
print(b'red %s' % b'blue')
print('red %s' % 'blue')

>>>
b'red blue'
red blue
```

​		但是，如果格式字符串中表示bytes实例，就不能传递一个str类型的实例，因为Python不知道这个二进制文本应该用什么格式进行编码：

```python
print(b'red %s' % 'blue')

>>>
TypeError: %b requires a bytes-like object, or an object that implements __bytes__, not 'str'
```

​		如果格式化字符串表示str实例，可以传递bytes实例，但是结果与预期不同：

```python
print('red %s' % b'blue')

>>>
red b'blue'
```

​		这样写的代码，会让操作系统在bytes实例上面调用__ repr__方法（参见项目75），然后用这次调用所得到的结果替换格式字符串里面的%s，因此程序会输出b'blue'，而不是预期输出的blue。

​		

​		第二个问题发生在操作文件句柄的时候，这里的句柄指的是内置的open函数放回的句柄。这样的句柄默认需要使用Unicode字符串操作，而不能采用原始的bytes。在Python2 中，通常会因此导致出错。例如，将二进制数据写入文件时，这个看似简单的代码就会出错：

```python
with open('data.bin', 'w') as f:
    f.write(b'\xf1\xf2\xf3\xf4\xf5')
    
>>>
TypeError: write() argument must be str, not bytes
```

​		这个异常出现的原因是在调用open函数打开文件时采用了要求以文本形式写入的“w”模式，应当采用“wb”模式。当文件以文本模式打开时，write方法接受的包含Unicode数据的str实例，不是包含二进制数据的bytes实例。所以，我们在调用open函数将模式改为“wb”：

```python
with open('data.bin', 'wb') as f:
    f.write(b'\xf1\xf2\xf3\xf4\xf5')
```

​		文件读操作时，同样会出现相似的问题。例如，当通过下面的代码尝试读取上面写好的二进制文件时：

~~~python
with open('data.bin', 'r') as f:
data = f.read()

>>>
UnicodeDecodeError: 'gbk' codec can't decode byte 0xf5 in position 4: incomplete multibyte sequence
~~~

​		导致读操作失败的原因是，才用了操作文本数据的“r”模式，应当采用操作二进制数据的“rb”模式。当以文本模式操作句柄时，系统会采用默认的文本编码方式处理二进制数据。所以，上面的写话会让系统通过bytes.decode把数据解码成str字符串，再用str.encode把字符串编码成二进制值。然而对于大多数系统来说，默认的编码方案是UTF-8（这里调成了’gbk‘），所以系统可能会把b'\xf1\xf2\xf3\xf4\xf5'当做UTF-8（这里是“gbk”）格式字符串去解码，于是就出现上述异常。为了修复这个异常，需要把模式改为“rb”：

```python
with open('data.bin', 'rb') as f:
    data = f.read()
assert data == b'\xf1\xf2\xf3\xf4\xf5'
```

​		此外，也可以也可以在调用open方法时，通过encoding参数来指定编码格式，以确保平台特有的行为不会干扰代码运行的结果。例如，假设刚才写的二进制数据表示的是一个采用’cp1252‘标准（一种老式的Windows编码）进行字符串编码，可以这么写：

```python
with open('data.bin', 'r', encoding='cp1252') as f:
    data = f.read()
assert data == 'ñòóôõ'
```

​		这样操作，异常虽然消失了，但是返回的字符串与读取原始字节数据非常不同。这个例子，告诉我们，要时刻注意当前操作系统默认的编码标准（可以通过命令查看： python3 -c 'import locale; print(locale.getpreferredencoding())'），看是否与期望的相同。当不太确定的时候，在调用open函数是通过encoding参数指定编码方式。



**要点**

* bytes包含的是b bit值所组成的序列，str包含的是Unicode码点组成的序列
* 使用辅助函数来确保操作过程中输入时所期盼的字符串类型 ，是8 bit的序列、UTF-8编码的字符串、Unicode码点还是其他
* bytes实例和str实例之间不能混用诸如>、==、+、%等操作
* 如果想要读取或者写入二进制数据时，应该采用’rb‘ 或者 ’wb'模式
* 如果读取或写入Unicode数据时，应当注意操作系统默认的编码方式。可以通过在调用open方法时，指定encoding参数，来避免出错。

## 第4条 用支持插值的f-string取代C风格的格式字符串与str.format方法

​		字符串在Python代码中普遍存在。在用户界面和命令行实用程序中呈现消息时要用，把数据写入文件或socket时要用，在Exception里异常详情时要用（见项目27），在进行调试时（参见项目80和项目75）同样要用。

​		格式化是将预定义的文本和数据值组合成人类可读的消息，并将该消息存储为字符串的过程。Python对字符串格式化处理有四种方法，这些方法都内置带语言和标准库中。这四种方法中，除了一种外，其他三个都存在严重缺项使我们应当理解和避免的，这里将在最后将另一种方法。

​		Python中字符串格式化通常采用的方法是使用%。这个操作符左侧的文本模板叫做格式字符串（format string），我们可以在操作符右边写上某个值或由多个值所构成的元组（tuple），来替换格式字符串中的相关符号。例如，下面这段代码通过%操作符把难以阅读的二进制和十六进制数值，显示成十进制形式：

~~~python
a = 0b10111011
b = 0xc5f
print('Binary is %d, hex is %d' % (a, b))

>>>
Binary is 187, hex is 3167
~~~

​		格式字符串中像%d这样的占位符会被右侧的数据替换。这样的格式化语法来自C语言的printf函数，Python语言以及其他编程语言都沿用了类似的方式。所以Python支持printf中%s、%x、%f等占位符，同时也支持控制小数点的位置、并支持填充和对其方式。对于许多Python小白来书都喜欢C风格的字符串格式化，因为他们比较熟悉这种方式并且这种方式比较简单。

​		在Python中采用C风格字符串格式化会有四个问题。

​		第一个问题是，如果你想改变%右侧元组中值的类型或顺序，可能会出现因类型转换不兼容而报错的问题。例如，下面简单的格式化表达是正确的：

~~~Python
key = 'my_var'
value = 1.234
formatted = '%-10s = %.2f' % (key, value)
print(formatted)

>>>
my_var = 1.23
~~~

​		但是，如果交换key和value，运行时就会报错：

```python
key = 'my_var'
value = 1.234
formatted = '%-10s = %.2f' % (value, key)
print(formatted)

>>>
TypeError: must be real number, not str
```

​		相似的，不改变右侧参数的位置，改变格式字符串中的位置，同样会报错：

~~~
key = 'my_var'
value = 1.234
formatted = '%.2f = %-10s' % (key, value)
print(formatted)

>>>
TypeError: must be real number, not str
~~~

​		为了避免这样的问题出现，就必须经常检查两侧的写法是否兼容。这个过程很容易出错，因为每次改完之后都要手工检查。

​		第二个缺点是，在填充模板之前，经常需要先对准备写进去的值进行小的调整，但这样依赖，真个表达式就会很长，让人感觉很混乱。在这里，我列出了我的厨房储藏室的内容，而没有进行内联更改。

```python
pantry = [
    ('avocados', 1.25),
    ('bananas', 2.5),('cherries', 15),
]
for i, (item, count) in enumerate(pantry):
    print('#%d: %-10s = %.2f' % (i, item, count))
    
>>>
#0: avocados   = 1.25
#1: bananas    = 2.50
#2: cherries   = 15.00
```

​		现在，我对正在格式化的值做了一些修改，以使打印的消息更有用。这将导致格式化表达式中的元组变得非常长，以至于需要跨多行分割，这损害了可读性:

~~~python
for i, (item, count) in enumerate(pantry):
	print('#%d: %-10s = %d' % (
		i + 1,
		item.title(),
		round(count)))

>>>
#1: Avocados = 1
#2: Bananas = 2
#3: Cherries = 15
~~~



​		第三个问题是，如果你想在一个格式化字符串中多次使用相同的值，你必须在右边的元组中重复它：

~~~python
template = '%s loves food. See %s cook.'
name = 'Max'
formatted = template % (name, name)
print(formatted)

>>>
Max loves food. See Max cook.
~~~

​		如果必须对格式化的值重复一些小的修改，那么这尤其令人恼火，而且容易出错。