## py02_day03

# 正则表达

元字符

| **记号** | **说 明**                                |
| -------- | ---------------------------------------- |
| .        | 匹配任意字符（换行符除外）               |
| […x-y…]  | 匹配字符组里的任意字符                   |
| [^…x-y…] | 匹配不在字符组里的任意字符               |
| \d       | 匹配任意数字，与[0-9]同义                |
| \w       | 匹配任意数字字母字符，与[0-9a-zA-Z_]同义 |
| \s       | 匹配空白字符，与[ \r\v\f\t\n]同义        |

| **记号** | **说 明**                              |
| -------- | -------------------------------------- |
| literal  | 匹配字符串的值                         |
| re1\|re2 | 匹配正则表达式re1或re2                 |
| *        | 匹配前面出现的正则表达式零次或多次     |
| +        | 匹配前面出现的正则表达式一次或多次     |
| ?        | 匹配前面出现的正则表达式零次或一次     |
| {M, N}   | 匹配前面出现的正则表达式至少M次最多N次 |

| **记号** | **说 明**        |
| -------- | ---------------- |
| ^        | 匹配字符串的开始 |
| $        | 匹配字符串的结尾 |
| \b       | 匹配单词的边界   |
| ()       | 对正则表达式分组 |
| \nn      | 匹配已保存的子组 |

# 常用函数与方法

match()函数  尝试用正则表达式模式从字符串的开头匹配，如果匹配成功，则返回一个匹配对象；否则返回None

```
>>> import  re
>>> m = re.match('foo', 'food')           #成功匹配
>>> print(m)
<_sre.SRE_Match object; span=(0, 3), match='foo'>
>>> 
>>> m = re.match(‘foo’, ‘seafood’)      #未能匹配
>>> print(m)
None

例子2
>>> import re
>>> re.match('f..','food buyfood goodfood eatfood')
<_sre.SRE_Match object; span=(0, 3), match='foo'>
>>> 
>>> re.match('f..','buyfood goodfood eatfood')
>>> 
>>> m=re.match('f..','buyfood goodfood eatfood')
>>> print(m)
None
>>> 
>>> m2=re.match('f..','food buyfood goodfood eatfood')
>>> m2.group()
'foo'
>>>

```

search()函数: 在字符串中查找正则表达式模式的第一次出现，如果匹配成功，则返回一个匹配对象；否则返回None

```
>>> import re
>>> m = re.search('foo', 'food')
>>> print(m)
<_sre.SRE_Match object; span=(0, 3), match='foo'>
>>> 
>>> m = re.search(‘foo’, ‘seafood’)      #可以匹配在字符中间的模式
>>> print(m)
<_sre.SRE_Match object; span=(3, 6), match='foo'>

例子2
>>> re.search('f..','food buyfood goodfood eatfood')
<_sre.SRE_Match object; span=(0, 3), match='foo'>
>>> 
>>> m1 = re.search('f..','food buyfood goodfood eatfood')
>>> 
>>> m2 = re.search('f..','buyfood goodfood eatfood')
>>> 
>>> m1.group()
'foo'
>>> m2.group()
'foo'
>>> 


```

group方法：使用match或search匹配成功后，返回的匹配对象可以通过group方法获得匹配内容

```
>>> import re
>>> m = re.match('foo', 'food')
>>> print(m.group())
foo

>>> m = re.search('foo', 'seafood')
>>> m.group()
'foo'

```

findall函数：在字符串中查找正则表达式模式的所有出现；返回一个匹配对象的列表

```
>>> import re
>>> m = re.search('foo', 'seafood is food')
>>> print(m.group())    #search只匹配模式的第一次出现
foo
>>> 
>>> m = re.findall(‘foo’, ‘seafood is food’)  #获得全部的匹配项
>>> print(m)
['foo', 'foo']

例子2
>>> m1 = re.findall('f..','food buyfood goodfood eatfood')
>>> 
>>> m2 = re.findall('f..','buyfood goodfood eatfood')
>>> 
>>> print(m1)
['foo', 'foo', 'foo', 'foo']
>>> 
>>> print(m2)
['foo', 'foo', 'foo']
>>> 


```

finditer()和findall()函数有相同的功能，但返回的不是列表而是迭代器；对于每个匹配，该迭代器返回一个匹配对象

```
>>> m = re.finditer('foo','food buyfood goodfood eatfood')
>>> for i in m:
...     print(i.group())
... 
foo
foo
foo
foo
>>>
```



compile函数: 对正则表达式模式进行编译，返回一个正则表达式对象
不是必须要用这种方式，但是在大量匹配的情况下，可以提升效率

```
>>> import re
>>> patt = re.compile('foo')
>>> m = patt.match('food buyfood goodfood eatfood')
>>> m.group()
'foo'
>>>

例子2
>>> patt=re.compile('f..')
>>> m = patt.findall('buyfood goodfood eatfood')
>>> print(m)
['foo', 'foo', 'foo']

```

split方法: 根据正则表达式中的分隔符把字符分割为一个列表，并返回成功匹配的列表
字符串也有类似的方法，但是正则表达式更加灵活

```
>>> import re      #使用 . 和 - 作为字符串的分隔符
>>> mylist = re.split('\.|-', 'hello-world.data')
>>> print(mylist)
['hello', 'world', 'data']

```

sub方法  把字符串中所有匹配正则表达式的地方替换成新的字符串

```
>>> import re
>>> m = re.sub('girl', 'woman', 'she is a girl  beautiful girl')
>>> print(m)
she is a woman  beautiful woman
>>> 

```





