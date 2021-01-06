---
title: Python-基础
date: 2021-01-03 16:27:23
tags:
- Python
- Python-基础
categories: Python
top_img:
cover:
---

###   Python-基础

####  1. 格式化输出 `format`

```python
person_name = '张三'

person_age = 18

person_sex = '男'

print('''
    姓名: {}
    
    年龄: {}
    
    性别: 
    
'''.format(person_name, person_age, person_sex))
```

#### 2. `%s`

```python

person_name = '张三'

person_age = '18'

person_sex = '男'


print('姓名:%s 年龄:%s 性别:%s'%(person_name,person_age,person_sex))

```

####  3. `input`输入

```python
# input

name = input('请输入 python: ')

print('学习语言: '+name)

```

#### 4. 进制转换

```python

```

#### 5. 三目运算符

```python
# 三目运算符
a = 4
b = 6
result = a + b if a < b else b - a
# 10 
print(result) 
```

####  6. `if` 语句

```python
# if
a = 10
b = 30

if a>b:
    print(a)
else:
    print(b)
   
```

####  7.  `for` 循环

```python
# 使用系统 range 指定范围
arr = ['a',1,{'value':'bin'}]
for i in range(len(arr)):
    print(arr[i])

-------------------------

# 输出 3 遍 hello world
for ia in range(3):
    print('Hello world')

-------------------------------

# 九九乘法口诀表
for i in range(1, 10):
    for j in range(1, i+1):
        print('{}x{}={}\t'.format(j, i, i*j), end='')
    print()
    
```

####  8. `for else`结构

```python
# pass 空语句
```

####  9. `while`循环

```python
n = 1
while n<=30:
    if n%3==0 and n%5==0:
        print('---------------->',n)
    n+=1
    
# python 独有方法
ceng = 1
while ceng<=5:
    print('*'*ceng)
    
    ceng+=1
    
# 逻辑
ceng = 1
while ceng <= 5:
    count = 1
    while count <= ceng:
        print('*',end='')
        count += 1
    print()
    ceng += 1
```

####  10. 字符串

+ 常量

  ```python
  s1 = 'abc'
  s2 = "abc"
  s3 = '''abc'''
  print(id(s1),id(s2),id(s3))
  
  s1: 2128137317424
  s2: 2128137317424 
  s3: 2128137317424
      
  # 三引号占用的内存空间与单双引号不同
  
  print(s1==s2) # 比较的是内容 True
  print(s1 is s2) # 比较的是地址 True
  ```

+ 变量

  ```python
  s1 = input('请输入:')
  s2 = input('请输入:')
  print(s1==s2) # True
  print(s1 is s2) # False ,常量是True， input()底层做了处理，所以最后地址是不一样的
  ```

+ 切片使用

  ```python
  filename = 'picture.png'
  
  filename[5] # 从0 开始 取第 5 位
  
  filename[0:5] # 取出 5 位
  
  filename[::-1] # 倒叙输出
  
  ```

+ 字符串的内置方法

  ```python
  # 大小写相关
  
  str = 'abc bb'
  print(str.capitalize()) # 首字母大写 Abc bb
  print(str.title()) #  单词的每个首字母大写 Abc Bb
  print(str.upper()) # 所有字母大写 ABC BB
  print(str.lower()) # 所有字母小写  abc bb
  
  ```

+ 随机数应用(验证码)

  ```python
  
  # 验证码案例
  code = ''
  import random
  s = 'QWERTYUIOPASDFGHJKLZXCBN'
  
  for i in range(4):
      ran = random.randint(1, len(s) - 1)
      code += s[ran]
  print(code)
  user_input = input('请输入验证码: ')
  if user_input.lower() == code.lower():
      print('验证码输入正确')
  else:
      print('验证码输入错误')
  ```

+ 查找相关的

  ```python
  # find()  rfind() lfind() index rindex() replace()
  
  str = 'abcd'
  print(str.find('e')) # 找不见返回 -1 ,找见输出起始位置
  print(str.rfind('e')) # 找不见返回 -1 ,找见输出起始位置
  
  # index() 找不见报异常
  # ValueError: substring not found
        
  ```

  ```python
  # rfind()
  x = path.rfind('/')
  filename = path[x+1::]
  print(filename)
  
  ```

  ```python
  # replace()
  
  replace(old,new[,max])
  
  # 将空格替换为 # 号
  s1 = 'indec lucy luks gooes'
  s2 = s1.replace(' ','#')
  print(s2)
  
  # 指定替换的做大次数
  s2 = s1.replace(' ','#',2)
  ```

