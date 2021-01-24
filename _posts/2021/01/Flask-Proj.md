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

+ 在虚拟环境中使用一下命令将当前虚拟环境中的依赖包以版本号生成至文件中

  ```bash
  pip freeze > requirements.txt
  ```

+ 当需要创建这个虚拟环境的完全副本,可以创建一个新的虚拟环境,并执行一下命令

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

  ```bash
  port='端口号'
  ```

+ 配置文件

  ```python
  # 新建 settings.py, 写入一下配置信息
  
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
  + 路由的变量规则

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

