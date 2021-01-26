---
title: Flask-Proj
date: 2021-01-22 13:10:06
tags:
- Python
- Linux
categories: Flask
top_img:
---

###  Flask-Proj

####  虚拟环境及包的安装

+ 创建虚拟环境

+ 下载`Flask`

  ```bash
  pip install flask=='版本号' / pip install flask(自行选择版本号)
  ```

+ `Flask-Proj`开发

+ `requirements`文件

  ```bash
  Python 项目中必须包含一个 requirements.txt 文件 ,用于记录所有依赖包及其精确的版本号,以便在新环境中进行部署操作
  ```

+ 在虚拟环境中使用以下命令将当前虚拟环境中的依赖包以版本号生成至文件中

  ```bash
  pip freeze > requirements.txt
  ```

+ 当需要创建这个虚拟环境的完全副本,可以创建一个新的虚拟环境,并执行以下命令

  ```bash
  pip install -r requirements.txt
  ```



###  项目(Flask_Proj)

####  运行测试

+ 运行

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/proj.png">

+ 配置字符集

  ```bash
  
  app.py:
  	# 配置字符集
  	# -*- coding:utf-8 -*-
  ```


+ 端口号修改

  ```python
  app.run(port='端口号')
  ```

+ 配置文件

  ```python
  # 新建 settings.py, 写入以下配置信息
  
  ENV = 'development' # 开发环境
  DEBUG = True # 开启 debug 模式
  
  # 在 app 导入
  import settings
  
  # 在 app 定义下写如下信息
  app.config.from_object(settings)
  
  
  ```

+ 终端启动方式

  ```bash
  python/python3 app.py
  ```

+ 配置信息无效可通过图像化界面开启`DEBUG`

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/debug.png" width="600">

+ 修改后

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/settingsDebug.png" width="600">

####  路由请求方式限定

+ `POSTMAN` 进行测试

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/postman.png">

+ 添加新的请求方式

  ```python
  # 默认支持 GET 请求
  @app.route('/',methods = ['GET','POST'])
  ```

+ 路由的请求与相应

  ```bash
  response 响应:
  	200 - 请求成功
  	404 - 请求的资源(网页等)不存在
  	500 - 内部服务器错误
  	302 - 重定向
  	301 - 资源(网页等)被永久转移到其他 URL
  ```

+ `Flask`路由和变量规则

  ```python
  # 路由 route
  这个装饰器其实就是将 rule 字符串跟视图函数进行了数据绑定,通过 add_url_rule() 实现绑定
  
  # 等效写法
  # ------------------- 装饰器 ------------------------------
      @app.route('/',methods = ['GET','POST'])
      def hello_world():
          return 'Hello World!'
   # -------------------- add_url_rule() -------------------
      def index():
      	return '<h1><font color="red">index Text</font></h1>'
  	app.add_url_rule('/index', view_func = index)
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/add_url_rule.png">

  +  路由的变量规则

    ```bash
    通过把 URL 的一部分标记为 <variable_name> 就可以在 URL 中添加变量。标记的 部分会作为关键字参数传递给函数。通过使用 <converter:variable_name> ，可以 选择性的加上一个转换器，为变量指定规则。
    ```

    ```python
    # 默认 str
    @app.route('/getValue/<key>') # 默认 str 不需要添加数据类型
    def getValue(key):
        return data.get(key)
    
    # int
    
    # int 类型
    @app.route('/add/<int:num>')  # 默认 str 不需要添加数据类型
    def add(num):
        result = num + 10
        return str(result)
    
    ```

  + 转换器类型：

    | `string` | （缺省值） 接受任何不包含斜杠的文本 |
    | -------- | ----------------------------------- |
    | `int`    | 接受正整数                          |
    | `float`  | 接受正浮点数                        |
    | `path`   | 类似 `string` ，但可以包含斜杠      |
    | `uuid`   | 接受 UUID 字符串                    |
  
  +  路由的斜杠问题（唯一的 `URL` 问题）
  
     ```python
     ‘/index/’ 
     
     路由中没有斜杠,浏览器访问会报错
     
     路由中有斜杠,访问时没有则会自动重定向
     ```
  
  + `return`
  
    ```python
    return 后面返回的字符串其实也是做了一个 response 对象的封装。最后的返回结果还是 response 对象。
    ```
  
    

###  Jinja2 模板引擎

####  渲染模板函数

1. `Flask` 提供的 `render_template`函数封装了该模板引擎

2.  `render_template` 函数的第一个参数是模板的文件名,后面的参数都是键值对,表示模板中变量对应的真实值。

   ```python
   # 导入 render_template
   from flask import Flask,render_template
   
   # 使用 render_template
   @app.route('/index', methods = ['GET', 'POST'])
   def index():
       return render_template('index.html')
   ```

   <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/Jinja2.png" width="600">

3. 变量代码块

   ```jinja2
   {# 注释语法 #}
   {{ value1 }}
   
   {# 通常,模板中使用的变量名和要传递的数据的变量名保持一致。 #}
   
   ```

   <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/jinjaStr.png" width="600">

4. 控制代码块

   + `for`循环

     ```jinja2
     {% for play in my_list %}
         <h1> {{ play }} </h1>
     {% endfor %}
     ```

     <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/forjinja.png">

   + `if`

     ```jinja2
     {% if num>3 %}
     {{ num} }}
     {% endif %} 
     ```

5.  内建过滤器

   + 含义

     ```jinja2
     过滤器:
     
     	过滤器的本质就是函数m有时候我们不仅仅要输出变量的值,我们还需要改变变量的显示甚至格式化,运算等等，而在模板中是不能直接
     	
     调用 Python 中的某些方法m那么就用到了过滤器。
     
     ```

   + 使用方式

     ```jinja2
     
     变量名 | 过滤器
     
     {{ variable | filter_name(*args) }} 
     
     {# 如果没有任何参数传递给过滤器,则可以省略括号 #}
     
     {{ variable | filter_name }}
     
     {# 链式调用 #}
     
     {{ variable | filter_name1 | filter_name2 | ··· }}
     
     https://www.bilibili.com/video/BV17W41177oE?p=14
     
     ```


###  Web 表单

```jinja2
在 Flask 中,为了处理 web 表单,我们一般使用 Flask-WTF 扩展,它封装了 WTForms,并且它有验证表单数据的功能。
```