+ 编码相关

  ```python
  # encode 编码
  
  # decode 解码
  
  # 解码编码
  msg = '人生苦短,我学 Python'
  # encode('指定编码') decode('')
  result = msg.encode('utf-8')
  print(result)
  
  decode =result.decode('utf-8')
  print(decode)
  
  ```

+ `endswith() startwith()`

  ```python
  
  应用: 文件上传 只能上传(jpg，png,bmp,gif)
      
  # 返回值都是布尔类型 True False  
  
  # endswith() 
  filename = 'python.png'
  result = filename.endswith('png') #  filename 是否以 png 结尾
  print(result) # True
  
  --------------------------------------------------------------------------------
  # startwith() 
  s = 'hello'
  result = s.startswith('he') # 判断是否以 he 开头
  print(result) # True 
  
  
  ```

+ `join`使用

  ```python
  # join
  new_str = '_'.join('abc') # 用符号连接字符串
  print(new_str) # a_b_c
  ```

  

+ 去除左右空格

  + 去除左边空格

    ```python
    # 去除左空格
    s = '   hello '
    s = s.lstrip()
    print(s+'1') # hello  1
    ```

  + 去除右边空格

    ```pytohn
    # 去除右空格
    s = '   hello '
    s = s.rstrip()
    print('a'+s+'1') # a   hello1
    ```

  + 去除左右两边的空格

    ```python
    # 同时去除空格
    s = '   hello  '
    s = s.strip()
    print('a'+s+'1') # ahello1
    
    ```

+ 分割字符串

  ```python
  # split('指定字符切割','分割次数 int ')
  s = 'hello world hello kitty'
  result = s.split(' ')
  print(result)
  
  # 结果是 列表
  # ['hello', 'world', 'hello', 'kitty']
  ```

+ 求取定个数(统计)

  ```python
  s = 'aaaaaaaaa'
  s.count('s')
  ```

  

####  11. 列表

+ 遍历列表

  ```python
  for i in range(len(movies)):
      print(movies[i])
  ```

+ 修改列表

  ```python
  branch = ['a','b','c']
  
  branch[0] = 0
  
  print(branch) # [0, 'b', 'c']
  ```

+ 列表元素删除

  ```python
  del branch[0]
  print(branch)
  
  # 删除相关
  remove()
  pop()
  clear()
  ```

+ 列表的切片操作

  ```python
  branch[1::]
  print(branch[1::])
  ```

+ 列表的函数使用

  + `append()`

    ```python
    # append() 末尾追加
    
    
    ```

  + `extend()`

    ```python
    # extend() 
    
    	+、  extends() 列表的合并
    
    ```

  + `insert()`

    ```python
    
    指定位置插入
    
    ```

+ 列表的排序

  ```python
  a = [100,1,5,20,45,11]
  
  # 默认升序
  sorted(列表)
  # print(sorted(a)) [1, 5, 11, 20, 45, 100]
  
  # 翻转
  sorted(a, reverse=True)
  # print(sorted(a, reverse=True)) [100, 45, 20, 11, 5, 1]
  ```

+ 冒泡排序

  ```python
  
  ```

+ 选择排序

  ```python
  
  ```

####  12 . 元组

```python
特点: 
    1. 定义的符号: ()
    2. 元组中的内容不可修改
    3. 关键字: tuple
    
    只能执行 查 的操作
    
```

```python
import  random
list1 = []
for i in range(10):
    ran = random.randint(1,20)
    list1.append(ran)
print(list1)
t = tuple(list1)
print(t)

[3, 9, 18, 17, 7, 19, 8, 14, 7, 15]
(3, 9, 18, 17, 7, 19, 8, 14, 7, 15)

# 使用列表进行增删改查

```

####  13. 字典

```python
# 空字典 dict1 = dict()
# 空列表 list1 = list()
# 空元组 tuple1 = tuple()
dict = {}
```

+ 增加

  ```python
  dict[key] = value;
  
  # 同名则为修改
  
  ```

+ 删除

  ```python
  del 字典名[key]
  
  对应的函数:
      字典名.remove('key') # 没有报错
      字典名.pop('key')
      字典名.clear()
      字典名.popitem()
  
      
  注意:
      pop([key,default])
      根据 key 删除字典中的键值对,返回值是 只要删除成功，怎返回键值对的值 value
      pop 的默认值,往往是在删除的时候没有找到对应的 key ，则返回 default 默认值
      
      popitem(): 随机删除字典中键值对(一般都是从末尾删除元素)
          
  ```

