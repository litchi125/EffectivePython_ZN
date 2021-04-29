# 第一章 培养Python思维

​		编程语言的用法习惯是由用户定义的。这么多年来，Python社区使用Pythonic来形容Python这种独特的风格。这种风格并非受编译器的约束或强制形成的，而是在大家使用Python语言及合作的过程中积累下丰富经验，逐渐形成的。Python开发者并不喜欢复杂的代码，他们更喜欢选择简单、高可读，而非复杂的代码。(在你的解析器中输入import this，就可以查看The Zen of Python。)

​		熟悉其他编程语言的程序员可能会尝试按照c++、Java或者他们熟悉的任何语言的编码风格去书写Python代码。对于Python小白来说，可能就需要花些时间去熟悉Python所能表达的众多概念。因此，了解Python中最常用的方法(即Python方法)是很重要的，这些模式将影响你编写的每一个程序。

## 第1条 了解你所使用的Python版本



​		本书的巨大多数代码都将遵循Python3.7(发布于2018年6月)。此外，本书也会给出一些按照Python3.8(发布于2019年10月)语言规范编写的实例，用以突出展示即将广泛使用的Python3.8新特性。本书将不再包含Python2.

​		很多电脑都会搭建包含多个版本的标准CPython运行环境。这就导致，在命令行中运行Python时，默认运行的Python版本并不清除，它有可能启动的是Python2.7，有时也会默认启动一些旧Python版本，例如Python2.6或Python2.5. 你可以使用--version参数，准确的找到所使用的版本号。

~~~shell
$ python --version
Python 2.7.10
~~~

​		Python3可以直接用Python3启动：

~~~shell
$ python3 --version
Python 3.8.0
~~~

​		你还可以通过检查sys内置模块中的值来确定你在运行时使用的Python版本

~~~python
print(sys.version_info)
sys.version_info(major=3, minor=8, micro=1, releaselevel='final', serial=0)
print(sys.version)
3.8.1 (tags/v3.8.1:1b293b6, Dec 18 2019, 23:11:46) [MSC v.1916 64 bit (AMD64)]
~~~

​		Python 3由Python核心开发人员和社区积极维护，并不断得到改进。本书中介绍Python3的各种强大的新特性。大多数最常见的Python开源库都与Python 3兼容，并专注于Python 3。我强烈建议您在所有Python项目中使用ython 3。

​		Python2将于2020年1月1日停止维护，所有的bug修复、安全补丁，以及特性特性都会停止维护。在此之后，再使用Python2进行编码将会是一件痛苦的事，因为官方已经不再维护。深度依赖Python2代码库的开发者可以考虑使用2to3(Python预装工具)和six(社区报，参将项目82)工具进行迁移。

**要点**

* Python3 是最新版本的Python，受到了很好的支持，你应该在你的项目中使用Python3进行开发。
* 在命令行运行Python时，一定要确认启动的Python版本是不是你说需要的。
* 避免再使用Python2进行开发，因为它已经于2020年1月1日停止维护。

## 第2条 遵循PEP8 风格指南

​		Python Enhancement Proposal #8，叫作PEP8，它是针对Python代码风格而编订的风格指南。只要你使用正确的语法，代码随便怎么写都可以，但是采用统一的编码风格能够使你的代码更易读、易懂。如果采用和其他Python开发者相同的代码风格，那么你就可以在社区中很顺利与大家完成协作项目。但是，即使您是唯一一个阅读您的代码的人，遵循样式指南也会使您以后更容易更改内容，并可以帮助您避免许多常见错误。

