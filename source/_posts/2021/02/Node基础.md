---
title: Node基础
date: 2021-02-04 09:21:41
tags:
- Node
- Javascript
categories: Node
top_img:
cover:
---

### Node基础

####  命令行基础

+ 常用指令
  1. `Win+r`调出`DOS`窗口

  2. `cd`目录名 进入指定目录

  3. `md`目录名 创建一个文件夹

  4. `rd` 目录名 删除一个文件夹

+ 目录

  1. `.`表示当前目录
  2. `..`表示上一级目录

+ 环境变量

####  进程和线程

> 
>
> 进程: 进程负责为程序的运行提供必备的环境
>
> 线程: 线程计算机中的最小的计算单位，线程负责执行进程中的程序
>
> Node的服务器是单线程的: Node 处理请求时是单线程,但是在后台拥有一个I/O线程池
>
> 

####  Node 简介

+ 简介

  ```javascript
  1. Node.js 是一个能够在服务器端运行 Javascript 的开放源代码、跨平台 Javascript 运行环境。
  2. Node 采用Google开发的 V8 引擎运行 js 代码，使用事件驱动、非阻塞和异步I/O模型等技术来提高性能、可优化应用程序的传输量和规模。
  ```



####  Node 安装使用

+ 安装  <a href="https://nodejs.org/en/">点击前往 Node 官网</a>

+ 检测

  ```javascript
  node --version
  ```

  + 成功显示版本号

  + 安装失败错误代码`2502,2503`

    1. 安装权限不足
       + 以管理员身份运行`powershell: windows+x `
       + 输入运行安装包命令`msiexec/package [ D:\Program Files\nodejs\replace-your-node-path  node-v10.13.0-x64.msi your-node-version`

    2. 安装验证失败

       ```bash
       添加系统环境变量
       
       找到系统中的 node.exe 的路径添加系统环境变量后退出执行:
       
       windows+r: cmd  node -v
       
       ```

       <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/nodepath.png" width="600">