+ 修改

  ```python
  # 同名则为修改
  ```

+ 查询

  ```python
  dict[key]
  ```

+ 字典的拼接

  ```python
  update() 
  ```

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20210104101610.png">



+ 形式转换

  ```python
  fromkeys(seq)
  
  将 seq 转成字典的形式,如果没有指定默认的 value 则用 None
  
  list1 = ['a','b','c']
  
  new_dict = dict.fromkeys(list1);
  
  ```

####  14. 集合

+ 关键字

  ```python
  集合: set 关键字 无序不重复的元素
      
  作用: 不重复的特点
      
  ```

+ 声明集合

  ```python
  set() # 创建空集合,只能使用 set()
  ```

+ 应用

  ```python
  list1 = [1, 2, 3, 4, 1, 2, 3]
  newList = set(list1)
  print(newList) # {1, 2, 3, 4}
  
  ```

+ 增

  ```python
  s1 = set()
  # 增
  # 增加一个
      s1.add('add-01')
      s1.add('add-02')
      s1.add('add-03')
      print(s1) # {'add-03', 'add-01', 'add-02'}
  # 增加多个
  	update()
      t1 = ('a','b')
      s1.update(t1)
      print(s1) # 输出无序
  
  ```

+ 删

  ```python
  remove() # 存在删除,没有报错 keyValue
  pop() # 随机删除,在集合中删除第一个
  clear() # 清空
  
  dicard() # 类似remove() 在移除没有元素不报错
  
  
  ```

+ 改

+ 查

+ 可变和不可变

  ```python
  
  
  不可变: 对象指向的内存中的值是不可以改变
      
  不可变的类型: int str float 元组tuple
      
  ----------------------------------------------    
      
  可变的； 对象所指向的内存中的值是可以改变的
  
  可变类型: 字典dict  列表list
      
     
  ```

+ 类型转换

  ```python
  str()  int()  list()  dict()  set()  tuple()
  ```

  + `str`可转类型

    ```python
    int list set tuple
    
    ----------------------------  str--> int  --------------------
    
    s = '1234' # 字符串类型
    i = int(s) # 字符串转换为数字
    print(type(i)) # <class 'int'>
    
    -----------------------------  str--> list --------------------
    list1 = list(s)
    print(list1) # ['1', '2', '3', '4']
    
    -----------------------------  str--> set --------------------
    
    set1 = set(s)
    print(set1) # {'3', '4', '1', '2'}
    
    -----------------------------  str--> tuple --------------------
    tupl1 = tuple(s)
    print(tupl1) # ('1', '2', '3', '4')
    
    ```

  + `list`可转类型

    ```python
    set()  tuple() 可以转换成字典 [(key,value),()···]
    ```

  + `dict可转类型`

    ```python
    list
    ```

  + `tuple可转类型`

    ```python
    list
    ```

  + `set可转类型`

    ```python
    list
    ```

####  15. 函数

+ 函数简介

  ```python
  作用: 将重复的代码,封装到函数,只要使用直接找函数 函数可以增强代码的模块化和提高代码的重复利用率
      
  格式:
      def 函数名:
          pass
  ```

+ 拆包装包

  ```python
  装包: 把传递的参数,包装成一个集合,称之为“装包”
      
  拆包: 把集合参数,再次分解成单独的个体,称之为"拆包"
      
  # 封装一个求和函数
  def add(*args):
      sum = 0
      if len(args) > 0:
          for i in args:
              sum += i
          print(sum)
      else:
          print('没有元素可以计算')
  add()
  add(1,2,4,6,100)
  
  注意: 可变参数必须放在后面
  ```

+ 关键字参数

  ```python
  # 关键字参数
  def add(a,b=1):
      print(a+b)
  add(1,2) # 3  b=1 相当于默认值，后来的值会将其覆盖
  
  # 可变 值必须是 key=value
  def add(**args):
      pass
  
  调用函数时有 ** 叫拆包
  
  定义时有 ** 叫装包
  
  应用:
      def bb(a, b, *c, **d):
          print(a, b, c, d)
  
      bb(1, 2)  # 1 2 () {}
      bb(1, 2, 3, 4)  # 1 2 (3, 4) {}
      bb(1, 2, x=100, y=20)  # 1 2 () {'x': 100, 'y': 20}
  
  ```

+ 函数的返回值

  ```python
  return
  
  有 return 需要用变量接受
  ```

