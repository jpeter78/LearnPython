#2020.01.17学习并记录

变量和简单数据类型

### 变量的命名和使用

+ 变量名只能包含字母、数字和下划线，不能以数字开头
+ 将Python关键字和函数名做变量名，即不要使用Python保留用于特殊用途的单词
+ 变量名应既简短又具有描述性。
+ 变量名不要使用全大写字母，一般默认用它来表示全局变量，虽然python没有全局变量的概念。

### 字符串

字符串就是一系列的字符，在Python中，用引号括起的都是字符串，可以用双引号或单引号；但不能一边单引号，一边双引号。
+ title：对字符串每个单词首字母大写
``` python
name = 'ada lovelace'
print(name.title())
```
+ upper：字符串每个字母大写
+ lower：字符串每个字母小写
``` python
name = 'Ada Lovelace'
print(name.upper())
print(name.lower())
```
+ rstrip：去除字符串末尾的空白
+ lstrip：去除字符串开头的空白
+ strip:去除字符串首尾的空白
+ 拼接：用+可以把两个字符串拼接成一个字符串。
``` python
first_name = 'ada'
last_name = 'lovelace'
full_name = first_name + ' ' + last_name
```
+ 换行：\n
+ 制表符：\t
``` python
print('Languages:\n\tPython\n\tC\n\tJavaScript')
```


数字