+ 使用

  ```javascript
  node 文件名.js
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/helloNode.png" width="400">

+ 模块化

  ```javascript
  - 在 Node 中 一个 js 文件就是一个模块
  - 在 Node 中,每一个 js 文件中的 js 代码都是独立运行在一个函数中
  
  模块分成两大类:
      核心模块:
          1. 由 Node 引擎提供的模块
          2. 核心模块的标识就是模块的名称
      文件模块:
  	1. 由用户自己创建的模块
          2. 文件模块的标识就是文件的路径(绝对路径、相对路径)
  			
  			相对路径使用  . 或 .. 开头
  ```

+ 外部模块引入

  ```javasc
  在 node 模块中,通过 require() 函数来引入外部的模块
      
      require() 可以传递一个文件的路径作为参数, node 将会自动根据该路径来引入外部模块
  
      使用 require() 引入模块以后,该函数会返回一个对象，这个对象代表是引入的模块
      
      exports 向外部暴露变量和方法
  	只需要将需要暴露给外部的变量或方法设置为 exports 的属性
  	
  ```

+ `exports`使用

  ```javascript
  A.js: exports.x = 'Hello World 模块的 x '
  
  B.js: 
  
  	引入 A 模块: var md = require('file-path/A');
  					console.log(md.x) // B模块输出: Hello World 模块的 x
  
  exports 是 module.exports 的别名(地址引用关系),导出对象最终以 module.exports 为准。
  
  ```

+ `global`

  ```javascript
  在 node 中有一个全局对象 global 它的作用和网页中 window 类似
  
  在全局中创建的变量都会作为 global 的属性保存
  
  在全局中创建的函数都会作为 global 的方法保存
  
  当 node 执行模块中的代码时,它会首先在代码的最顶端,添加如下代码
  function(exports,require,modelm__filename,__dirname{
            
            在代码最底部,添加如下代码
            }
  ```

#### 包（package）

+ `package`
  1. `CommonJS` 的包规范允许我i们将一组相关的模块泽合到一起，形成一组完整的工具
  2.  `CommonJS` 的包规范由包结构和包描述文件两个部分组成

+ 包结构: 用于组织包中的各种文件

  ```javascript
  包实际上就是一个压缩文件,解压后还原为目录。符合规范的目录,应该包含如下文件:
  
      - package.json 描述文件
      - bin 可执行二进制文件
      - doc 文档
      - test 单元测试
       
  ```

+ 包描述文件: 描述包的相关信息，以供外部读取分析

+ `npm(Node Package Manager)`

  ```javascript
  npm search package-name // 搜索
  
  npm install package-name // 下载
  
  ```

+ 配置`cnpm`

  ```javascript
  // 安装 cnpm
  npm install -g cnpm --registry=https://registry.npm.taobao.org
  
  // 常用命令
  安装包
  cnpm i <pkg>  或者 cnpminstall <pkg>  或者  cnpm i <pkg>@<version>  或者  cnpminstall <pkg>@<version>
  
  卸载包
  cnpm uninstall <name> 或者 cnpm uninstall <name>@[<version>]
  
  查看当前项目下的包列表
  cnpm ls
  
  查看全局包列表
  cnpm ls －g
  
  清理缓存
  cnpm cache clean
                                                  
  ```

###  Node

####  系统模块



#####  读写文件

+ `fs`

  ```javascript
  
  fs 是 file-system 的简写 就是文件系统的意思
  
  在 node 中如果想要进行文件操作，就必须引入 fs 这个核心模块
  
  fs.readFile('文件路径/文件名称',['文件编码'],callback)
  ```

+ 文件读取

  ```javascript
    第一个参数就是要读取的文件路径
    第二个参数就是回调函数
          成功
              data 数据
              error null
          失败
              data null
              error 错误对象
  ```

  ```javascript
  // 引入 fs 模块
  var fs = require('fs');
  // 文件读取
  fs.readFile("./b.txt", function (error, data) {
    if (error) {
      console.log("读取文件失败");
      return;
    } else {
      console.log(data.toString());
    }
  ```

+ 写文件

  ```javascript
  第一个参数: 文件路径
  第二个参数: 文件内容
  第三个参数: 回调函数
  
  error
  	成功: 
  		文件写入成功
          error --> null
  	失败: 
  		文件写入失败
          error 就是错误对象
     
   fs.writeFile('文件路径/文件名称','数据',callback);

  ```
  
  ```javascript
  var fs = require('fs');
  fs.writeFile('./file-name','write-content',function(error){
      if(error){
          console.log('写入失败');
      }else{
          console.log('文件写入成功···');
      }
})
  ```

+ 系统模块`path`路径操作

  ```javascript
  path.join('路径','路径',····)
  ```

  ```javascript
  // 主要是由于系统不同使用的路径分隔符不同
  // 拼接如下路径 public/img/avatar
  
  const path = require("path");
  const filepath = path.join("public", "img", "avatar");
  
  console.log(filepath);
  
  ```

+ 相对路径、绝对路径

  ```javascript
  1. 大多数情况下使用绝对路径,因为相对路径有时候相对的是命令行工具的当前工作目录
  2. 在读取文件或者设置文件路径时都会选择绝对路径
  3. 使用 __dirname 获取当前文件所在的绝对路径
  ```

+ 第三方模块

  ```javascript
  别人写好的m具有特定功能,我们能直接使用的模块即第三方模块，由于第三方模块都是由多个文件组成并且被放置在一个文件夹中,所以又名包名。
  
  https://www.npmjs.com/
  ```

  

####  简单的 http 服务



+ 搭建简单的服务器

  ```javascript
  // 加载 http 核心模块
  var http = require("http");
  // 使用 http.createServer() 方法创建一个 Web 服务器 返回一个 server 实例
  var server = http.createServer();
  
  /*
      当客户端请求过来,就会自动触发服务器的 request 请求事件,  然后执行第二个参数: 回调处理
  */
  server.on("request", function (request, response) {
    console.log("收到客户端的请求了··" + request.url);
  
    /*
        response 对象有一个方法 write 可以用来给客户端发送响应数据
        write 可以使用多次,但是最后一定要使用 end 来结束响应 否则客户端会一直等待
        */
    response.write("响应···");
    // 告诉客户端 我的话说完了 你可以直接呈递给用户
    response.end();
  });
  
  // 绑定端口号
  server.listen(3031, function () {
    console.log("服务器启动成功，可以通过 http://127.0.0.1:3000/ 进行访问了");
  });
  
  ```

+ 请求路径获取响应

  + 普通文本响应

    ```javascript
    // 引入 http 模块
    var http = require("http");
    // 创建 server
    var server = http.createServer();
    // 发送
    server.on("request", function (request, response) {
        console.log("收到请求了: " + request.url);
        // 根据不同的请求的路径,响应不同的内容
        var url = request.url;
        if (url === "/") {
            response.end("index Page");
        } else if (url === "/login") {
            response.end("user login");
        } else if (url === "/register") {
            response.end("user register");
        } else {
            response.end("response ·····");
        }
    });
    // 绑定端口号
    server.listen(3101, function () {
        console.log("服务器启动成功···可以通过127.0.0.1:3031 来访问了");
    });
    
    ```

  + 响应 `json`数据类型

    ```javascript
    // 引入 http 模块
    var http = require("http");
    // 创建 server
    var server = http.createServer();
    // 发送
    server.on("request", function (request, response) {
        // 配置响应编码
        response.setHeader("Content-Type", "[text/plain 根据类型变化可选];charset=utf-8");
        console.log("收到请求了: " + request.url);
        // 根据不同的请求的路径,响应不同的内容
        var url = request.url;
        // 定义json 类型数据
        var products = [
            {
                brand: "xiaomi",
                price: 6699,
                color: "blue",
            },
            {
                brand: "iPhone",
                price: 9988,
                color: "purple",
            },
            {
                brand: "huawei",
                price: 9988,
                color: "blue",
            },
        ];
        // 响应的内容只能是 二进制数据或者字符串
        if (url === "/products") {
            console.log(JSON.stringify(products));
            response.end(JSON.stringify(products));
        }
    });
    // 绑定端口号
    server.listen(3101, function () {
        console.log("服务器启动成功···可以通过127.0.0.1:3031 来访问了");
    });
    
    ```

+ 常见`Content-Type`类型

  ```javascript
  常见的媒体格式类型如下：
      text/html  HTML格式
      text/plain 纯文本格式
      text/xml  XML格式
      image/gif gif图片格式
      image/jpeg jpg图片格式
      image/png png图片格式
  ```

  