+ `global`问题

  ```python
  函数内部声明的变量,局部变量
  
  声明在函数外侧的变量是全局变量
  
  
  
  def fun():
      global name # 不修改全局变量,只是获取打印,但是如果要发生修改全局变量,则要在函数内部声明, global 变量名
      
  全局变量如果是不可变在函数中进行修改需要添加 global 关键字
  如果全局变量是可变的,在函数中修改的时候就不需要添加 global 
  ```

+ 嵌套函数

  ```python
  def func():
      # 声明变量
      n = 100  # 局部变量
      list1 = [2, 3, 45, 5]
  
      # 声明内部函数
      def inner_func():
          nonlocal n # 内部函数修改局部变量需要使用 nonlocal
          # 对 list1 的元素进行 +5 操作
          for index, i in enumerate(list1):
              list1[index] = i + n
          list1.sort()
          print(list1)  #  [102, 103, 105, 145]
      inner_func()
  func()
  
  内部函数的特点:
      1. 可以访问外部函数的变量
      2. 内部函数可以修改外部函数的可变类型的变量 比如: list1
      3. 内部函数修改全局的不可变变量时,需要在内部函数声明 global 变量名
      内部函数修改外部函数的不可变的变量时,需要在内部函数中声明； nonlocal 变量名
    	4. locals() 查看本地变量有哪些,以字典的形式输出
      globals() 可以查看全局变量有那些,以字典的形式输出(会出系统的一些键值对)
  ```

####  16. 闭包

+ 闭包的概念

  ```python
  在函数中提出的概念
  ```

+ 条件

  ```python
  1. 外部函数中定义了内部函数
  2. 外部函数是有返回值
  3. 返回值是: 内部函数域名
  4. 内部函数引用了外部函数的变量
  
  语法格式:
      def 外不函数():
          pass
      	def 内部函数():
              pass
          return 内部函数名
  ```

+ 闭包的应用

  ```python
  
  ```

+ 闭包的缺点

  ```python
  闭包的缺点: 
      1. 作用域没有那么直观
      2. 因为变量不会被垃圾回收所以有一定的内存占用问题
  ```

+ 闭包的作用

  ```python
  闭包的作用: 
      1. 可以使用同级的作用域
      2. 读取其他元素的内部变量
      3. 延长作用域
  ```

+ 闭包的总结

  ```python
  总结:
      1. 闭包似优化了变量,原来需要类对象完成工作,闭包也可以完成
      2. 由于闭包引用；额外部函数的局部变量,则外部函数的局部变量没有及时释放,消耗内存
      3. 闭包的好处,使代码变得简洁,便于阅读代码
      4. 闭包是理解装饰器的基础
  ```

####  17. 装饰器(重点)

+ 装饰器

  ```python
  特点: 
      1. 函数 A 是作为参数出现的(函数B就会接受函数A作为参数)
      2. 要有闭包的特点
  ```

  ```python
  
  # 定义一个装饰器 (含有闭包特点)
  def decorate(func):
      a = 100
  
      def wrapper():
          print('----------------------> 内部函数 输出')
          func()
          print('----------------------- 111111111111112222222222222', a)
      return wrapper
  
  # 使用装饰器
  @decorate
  def house():
      print('我是毛坯房······················')
  
  # 调用函数
  house()
  
  ```

+ 带参数的装饰器

  ```python
  *args,**kwargs 作为参数传递
  
  
  如果装饰器是多层的,谁距离函数最近就优先使用那个装饰器
  ```

####  18. 匿名函数

```python
def add(a,b):
    return a+b
f = add

s = lambda a,b:a+b

result = s(1,2)
```

<img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20210104145533.png">

+ 匿名函数作为参数

  ```python
  
  ```

+ `map()`

  ```python
  list1 = [1,4,7,6]
  result = map(lambda x:x if x%2==0 eldr x+1,list1)
  print(list(result))
  ```

+ `reduce()`

  ```python
  对列表中的元素进行加减乘除运算的函数
  ```

+ `filter()`

  ```python
  # 过滤出 大于 10 的数子
  list1 = [10, 20, 2, 3, 4, 6, 19]
  result = filter(lambda x: x > 10, list1)
  print(list(result))
  ```

+ 递归函数

  ```python
  普通函数: def func(): pass
  匿名函数: lambda 参数: 返回结果
  递归函数: 普通函数的一种表现形式
  ```

###  文件操作