​		PEP 8提供了关于如何编写清晰Python代码的丰富细节。它会随着Python语言的发展而不断更新。可以在[这里](https://www.python.org/dev/peps/pep-0008/)阅读完整的指南。以下是一些你应该一定要遵守的规则。

**空格**

​		在Python中，空格在语法上是有意义的。Python程序员对空格对代码清晰度的影响特别敏感。遵循以下与空格相关的指导原则:

* 使用空格(space)表示缩进，而不是制表符(tab)
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

* 方法、变量及属性采用小写字母来拼写，各单词之间采用下划线连接，例如：lowercase_underscore
* 受保护的实例属性，采用一个下划线开头，例如：_leading_underscore
* 私有实例属性，采用两个下划线开头，例如：__double_leading_underscore
* 类(包括异常)命名时，每个单词的首字母大写，例如：CapitalizedWord
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

* 把import 语句(包含from x import y)放嘴文件开头
* 引入模块是，应该使用绝对名称，而不应该根据相对路径引入。例如，引入bar包中的foo模块，应该完整地写出from bar import foo，即便当前路径为bar包中，也不应该简写成import foo
* 如果一定要用相对名称来编写impot语句，应该明确的写出from . import foo
* 文件中的import语句应该按顺序分成三部分：首先引入标准库中的模块，然后引入第三方模块，最后引入自定义模块。每一种都要按照字母表顺序引入。

*提示*

​		[Pylint](https://www.pylint.org)是一款流行的Python源码静态分析工具。他可以自动检查手册是的代码是否符合PEP 8风格指南，而且还能找出很多常见错误。很多IDE与编译器，也都办好这样的linting工具或者支持类似的插件。

*要点*

* coding时，应当遵循PEP 8风格指南
* 与广大Python coder采用相同的代码风格，以便可以协作完成项目
* 使用一直的代码风格，代码的后续维护更容易

## 第3条 了解bytes与str的区别

​		在Python中有两种类型表示字符序列：bytes、str。bytes实例包含的是原始数据，即8位的无符号值(通常按照ASCII编码规范显示)

~~~python
a = b'h\x65llo'
print(list(a))
[104, 101, 108, 108, 111]
print(a)
b'hello'
~~~

​		str实例包含的是Unicode码点(code point，也叫代码点)，这些码点与人类语言中的文字字符对应。

~~~python
a = 'a\u0300 propos'
print(list(a))
['a', '̀', ' ', 'p', 'r', 'o', 'p', 'o', 's']
print(a)
à propos
~~~



​		需要注意的是，str实例并不一定非要用固定的方案编码成二进制数据，bytes实例也不一定非要按照某种固定的方案解码成字符串。要不Unicode数据转换成二进制数据，必须调用str的encode方法。要把二进制数据转换成Unicode数据，必须调用byres的decode方法。调用这些方法的时候，可以明确自己要使用的编码方案，也可以采用系统默认的方案，通常为UTF-8(有时候也不一定，下面会讲)。

​		由于两种字符类型的不同，在Python代码中一般分为两种情况：

* 开发者需要操作包含UTF-8编码(或其他编码)的8 bit的原始序列
* 开发者需要操作不含特殊编码的Unicode字符串

​		开发者通常需要两个辅助方法来完成不同情况下的转换，并确保输入值的类型与预期类型相符。

​		第一个辅助方法接受一个bytes 或 str 类型的实例，并返回一个str类型值“

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

​		第二个辅助方法接受一个bytes 或 str实例，并返回一个bytes类型值：

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

​		比较两个字符串完全相同(他们的ASCII编码均表示“foo”)，但分别属于bytes类型和str类型的实例时，通常会返回False：

```python
print(b'foo' == 'foo')

>>>
False
```

​		两种类型的实例都可以出现在%操作符的右侧，用来替换左侧那个格式化字符串(format string)里面的%s：

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

​		这样写的代码，会让操作系统在bytes实例上面调用__ repr__方法(参见项目75)，然后用这次调用所得到的结果替换格式字符串里面的%s，因此程序会输出b'blue'，而不是预期输出的blue。

​		

​		第二个问题发生在操作文件句柄的时候，这里的句柄指的是内置的open方法放回的句柄。这样的句柄默认需要使用Unicode字符串操作，而不能采用原始的bytes。在Python2 中，通常会因此导致出错。例如，将二进制数据写入文件时，这个看似简单的代码就会出错：

```python
with open('data.bin', 'w') as f:
    f.write(b'\xf1\xf2\xf3\xf4\xf5')
    
>>>
TypeError: write() argument must be str, not bytes
```

​		这个异常出现的原因是在调用open方法打开文件时采用了要求以文本形式写入的“w”模式，应当采用“wb”模式。当文件以文本模式打开时，write方法接受的包含Unicode数据的str实例，不是包含二进制数据的bytes实例。所以，我们在调用open方法将模式改为“wb”：

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

​		导致读操作失败的原因是，才用了操作文本数据的“r”模式，应当采用操作二进制数据的“rb”模式。当以文本模式操作句柄时，系统会采用默认的文本编码方式处理二进制数据。所以，上面的写话会让系统通过bytes.decode把数据解码成str字符串，再用str.encode把字符串编码成二进制值。然而对于大多数系统来说，默认的编码方案是UTF-8(这里调成了’gbk‘)，所以系统可能会把b'\xf1\xf2\xf3\xf4\xf5'当做UTF-8(这里是“gbk”)格式字符串去解码，于是就出现上述异常。为了修复这个异常，需要把模式改为“rb”：

```python
with open('data.bin', 'rb') as f:
    data = f.read()
assert data == b'\xf1\xf2\xf3\xf4\xf5'
```

​		此外，也可以也可以在调用open方法时，通过encoding参数来指定编码格式，以确保平台特有的行为不会干扰代码运行的结果。例如，假设刚才写的二进制数据表示的是一个采用’cp1252‘标准(一种老式的Windows编码)进行字符串编码，可以这么写：

```python
with open('data.bin', 'r', encoding='cp1252') as f:
    data = f.read()
assert data == 'ñòóôõ'
```

​		这样操作，异常虽然消失了，但是返回的字符串与读取原始字节数据非常不同。这个例子，告诉我们，要时刻注意当前操作系统默认的编码标准(可以通过命令查看： python3 -c 'import locale; print(locale.getpreferredencoding())')，看是否与期望的相同。当不太确定的时候，在调用open方法是通过encoding参数指定编码方式。



**要点**

* bytes包含的是b bit值所组成的序列，str包含的是Unicode码点组成的序列
* 使用辅助方法来确保操作过程中输入时所期盼的字符串类型 ，是8 bit的序列、UTF-8编码的字符串、Unicode码点还是其他
* bytes实例和str实例之间不能混用诸如>、==、+、%等操作
* 如果想要读取或者写入二进制数据时，应该采用’rb‘ 或者 ’wb'模式
* 如果读取或写入Unicode数据时，应当注意操作系统默认的编码方式。可以通过在调用open方法时，指定encoding参数，来避免出错。

## 第4条 用支持插值的f-string取代C风格的格式字符串与str.format方法

​		字符串在Python代码中普遍存在。在用户界面和命令行实用程序中呈现消息时要用，把数据写入文件或socket时要用，在Exception里异常详情时要用(见项目27)，在进行调试时(参见项目80和项目75)同样要用。

​		格式化是将预定义的文本和数据值组合成人类可读的消息，并将该消息存储为字符串的过程。Python对字符串格式化处理有四种方法，这些方法都内置带语言和标准库中。这四种方法中，除了一种外，其他三个都存在严重缺项使我们应当理解和避免的，这里将在最后将另一种方法。

​		Python中字符串格式化通常采用的方法是使用%。这个操作符左侧的文本模板叫做格式字符串(format string)，我们可以在操作符右边写上某个值或由多个值所构成的元组(tuple)，来替换格式字符串中的相关符号。例如，下面这段代码通过%操作符把难以阅读的二进制和十六进制数值，显示成十进制形式：

~~~python
a = 0b10111011
b = 0xc5f
print('Binary is %d, hex is %d' % (a, b))

>>>
Binary is 187, hex is 3167
~~~

​		格式字符串中像%d这样的占位符会被右侧的数据替换。这样的格式化语法来自C语言的printf方法，Python语言以及其他编程语言都沿用了类似的方式。所以Python支持printf中%s、%x、%f等占位符，同时也支持控制小数点的位置、并支持填充和对其方式。对于许多Python小白来书都喜欢C风格的字符串格式化，因为他们比较熟悉这种方式并且这种方式比较简单。

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

​		如果必须对格式化的值重复一些小的修改，那么这尤其令人恼火，而且容易出错。例如，如果这次要填的是name.title()而不是name本身，就需要提醒自己，把所有的name都改成name.title()。如果有的地方改了，有的地方没改，那输出的结果可能就不一致了：

~~~python
name = 'brad'
formatted = template % (name.title(), name.title())
print(formatted)

>>>
Brad loves food. See Brad cook.

~~~

​		为了结果这个问题，Python不仅可以对元组进行%操作，也可以对字典类型进行%操作。格式字符串里面的说明符与dict里面的键以相应的名称对应起来，例如%(keys)s这个说明符，疑似就是用字符串(s)来表示dict里面名为key的那个键所对应的值。这里，通过这种方法解决刚才讲到的第一个缺点，也就是用%操作符两侧的顺序不匹配问题：

```python
key = 'my_var'
value = 1.234
old_way = '%-10s = %.2f' % (key, value)
new_way = '%(key)-10s = %(value).2f' % {
    'key': key, 'value': value}  # Original
reordered = '%(key)-10s = %(value).2f' % {
    'value': value, 'key': key}  # Swapped
print(old_way)
print(new_way)
print(reordered)

>>>
my_var     = 1.23
my_var     = 1.23
my_var     = 1.23
```

​		在格式化字符串时使用字典也解决了上面讲到的第三个问题，也就是用同一个值替换多个格式化说明符的问题。改用这种写法之后，我们就不用在%右侧重复这个值了：

```python
name = 'Max'
template = '%s loves food. See %s cook.'
before = template % (name, name) # Tuple
template = '%(name)s loves food. See %(name)s cook.'
after = template % {'name': name} # Dictionary
print(before)
print(after)

>>>
Max loves food. See Max cook.
Max loves food. See Max cook.
```

​		然而，字典格式化字符串的方法又会带来新的问题。例如上面提到的第二个关于格式化前对值的最小修改问题，字典格式化会让格式化表达式会变得更长，视觉上也更混乱，因为在格式化表达式之前，值的右侧会出现字典键和冒号操作符：

```python
pantry = [
    ('avocados', 1.25),
    ('bananas', 2.5),
    ('cherries', 15),
]
for i, (item, count) in enumerate(pantry):
    before = '#%d: %-10s = %d' % (
        i + 1,
        item.title(),
        round(count))
    after = '#%(loop)d: %(item)-10s = %(count)d' % {
        'loop': i + 1,
        'item': item.title(),
        'count': round(count),
    }
    print(before)
    print(after)

>>>
#1: Avocados   = 1
#1: Avocados   = 1
#2: Bananas    = 2
#2: Bananas    = 2
#3: Cherries   = 15
#3: Cherries   = 15
```

​		在格式化表达式时使用字典还会增加冗长，这是Python中c风格表达式格式化的问题#4。每个键必须至少被指定两次——一次是在格式说明符中，一次是在字典中作为键，还有一次可能是在包含字典值的变量名中:

```python
soup = 'lentil'
formatted = 'Today\'s soup is %(soup)s.' % {'soup': soup}
print(formatted)

>>>
Today's soup is lentil.
```

​		除了重复的字符外，这种冗余会导致使用字典的格式化表达式很长。这些表达式通常必须跨多行，格式字符串跨多行连接，而字典赋值在格式化中每个值只有一行:

```python
menu = {
    'soup': 'lentil',
    'oyster': 'kumamoto',
    'special': 'schnitzel',
}
template = ('Today\'s soup is %(soup)s, '
            'buy one get two %(oyster)s oysters, '
            'and our special entrée is %(special)s.')
formatted = template % menu
print(formatted)

>>>
Today's soup is lentil, buy one get two kumamoto oysters, and our special entrée is schnitzel.
```

​		要理解这个格式表达式将输出什么样的结果，必须在格式字符串和字典的行之间来回观察。这种脱节使得很难发现错误，如果需要在格式化之前对任何值进行小的修改，可读性就会变得更糟。

​		一定会有更好的办法才对！

**内置的format方法与str类的format方法**

​		Python3中添加了高级字符串格式化(advanced string formatting)机制，它的表达能力比C风格采用的%操作要强。针对单个Python值，通过内置的format方法可以很好的实现所需。例如，通过逗号表示千位分隔符，^表示居中对齐：

```python
a = 1234.5678
formatted = format(a, ',.2f')
print(formatted)
b = 'my string'
formatted = format(b, '^20s')
print('*', formatted, '*')

>>>
1,234.57
*      my string       *
```

​		针对str类型，使用内置的format方法可以同时格式化对个值。这种方法，摒弃了C风格的%，而是采用{}充当占位符。默认情况下，格式字符串中的占位符被传递给format方法的相应位置参数替换，这些参数按它们出现的顺序传递：

~~~python
key = 'my_var'
value = 1.234
formatted = '{} = {}'.format(key, value)
print(formatted)

>>>
my_var = 1.234
~~~

​		在每个占位符中，你可以选择提供一个冒号，后面跟着格式说明符，以自定义值如何转换为字符串(请参阅帮助('FORMATTING')了解全部选项):

~~~python
key = 'my_var'
value = 1.234
formatted = '{:<10} = {:.2f}'.format(key, value)
print(formatted)
>>>
my_var = 1.23
~~~

​		可以这样理解这种格式化的方法：系统把str.format方法接受到的每个值传递给内置的format方法，并找到这个值在字符串中对应的{}，同时将{}里面写的格式也传递给format方法，例如系统处理value时，传的就是format(value,'.2f')。然后，系统会把format方法所返回的结果卸载真个格式化字符串{}所在的位置。另外。每个类都可以通过__ format__这个内置方法制定相应的逻辑，这样的话format方法在把类实例转换成字符串时，就会按照这个逻辑转换。

​		C风格格式化采用%来应道格式说明符，所以如果这个符号按照原样输出，就必须转义，也就是连写两个%%。同理，在调用str.format的时候，如果想把str中{、}输出，也需要转义：

~~~python
print('%.2f%%' % 12.5)
print('{} replaces {{}}'.format(1.23))
>>>
12.50%
1.23 replaces {}
~~~

​		在花括号内，还可以指定传递给format方法用于替换占位符的参数的位置索引。这允许更新格式字符串来重新排序输出，而不需要你也改变格式表达式的右边，从而解决上面的第一个问题:

~~~python
key = 'my_var'
value = 1.234
formatted = '{1} = {0}'.format(key, value)
print(formatted)
>>>
1.234 = my_var
~~~

​		同样的位置索引也可以在格式字符串中被多次引用，而不需要将值多次传递给格式方法，这从上到下解决了第三个问题：

~~~python
formatted = '{0} loves food. See {0} cook.'.format(name)
print(formatted)
>>>
Max loves food. See Max cook.
~~~

​		不幸的是，新的格式方法并不能解决上面的第二问题，当需要在格式化值之前对其进行小的修改时，会使代码难以阅读。新旧选项之间的可读性几乎没有差别，它们也同样繁杂：

~~~python
pantry = [
    ('avocados', 1.25),
    ('bananas', 2.5),
    ('cherries', 15),
]
for i, (item, count) in enumerate(pantry):
    old_style = '#%d: %-10s = %d' % (
    i + 1,
    item.title(),
    round(count))
    new_style = '#{}: {:<10s} = {}'.format(
    i + 1,
    item.title(),
    round(count))
    print(old_style)
    print(new_style)

>>>
#1: Avocados   = 1
#1: Avocados   = 1
#2: Bananas    = 2
#2: Bananas    = 2
#3: Cherries   = 15
#3: Cherries   = 15
~~~

​		str.format方法中使用的说明符还有更高级的选项，比如在占位符中使用字典键和列表索引的组合，以及将值强制转换为Unicode和repr字符串:

~~~python
menu = {
    'soup': 'lentil',
    'oyster': 'kumamoto',
    'special': 'schnitzel',
}
formatted = 'First letter is {menu[oyster][0]!r}'.format(
menu=menu)
print(formatted)
>>>
First letter is 'k'
~~~

​		但是这些特性并不能帮助减少第四个问题中的重复键的冗余。例如，这里我比较了在C风格的格式化表达式中使用字典的冗长，以及向format方法传递关键字参数的新风格

```python
    old_template = (
        'Today\'s soup is %(soup)s, '
        'buy one get two %(oyster)s oysters, '
        'and our special entrée is %(special)s.')
    old_formatted = old_template % {
        'soup': 'lentil',
        'oyster': 'kumamoto',
        'special': 'schnitzel',
    }
    new_template = (
        'Today\'s soup is {soup}, '
        'buy one get two {oyster} oysters, '
        'and our special entrée is {special}.')
    new_formatted = new_template.format(
        soup='lentil',
        oyster='kumamoto',
        special='schnitzel',
    )
    print(old_formatted)
    print(new_formatted)
>>>
Today's soup is lentil, buy one get two kumamoto oysters, and our special entrée is schnitzel.
Today's soup is lentil, buy one get two kumamoto oysters, and our special entrée is schnitzel.
```

​		这种风格稍微不那么混乱，因为它消除了字典中的一些引号和格式说明符中的一些字符，但它几乎没有什么吸引力。此外，在占位符中使用字典键和索引的高级特性只提供了Python的一小部分表达功能。这种表达性的缺乏是如此有限，以至于从整体上削弱了str格式方法的价值。

​		考虑到这些缺点和C风格格式表达式仍然存在第二和第四个问题，通常避免使用str.format。当然，我们还是必须掌握新的格式说明符所使用的这套迷你语言(mini language)，我们可以在str的{}里面按照这套迷你语言的规则来指定冒号右侧的格式。系统内置的format方法也会使用这套规则。除此之外，str.format方法就只有历史意义了，他让我们可以在这套机制的基础之上学习Python新引入的f-string。

**差值格式字符串**

​		Python3.6添加了新的特性--插值格式字符串(interpolated format string，简写f-string)，这一种新的语法将会解决上面出现的所有问题。这种语法要求在格式字符串前添加前缀字母f，和bytes类型的字符串前面的b，或者表示原始字符串(未经转义)的前缀r是一样的。

​		f-string让格式字符串的表达能力发挥到了极致，他彻底解决了上面的第四个问题：键名导致程序冗余。我们不用像C风格那样专门定义dict，也不用再像调用str.format方法那样专门把值传给某个参数，这次可以直接在f-string的{}里面引用当前Python里所以的变量名，从而达到简化目的：

~~~python
key = 'my_var'
value = 1.234
formatted = f'{key} = {value}'
print(formatted)
>>>
my_var = 1.234
~~~

​		str.format方法所支持的那套秘密语言，也就是在{}内的冒号右侧所采用的那套规则，现在也可以用到f-string中，而且可以向之前使用str.format那样，通过！符号把值转化为Unicode和repr形式的字符串：

~~~python
formatted = f'{key!r:<10} = {value:.2f}'
print(formatted)
>>>
'my_var' = 1.23
~~~

​		采用f-string要比C风格的%操作以及str.format方法都更加简短。这里，从短到长的顺序把这种方法统一展示，并且将等号右侧对齐，以便更好的观察：

```python
key = 'my_var'
value = 1.234
f_string = f'{key:<10} = {value:.2f}'
c_tuple = '%-10s = %.2f' % (key, value)
str_args = '{:<10} = {:.2f}'.format(key, value)
str_kw = '{key:<10} = {value:.2f}'.format(key=key,
                                          value=value)
c_dict = '%(key)-10s = %(value).2f' % {'key': key,
                                       'value': value}

print(f_string)
print(c_tuple)
print(str_args)
print(str_kw)
print(c_dict)

>>>
my_var     = 1.23
my_var     = 1.23
my_var     = 1.23
my_var     = 1.23
my_var     = 1.23
```

​		f -string还允许将完整的Python表达式放入占位符括号中，通过允许对使用简洁语法格式化的值进行小的修改，从上面解决第二个问题。用c风格的格式和str.format方法实现多行现在很容易就能在一行中实现：

```python
pantry = [
    ('avocados', 1.25),
    ('bananas', 2.5),
    ('cherries', 15),
]
for i, (item, count) in enumerate(pantry):
    old_style = '#%d: %-10s = %d' % (
        i + 1,
        item.title(),
        round(count))
    new_style = '#{}: {:<10s} = {}'.format(
        i + 1,
        item.title(),
        round(count))
    f_string = f'#{i + 1}: {item.title():<10s} = {round(count)}'
    print(new_style)
    print(new_style)
    print(f_string)

>>>
#1: Avocados   = 1
#1: Avocados   = 1
#1: Avocados   = 1
#2: Bananas    = 2
#2: Bananas    = 2
#2: Bananas    = 2
#3: Cherries   = 15
#3: Cherries   = 15
#3: Cherries   = 15
```

​		你也可以向C语言相邻字符串(adiacent-string concatenation)拼接那样，把f-string写成多行，这样看起来会更加清晰。尽管，这样写要比单行更长，当仍然比其他多行的写法要好很多：

```python
pantry = [
    ('avocados', 1.25),
    ('bananas', 2.5),
    ('cherries', 15),
]
for i, (item, count) in enumerate(pantry):
    print(f'#{i + 1}: '
          f'{item.title():<10s} = '
          f'{round(count)}')
 >>>
#1: Avocados   = 1
#2: Bananas    = 2
#3: Cherries   = 15
```

​		Python表达式也可以出现在格式说明符选项中。例如通过使用变量而不是在格式字符串中硬编码来参数化要打印的数字数：

```python
places = 3
number = 1.23456
print(f'My number is {number:.{places}f}')

>>>
My number is 1.235
```

​		f-string所提供的表达性、简洁性和清晰性的结合，使其成为Python程序员的最佳内置选项。当需要将值格式化为字符串时，推荐使用f-strings。

**要点**

* 使用%操作符的c风格格式字符串会遇到各种陷阱和冗长的问题。
* str.format方法在其格式化说明符迷你语言中引入了一些有用的概念，但是它重复了c风格格式字符串的错误，应该加以避免。
* F-strings是一种用于将值格式化为字符串的新语法，它解决了c风格格式字符串的最大问题。
* F-string简洁但功能强大，因为它们允许任意Python表达式直接嵌入到格式说明符中。

## 第5条  用辅助方法代替复杂的表达式

​		Python简洁的语法使得编写实现大量逻辑的单行表达式变得很容易。例如，假设我想解码来自URL的查询字符串。这里，每个查询字符串参数表示一个整数值：

```python
from urllib.parse import parse_qs
my_values = parse_qs('red=5&blue=0&green=',
keep_blank_values=True)
print(repr(my_values))

>>>
{'red': ['5'], 'blue': ['0'], 'green': ['']}
```

​		在解析字符串参数时，有的可能有多个参数，有的可能只是单一参数，有的可能是空白值，可能还会遇到一些没有提供参数的情况。在结果字典上使用get方法将在每种情况下返回不同的值：

```python
from urllib.parse import parse_qs
my_values = parse_qs('red=5&blue=0&green=',
keep_blank_values=True)
# print(my_values)
# print(repr(my_values))
print('Red: ', my_values.get('red'))
print('Green: ', my_values.get('green'))
print('Opacity: ', my_values.get('opacity'))
>>>
Red:  ['5']
Green:  ['']
Opacity:  None
```

​		当参数不存在或者为空时，可以给定默认值0。对于这样的情况，采用Boolean表达式是更好的选择，不值得写完成的if语句或者辅助方法。

​		Python的Boolean表达式这种语法写起来更简单，Python会把空字符串、空列表以及0都当做False。因此，只需要把get方法吵到的结果放在or操作符的左边，并在右边写上0就可以了。这样的话，只要左面的表达式为False，name整个表达式的值就自然被评估为右边那个表达式的值，也就是0.

```python
red = my_values.get('red', [''])[0] or 0
green = my_values.get('green', [''])[0] or 0
opacity = my_values.get('opacity', [''])[0] or 0
print(f'Red: {red!r}')
print(f'Green: {green!r}')
print(f'Opacity: {opacity!r}')

>>>
Red: '5'
Green: 0
Opacity: 0
```

​		red这种情况正常返回，因为red值在my_values字典中，他的值就是在list列表中的一个字符串值。Python会把吧这种情况默认为True，所以red值就是or左侧的部分。

​		green能够读取是因为green的值是list列表中的空字符串。空字符串，Python默认为False，green的值就是or右侧的0.

​		opacity能够读取是因为：opacity不在my_values字典中，Python会默认返回第二个值[''](参见第16条)。默认值也是只有空字符串的列表，所以当opacity在字典中找不到时和green一样。

​		然而，这个表达式很难读懂，而且它仍然没有完成我们的所有需求。如果还希望确保所有的参数都转换为整数，以便可以立即在数学表达式中使用，还需要将内置方法int写进去，才能将字符串解析为int：

~~~python
red = int(my_values.get('red', [''])[0] or 0)

~~~

​		这样更加难读，并且看起还更加别扭。这种代码很可怕，如果你是第一次阅读，就需要把整个表达式逐层拆开，才能明白表达啥意思，这很浪费时间。代码可以下的短一些

并非都要写在一行：

~~~Python
red_str = my_values.get('red', [''])
red = int(red_str[0]) if red_str[0] else 0
~~~

​		这样写更好。当逻辑不是太复杂，if/else条件表达式会让代码更清晰。但是在这个例子中，不如写一个完整的if/else表达式结构清晰。对比实现逻辑的几种展开表达式，刚才的那种浓缩式的写法就显得复杂：

~~~python
green_str = my_values.get('green', [''])
if green_str[0]:
	green = int(green_str[0])
else:
	green = 0
~~~

​		如果你需要重复的使用这种逻辑，可以写一个辅助方法：

~~~python
def get_first_int(values, key, default=0):
	found = values.get(key, [''])
	if found[0]:
		return int(found[0])
return default

~~~

​		这样的代码要比采用or的表达式或者if/else结构都更加清晰易懂。

~~~python
green = get_first_int(my_values, 'green')
~~~

​		一旦表达式变得复杂，就应该考虑将它们分割成更小的部分，并将逻辑转移到帮助方法中。这样所获得的可读性总是超过所获得的简洁性。避免复杂表达式的语法让你陷入像这样的混乱。遵循DRY原则:不要重复自己。

**要点**

* Python语法很容易把复杂的意思放在同一行表达，这样写很难懂
* 复杂的表达式，尤其是要重复使用的复杂表达式，应该放到辅助方法中
* 用if/else条件表达式，要比or、and写成的Boolean更好懂

## 第6条 把数据结构直接拆分到多个变量里,不要专门通过下标访问

​		Python内置的元组类型可以创建不可变的序列，把许多元素依次保存起来。最简单的方法是只用元组保存两个值，例如字典里的键值对：

```python
snack_calories = {
'chips': 140,
'popcorn': 80,
'nuts': 190,
}
items = tuple(snack_calories.items())
print(items)

>>>
(('chips', 140), ('popcorn', 80), ('nuts', 190))
```

​		可以通过数字索引直接访问元组里的值：

```python
item = ('Peanut butter', 'Jelly')
first = item[0]
second = item[1]
print(first, 'and', second)

>>>
Peanut butter and Jelly
```

​		一旦建立了元组，就不能够在通过索引去重新赋值：

```python
pair = ('Chocolate', 'Peanut butter')
pair[0] = 'Honey'

>>>
    pair[0] = 'Honey'
TypeError: 'tuple' object does not support item assignment
```

​		Python同样拥有解包的语法，通过这种语法只需要一个语句就可以把元组里面的元素赋值给多个变量。解包元组时，并非是要修改元组本身，并且元组本身是不可更改的，但是解包后赋值元素的变量是不一样的。例如，如果元组是确定的，就可以直接通过解包操作把元组的元素赋值给两个变量名，而不通过索引：

~~~python
item = ('Peanut butter', 'Jelly')
first, second = item # Unpacking
print(first, 'and', second)
>>>
Peanut butter and Jelly
~~~

​		通过解包操作来赋值要比通过下标去访问元组内的元素更加简洁，并通常仅需要几行代码。解包操作的左侧也可以是列表、序列、或任意深度的可迭代对象(iterable)。这里并不推荐按照下面这么写代码，但是知道它的原理是非常重要的：

~~~python
favorite_snacks = {
'salty': ('pretzels', 100),
'sweet': ('cookies', 180),
'veggie': ('carrots', 20),
}
((type1, (name1, cals1)),
(type2, (name2, cals2)),
(type3, (name3, cals3))) = favorite_snacks.items()
print(f'Favorite {type1} is {name1} with {cals1} calories')
print(f'Favorite {type2} is {name2} with {cals2} calories')
print(f'Favorite {type3} is {name3} with {cals3} calories')

>>>
Favorite salty is pretzels with 100 calories
Favorite sweet is cookies with 180 calories
Favorite veggie is carrots with 20 calories
~~~

​		对于Python小白来说，可能还不知道通过解包操作还可以交换两个变量的值，而不专门创建临时变量。这里使用典型的索引语法在列表中的两个位置之间交换值，这是升序排序算法的一部分：

```python
def bubble_sort(a):
    for _ in range(len(a)):
        for i in range(1, len(a)):
            if a[i] < a[i-1]:
                temp = a[i]
                a[i] = a[i-1]
                a[i-1] = temp
names = ['pretzels', 'carrots', 'arugula', 'bacon']
bubble_sort(names)
print(names)

>>>
['arugula', 'bacon', 'carrots', 'pretzels']
```

​		然而，通过解包语法，就可以通过简单的一行实现交换：

~~~python
def bubble_sort(a):
    for _ in range(len(a)):
        for i in range(1, len(a)):
            if a[i] < a[i-1]:
                a[i-1],a[i] = a[i], a[i-1]

names = ['pretzels', 'carrots', 'arugula', 'bacon']
bubble_sort(names)
print(names)

>>>
['arugula', 'bacon', 'carrots', 'pretzels']
~~~

​		这种交换变量的原理是：Python在处理赋值操作时，要先对等号右侧赋值，于是，它会创建一个临时的元组，把a[i] 与a[i-a]这两个元素放到临时的元组中。例如，第一次

进入循环内部是，这两个元素分别是‘carrots’与‘pretzels’，于是，系统就创建临时元组(‘carrots’,‘pretzels’)。然后，Python会对这个临时元组进行解包操作，把临时元组里面的两个元素分别放到等号左边的两个地方，于是，‘carrots’就会把a[i-1]里面原有的‘pretzels’替换，‘pretzels‘也会把a[i]里面原有的’carrots‘替换条。现在，出现在a[0]的位置就是’carrots‘，出现在a[1位置的就是’pretzels‘。做完解包操作后，系统会挥手这个临时元组。

​		解包操作还有一个重要的用法，可以用在for循环或者类似的结构中(例如推导与生成表达式，第27条)，把复杂的数据拆分到相关的变量之中。下面这段代码没有采用解包操作，而是采用了传到的写法迭代snacks列表里面的元素。

```python
snacks = [('bacon', 350), ('donut', 240), ('muffin', 190)]
for i in range(len(snacks)):
    item = snacks[i]
    name = item[0]
    calories = item[1]
	print(f'#{i+1}: {name} has {calories} calories')

>>>
#1: bacon has 350 calories
#2: donut has 240 calories
#3: muffin has 190 calories
```

​		这虽然能获取到正确结果，但是却很乱，因为snacks结构本身就是复杂列表，每一个元素都是一个元组，所以必须逐层访问才能查到具体的数据。下面换一种写法，首先调用内置的enumerate方法(参见第7条)获取当前要迭代的元组，然后针对这个元组进行解包，这样就可以直接获取到具体的name与calories值：

~~~python
for rank, (name, calories) in enumerate(snacks, 1):
	print(f'#{rank}: {name} has {calories} calories')
>>>
#1: bacon has 350 calories
#2: donut has 240 calories
#3: muffin has 190 calories
~~~

​		这是Python风格的写法，不需要再通过下标逐层访问了。这种写法简短且容易理解。

​		Python的解包操作可以用在多个方面，例如构建列表(第13条)、给方法设计参数列表(第22条)、传递关键字参数(第23条)、接收多个返回值(第19条)等。

​		明智的使用解包操作，可以避免使用下标带来的麻烦，并且能让代码结果跟简单。

**要点**

* 解包操作是一种特殊的Python语法，只需要一行代码，就能把数据结构中的多个元素赋给多个值
* 解包操作在Python中运用广泛，凡是可迭代的对象都可以拆分，无论里面还有多少层迭代结构
* 尽量通过解包操作而不是下标访问数据，这能时代更简洁、明了

## 第7条 尽量使用enumerate取代range

​		Python 内置的range方法适合迭代一系列整数。

```python
from random import randint
random_bits = 0
for i in range(32):
    if randint(0, 1):
        random_bits |= 1 << i

print(bin(random_bits))

>>>
0b10100010100010110001100001010111
```

​		当有一个数据结构要迭代时，比如字符串列表，可以直接在序列上循环：

~~~python
flavor_list = ['vanilla', 'chocolate', 'pecan', 'strawberry']
for flavor in flavor_list:
print(f'{flavor} is delicious')

>>>
vanilla is delicious
chocolate is delicious
pecan is delicious
strawberry is delicious
~~~

​		当迭代一个列表数据时，经常会需要知道当前元素在列表中的位置。例如，遍历最喜欢的冰淇淋时，还要打印出他们的排行。可以通过传统的range方式：

~~~python
flavor_list = ['vanilla', 'chocolate', 'pecan', 'strawberry']
for i in range(len(flavor_list)):
flavor = flavor_list[i]
print(f'{i + 1}: {flavor}')
>>>
1: vanilla
2: chocolate
3: pecan
4: strawberry
~~~

​		与遍历flavor_list或range的其他例子相比，这看起来有些笨拙。我必须知道列表的长度。必须对数组下标，且多重步骤使它更难阅读。

​		Python提供了内置方法enumerate来解决这个问题。enumerate方法能够把任何一种迭代器(iterator)封装成惰性生成器(lazy generator，见第30条)。当每次迭代的时候，enumerate产生对循环索引和给定迭代器的下一个值。这里，通过内置的next方法手动推进enumerate所返回的iterator，来演示enumerate的原理：

```python
flavor_list = ['vanilla', 'chocolate', 'pecan', 'strawberry']
it = enumerate(flavor_list)
print(next(it))
print(next(it))
>>>
(0, 'vanilla')
(1, 'chocolate')
```

​		enumerate输出的每一对数据，还可以通过for循环解包(见第6条)给两个变量。这样会使代码更清晰：

~~~python
for i, flavor in enumerate(flavor_list):
	print(f'{i + 1}: {flavor}')
>>>
1: vanilla
2: chocolate
3: pecan
4: strawberry
~~~

​		另外，还可通过enumerate的第二个参数指定其实序号，这样就不用在每次打印的时候去调整了。例如，本例可以从1开始计算：

```python
flavor_list = ['vanilla', 'chocolate', 'pecan', 'strawberry']
for i, flavor in enumerate(flavor_list,1):
    print(f'{i}: {flavor}')
    
>>>
1: vanilla
2: chocolate
3: pecan
4: strawberry
```

**要点**

* enumerate方法可以通过简洁的代码迭代iterator，而且可以指出循环的序号
* 直接用enumerate方法而非通过range方法指定下标的取值范围，再用下标去访问序列
* 可以通过enumerate的第二个参数指定起始序号(默认为0)