+ 文件操作

  + 文件读取

    ```python
    import os
    # 以 txt 文件练习  其他读取 有 gbk 错误
    # 读取路径 print(os.getcwd()) D:\python就业视频\python基础
    stream = open(r'D:\python就业视频\python基础\hello.txt')
    container = stream.read()
    txt = stream.readable()  # 判断文件是否可读  True
    readLine = stream.readline()  # 读取一行
    lines = stream.readlines()  # 读取多行
    print(container, txt, readLine)
    ```

+ 文件写入

  ```python
  # mode = 'a' 
  stream = open(r'D:\python就业视频\python基础\hello.txt', 'w')
  print(stream.write('aaaaaaaaaaaaaaaa'))  # 覆盖源文件
  
  print(stream.writelines(str)) # 保留源文件 追加
  
  ```

+ 文件复制

  ```python
  with open(r'D:\python就业视频\python基础\hello.txt') as stream:
      container = stream.read()  # 读取文件
      with open(r'D:\python就业视频\hello.txt', 'w') as writeFile:
          writeFile.write(container)
          print('文件写入')
  ```

+ `os`模块

  ```python
  # 路径读取
  ```

###  异常机制

+ 异常

  ```python
  try:
      可能出现异常的代码
  except 类型1:
      如果有异常执行的代码
  except 类型1:
      如果有异常执行的代码
  ···
  finally:
      无论是否存在异常都会执行的代码
  ```

+ `try-except-else`结构:

  ```python
  
  ```

+ `try-finally`结构:

  ```python
  
  ```

+ 抛出异常(`126集`)

  ```python
  # 抛出异常
  def refister():
      username = input('请输入用户名: ')
      if len(username) < 6:
          raise Exception('我是抛出的异常···')
      else:
          print('输入的用户名是: ' + username)
  # 接受异常
  try:
      refister()
  except Exception as err:
      print(err)
      print('注册失败')
  else:
      print('注册成功')
  
  ```

###  列表推导式(`128集`)

+ 列表推导式

  + `[表达式 for 变量 in 旧列表] `

    ```python
    
    ```

  + `[表达式 for 变量 in 旧列表 if 条件]`

    ```python
    
    list1 = [10, 2, 4, 6, 90, 30, 60]
    # 取出 大于 10的数
    newList = [i for i in list1 if i >= 10]
    print(newList)
    ```

  + `if else`

    ```python
    dict1 = {'name': 'tom', 'salary': 5000}
    dict2 = {'name': 'lucy', 'salary': 8000}
    dict3 = {'name': 'jack', 'salary': 4500}
    dict4 = {'name': 'lily', 'salary': 3000}
    
    # if 薪资大于 5000 加 200,低于 5000 加 500
    
    newList = [person['salary'] + 200 if person['salary'] > 5000 else person['salary'] + 500 for person in list1]
    print(newList) # [5500, 8200, 5000, 3500] 
    ```

+ 字典推导式

  ```python
  # 集合推导式
  list1 = [1, 2, 1, 2, 3, 4, 5, 6, 4]
  set1 = {x for x in list1}
  print(set1) # {1, 2, 3, 4, 5, 6}
  ```

+ 集合推导式

  ```python
  dict1 = {'a': 'A', 'b': 'B'}
  newdict = {value: key for key, value in dict1.items()}
  print(newdict) # {'A': 'a', 'B': 'b'}
  ```

###  生成器

```python
在 python 中,这种一边循环一边计算的机制,称为生成器: generator

得到生成器的方式:
    1. 列表推导式
    2. 借助函数完成 (yield)
    
    注意: 只要函数中出现；了 yield 关键字,说明函数就不是函数,就是生成器
```



```python

步骤:
    1. 定义一个函数,函数中使用 yield 关键字
    2. 调用函数,接受调用的结果
    3. 得到的结果就是生成器
    4. 借助于 next()
    
---------------------------------------------------------------------------------

def fun():
    n = 0
    while True:
        n += 1
        yield n
g =  fun()
# next()  __next__()
print(next(g))
```

###  面向对象

+ 面向对象

  ```python
  
  ```

+ 类

  ```python
  class 类名[(父类)]:
      属性: 特征
      方法: 动作
  ```

+ 构造器

  ```python
  
  ```

+ 对象方法

  ```python
  
  class Phone:
      def call(self):
          print('call············')
          
          
  phone = Phone()
  # 通过对象调用的方法
  phone.call()
  ```

+ 类方法

  ```python
  特点: 
      1. 定义需要依赖装饰器 @classmethod
      2. 类方法中参数不是一个对象,而是类
      3. 类方法中只可以使用类属性
      4. 类方法中是否使用普通方法? 不能
  类方法的作用:
      因为只能访问类属性和类方法,所以可以在对象创建之前,如果需要完成一些动作(功能)
  
  class Dog:
      def __index__(self,nikename):
          self.nikename = nikename
      def run(self):
          print('{}在院子里跑来跑去'.format(self.nikename))
      def eat(self):
          print('吃饭饭····')
         # self.run() # 类中方法的调用 需要通过 self.方法名()
      @classmethod
      def test(cls):
          print('cls')
  ```

+ 静态方法

  ```python
  
  ```

  + 私有属性

    ```python
    class Phone:
        __brand = 'Note3'
    ```

    

###  正则表达式

+ 正则表达式的定义

  ```python
  正则表达式是对字符串的一种逻辑公式,就是用事先定义好的一些特殊字符,以及这些特殊字符组成规则的字符串
  正则表达式是对字符串和特殊字符操作的一种逻辑公式
  ```

+ 正则表达式的作用和特点

  ```python
  给定一个正则表达式和另一个字符串,达到一定目的
  
  1. 给定的字符串是否符合正则表达式的过滤逻辑(称作匹配)
  
  2. 可以通过正则表达式,从字符串中获取我们想要的特定部分
  
  正则表达式的特点是:
      1. 灵活性,逻辑性和功能性非常强
      2. 可以迅速的用极简单的方式达到字符串的复杂控制
    
  ```

+ 方法

  ```python
  # 使用正则 re 模块的方法: match 从头开始匹配,如果不成功则就返回 None
  
  # 使用正则 re 模块的方法: search  进行正则字符串匹配方法,匹配的是整个字符串 输出索引位置
  
  # group()
  
  # sub(’正则表达式‘,'新内容','替换')
  
  # split() 切割
  ```

  + `re.match`与`re.search`的区别

    ```python
    
    re.match 只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回 None，
    
    re.search 匹配整个字符串，直到找到一个匹配。
    
    ```

  + 检索和替换

    ```python
    re 模块提供了 re.sub 用于替换字符串中的匹配项
    
    # 语法
    	
        re.sub(pattern, repl, string, count=0, flags=0)
    
        pattern : 正则中的模式字符串。
        repl : 替换的字符串，也可为一个函数。
        string : 要被查找替换的原始字符串。
        count : 模式匹配后替换的最大次数，默认 0 表示替换所有的匹配。
        flags : 编译时用的匹配模式，数字形式。
    ```

  + `compile`函数

    ```python
    compile 函数用于编译正则表达式，生成一个正则表达式（ Pattern ）对象，供 match() 和 search() 这两个函数使用。
    ```

  + `findall`:

    ```python
    在字符串中找到正则表达式所匹配的所有子串，并返回一个列表，如果没有找到匹配的，则返回空列表。
    
    注意: match 和 search 是匹配一次 findall 匹配所有。
    ```

  + `split`

    ```python
    split 方法按照能够匹配的子串将字符串分割后返回列表
    ```

+ 正则预定义

  ```python
  \A: 表示从字符串的开始处匹配
  \Z: 表示从字符串的结束处匹配，如果存在换行，只匹配到换行前的结束字符串。
  \b: 匹配-一个单词边界，也就是指单词和空格间的位置。例如，’py\b' 可以匹配’ python” 中的’ py’，但不能匹配”oenpyx1"中的 'py'
  \B: 匹配非单词边界。’ py\b’可以匹配”openpyx1"中的’ py'，但不能匹配”python"中的’ py'
  \d: 匹配任意数字，等价于[0-9] 。
  \D: 匹配任意非数字字符，等价于[ \d]。
  \s: 匹配任意空白字符，等价于[\t\n\r\f] 
  \S: 匹配任意非空白字符，等价于[^\s]。
  \w: 匹配任意字母数字及下划线，等价于[a-zA-Z0-9_ ] 
  \W: 匹配任意非字母数字及下划线，等价于[^ \w]
  \\: 匹配原义的反斜杠\
  ```

+ 总结

  ```python
  . 任意字符除(\n)
  ^ 开头
  $ 结尾
  [] 范围
  
  量词:
      * >=0
      + >=1
  	? 0,1
      {m} 固定 m 位
      {m,} >=m
      {m,n} phone>=m  phone<=n(范围内的大小)
      
  
  ```

  

+ 起名

  ```python
  起名方式: (?P<name>正则)
      
  分组: ()
      
      分组可以使用 group(n组) 获取
  ```

  