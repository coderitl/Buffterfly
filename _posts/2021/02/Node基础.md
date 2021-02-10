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

  

####  第三方模块

+ 第三方模块`nodemon`,很有必要安装使用,修改内容将会实时刷新,无需重新启动

  ```bash
  # 下载 
  npm install nodemon -g
  
  #检测安装
  nodemon -v
  
  # 使用
  nodemon node-fils-name.js
  
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/nodemon.png" width="600">

+ 第三方模块`nrm`

  ```bash
  nrm(npm registry manager): npm 下载地址切换工具 npm 默认下载地址在国外,国内下载速度慢
  
  # 安装 nrm
  npm install nrm -g
  # 显示可用下载列表
  nrm list
  # 使用可用 镜像
  nrm use taobao
  #  * 代表当前在用镜像
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/nrm.png" alt="下载失败" width="600">

  + 解决方案(未尝试)

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/nrmresult.png">

+ 第三方模块`gulp`

  1. `gulp`能做什么

     ```bash
     项目上线 HTML CSS JS 文件压缩
     语法转换(es6,less)
     公共文件抽离
     ```

  2. `gulp`使用步骤

     + 项目中下载`gulp`库文件,要使用项目中根目录下执行`npm install gulp`

     + 在项目根目录下新建`gulpfile.js`文件，只能是这个文件名
     + 重构项目的文件夹结构 `src` 目录放置源代码文件 `dist`目录放置构建后文件
     + 在 `gulpfile.js`文件中编写任务
     + 在命令行工具中执行`gulp`任务

  3.  `gulp`中提供的方法

     + `gulp.src()`获取任务要处理的文件
     + `gulp.desc()`输出文件
     + `gulp.task()`建立gulp任务
     + `gulp.watch()`监控文件的变化

     + 使用`gulp`

       <img src='https://gitee.com/wang_hong_bin/repo-bin/raw/master/gulp.png'>

       ```javascript
       " npm install gulp "
       
       // 引入 gulp
       const gulp = require("gulp");
       // 使用 gulp.task() 方法建立任务
       // 参数: 1.任务的名称
       // 参数: 2. 任务的回调 
       gulp.task("first", () => {
         // 获取要处理的文件
         gulp
           .src("./src/css/index/style.css") // src: 目录自定义 自动会生成
           // 将处理后的文件输出到 dist 目录，dest输出
           .pipe(gulp.dest("./dist/css/index")); // dist: 目录自定义 自动会生成
       });
       // 全局安装命令工具 npm install gulp-cli -g
       ```

       + 下载命令工具,全局安装(全局安装: 多个项目都会使用, 库文件则不同)

         ```bash
         # 安装
         npm install gulp-cli -g
         # 检测
         gulp -v
         # 使用
         gulp task-name [Eg. first]
         ```

         <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/gulpfirst.png">

     + `gulp`插件
       1. `gulp-htmlmin` html 文件压缩
       2.  `gulp-csso`压缩css
       3. `gulp-babel`JavaScript语法转换
       4. `gulp-less`语法转换
       5. `gulp-uglify`压缩混淆 JavaScript
       6. `gulp-file-include`公共文件包含
       7. `browsersync` 浏览器实时同步

     + 使用插件

       ```bash
       下载插件文档: https://www.npmjs.com/package/gulp-htmlmin
       
        npm install --save gulp-htmlmin
        
       ```

       + 新建压缩 html 任务(先了解,等待后续补充)

         ```javascript
         // 引入 gulp
         const gulp = require("gulp");
         // 引用插件
         const htmlmin = require("gulp-htmlmin");
         
         
         // html 任务 压缩 html
         // 建立任务
         gulp.task("htmlmin", () => {
           return (
             gulp
               // 获取处理任务路径
               .src("./src/*.html")
               // 压缩 html 文件中的代码 collapseWhitespace 压缩空格? true 是 pipe( 任务事件 )
               .pipe(htmlmin({ collapseWhitespace: true }))
               // 输出
               .pipe(gulp.desc("dist"))
           );
         });
         ```

       + 原 `html `文件格式

         <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/yuanhtml.png" width="600">

       + 压缩后

         <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/htmlmin.png">

       + `构建`任务

         ```javascript
         // 构建任务  所有任务 通过 gulp default 全部执行
         gulp.task('default',['htmlmin','first']);
         
         ```

         

####  package.json

> 
>
> `node_modules` 无需传输，使用`npm install ` 会自动前往 `package.json` 寻找依赖下载
>
> 项目描述文件,记录当前项目的项目信息,例如: 项目名称 版本 作者` github` 地址 当前项目依赖了那些第三方模块 使用 `npm init -y` 生成
>
> 

+ `npm init -y`

  ```bash
  {
    "name": "node-day03", 
    "version": "1.0.0",
    "description": "",
    "main": "gulp-demo.js",
    "dependencies": { # 项目依赖
      "gulp": "^4.0.2",
      "gulp-file-include": "^2.3.0",
      "gulp-htmlmin": "^5.0.1"
    },
    "devDependencies": {}, # 开发依赖 --save 
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [],
    "author": "",
    "license": "ISC" # 开放源代码协议
  }
  
  ```

+ 开发依赖
  1. 在项目的开发阶段需要依赖，线上运营阶段不需要依赖第三方包，称为开发依赖
  2.  使用 `npm install` 包名 `--save-dev` 命令将包名添加到`package.json`文件的 `devDependencies`字段中

+ `package-lock.json`文件的作用
  1. 锁定包的版本,确保再次下载时不会因为包版本不同产生问题
  2.  加快下载速度, 因为该文件中已经记录了项目所依赖第三方包的树状结构和包的下载地址，重新安装时只需下载即可,不需做额外工作

+ 命令别名

  ```javascript
  package.json: 
      "scripts": {
          "test": "echo \"Error: no test specified\" && exit 1",
          "build": "nodemon app.js"
        }
         
  
  "build": "命令"
  
  "build": "nodemon app.js"
  
  # 执行
  npm run 别名 Eg. npm run build
  
  ```



####   服务器端基础概念

+ 网站服务器

  ```bash
  能够提供网站访问服务的机器就是网站服务器,它能够接受客户端的请求,能够对请求做出响应。
  ```

+ URL

  ```bash
  统一资源定位符,又叫 URL(uniform ResourceLocator) 是专门标识 Internet 网上资源位置而设的一种编址方式
  ```

+ URL 的组成

  ```bash
  输出协议://服务器 ip或域名:端口/资源所在位置标识
  
  https://lovobin.github.io:80/2021/02/Node%E5%9F%BA%E7%A1%80/
  
  http: 超文本传输协议, 提供了一种发布和接受 HTML 页面的方法
  
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



####  HTTP 协议

+ http 协议的概念

  ```bash
  超文本传输协议(英文: HyperText Transfer Protocol 缩写: HTTP) 规定了如何从网站服务器传输超文本到本地浏览器,它基于客户端服务器加构工作,是客户端服务器加构工作,是客户端和服务器端请求和应答的标准。
  ```

+ 报文

  ```bash
  在 HTTP 请求和响应的过程中传递的数据块就叫报文m包括要传送的数据和一些附加信息,并且要遵循规定好的格式。
  ```

+ 请求报文

  1. 请求方式

     + `GET`
     + `POST`

  2.  请求地址

     ```javascript
     server.on('request',(req,res)=>{
         req.headers // 获取请求报文
         req.url // 获取请求地址
         req.method // 获取请求方式
     })
     ```

     

####  HTTP 请求与响应处理

+ GET 参数请求处理

  ```javascript
  // http请求与响应.js
  const http = require("http");
  const server = http.createServer();
  // 处理 url
  const url = require("url");
  // req: request res: response
  server.on("request", (req, res) => {
    res.writeHeader(200, {
      "content-type": "text/plain;charset=utf8",
      hello: "world",
    });
  
    // 请求参数处理 http://127.0.0.1:3031/?username=zhangsan&age=18
    console.log(req.url); // /?username=zhangsan&age=18
    // 字符串截取可以获取参数
    // 内置模块
    console.log(url.parse(req.url));
    /*
      1. 要解析的 url 地址
      2. 将查询的参数解析成对象形式
  
      url.parse(req.url,true)
    */
    let params = url.parse(req.url, true).query;
    console.log("params: ", params);
  
    console.log("params-username:", params.username, "params-age:", params.age); // zhangsan 18
    res.end("请求成功");
  });
  server.listen(3031, (error) => {
    console.log("可以通过 127.0.0.1:3031/ 来访问服务器了····");
  });
  
  
  // 路径判断问题
  let {query,pathname}=url.parse(req.url,true);
  console.log(query.username,query.age);
  if(pathname=='/index' || pathname=='/'){
      res.end('index home')
  }
  
  ```

  

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/getParse.png" width="400">

+ POST 参数请求处理

  ```javascript
  // post请求参数.js
  // http请求与响应.js
  const http = require("http");
  const server = http.createServer();
  // 处理请求参数模块 post 请求转换为 对象数据
  const queryString = require("querystring");
  // req: request res: response
  server.on("request", (req, res) => {
    // 编码处理
    res.writeHeader(200, {
      "content-type": "text/plain;charset=utf8",
    });
    // post 参数是通过事件的方式接受的
    // data 当请求参数传递的时候触发 data 事件
    // end 当参数传递完成的时候触发 end 事件
    // username=aidou&password=123
    let postParams = "";
    req.on("data", (params) => {
      postParams += params;
    });
    req.on("end", () => {
      console.log(postParams);
      let querystr = queryString.parse(postParams);
      console.log(querystr); // { username: 'aidou', password: '123' }
    });
    res.end("ok");
  });
  server.listen(3031, (error) => {
    console.log("可以通过 127.0.0.1:3031/ 来访问服务器了····");
  });
  
  ```

  

####  路由

> 路由是指客户端请求地址与服务器端程序代码的对应关系

+ 路由处理

  ```javascript
  const http = require("http");
  const server = http.createServer();
  const url = require("url");
  server.on("request", (req, res) => {
    res.writeHeader(200, {
      "content-type": "text/html;charset=utf8",
    });
    // 获取请求方式
    const method = req.method.toLowerCase();
    console.log(method); // GET---  toLowerCase() ---> get
    // 获取请求地址
    const pathname = url.parse(req.url).pathname;
    console.log("pathname: ", pathname); // pathname:  /index
    if (method == "get") {
      if (pathname == "/" || pathname == "/index") {
        res.end("<h1> return get index home page </h1>");
      } else {
        res.end("<h1>Not Found GET</h1>");
      }
    }
    if (method == "post") {
      if (pathname == "/" || pathname == "/index") {
        res.end("<h1> return post index home page </h1>");
      } else {
        res.end("<h1>Not Found POST</h1>");
      }
    }
  });
  
  server.listen(3031, (error) => {
    console.log("ok");
  });
  ```

+ 静态资源访问

  ```javascript
  服务器端不需要处理,可以直接响应给客户端的资源就是静态资源，例如 css javascript image 文件等
  ```

  + 获取访问路径
  
    ```javascript
    # 获取 pathname  
    url.parse(req.url).pathname
    ```
  
  + 获取当前文件的绝对路径
  
    ```javascript
    # path 模块
    
    path.join(__dirname, "public" + pathname)
    
    ```

+ 静态资源读取

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/pathnameDefault.png">

  ```javascript
  # app.js
      const http = require("http");
      const url = require("url");
      const path = require("path");
      const fs = require("fs");
  
      const server = http.createServer();
  
      server.on("request", (req, res) => {
        res.writeHead(200, {
          "content-type": "text/html;charset=utf8",
        });
        // 响应文件路径
        let pathname = url.parse(req.url).pathname;  
        
          #   pathname = pathname == "/" ? "/default.html" : pathname; 更新显示判断
          
        // 绝对路径获取 url
        let realPath = path.join(__dirname, "public" + pathname);
        fs.readFile(realPath, (error, data) => {
          if (error != null) {
            res.end("读取失败···");
            return;
          } else {
            res.end(data);
          }
        });
      });
  
      server.listen(3031, (error) => {
        console.log("ok");
      });
  
  ```

+ `mime`模块

  ```bash
  npm install mime
  const mime = require('mime');
  
  let type = mime.getType(realPath);
  res.writeHead(200,{
  	'content-type': type
  });
  
  ```

  

####  同步`API`和异步`API`

1. 同步API

   > 只有当前 `API` 执行完成后,才能继续执行下一个 `API`

2.  异步 API

   > 当前 API 的执行不会阻塞后续代码的执行

3. 比较

   ```javascript
   
   
   // 同步 sync
   console.log("before···");
   setTimeout(() => {
    // 异步 async 
     console.log("last···");
   }, 20);
   console.log("after···");
   
   
   ```

   <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/async.png" width="400">

4.  同步 `API` 和异步` API `的区别

   > 
   >
   > 同步 API 可以从返回值中拿到 API 的执行结果,但是异步 API 是不可以的
   >
   > 同步 API 从上到下依次执行，前面代码会阻塞后面代码的执行。（会等待循环结束后才会执行后面的代码）
   >
   > 异步 API 不会等待 API 执行完成后再向下执行代码
   >
   > 

   ```javascript
   ------------------------------------- 1 ----------------------------------
   // 同步函数返回值问题
   function sum(n1, n2) {
     return n1 + n2;
   }
   const value = sum(2, 3);
   console.log(value); // 5
   
   // 异步函数返回值问题
   function getMsg() {
     setTimeout(() => {
       return "异步执行";
     }, 20);
   }
   const msg = getMsg();
   console.log("return msg result: ", msg); // undefined
   
   ---------------------------------- 2: 同步 -------------------------------------
   
   for (var i = 0; i < 10; i++) {
       console.log(i); // 同步会等待循环结束后才会执行后面的代码
   }
   console.log('for 循环后面的代码');
   
   ---------------------------------- 3: 异步 -------------------------------------
       
   console.log("code start running···············");
   setTimeout(() => {
     console.log("0.2 start code············");
   }, 20);
   
   setTimeout(() => {
     console.log("0 start code············");
   }, 0);
   console.log("code running end·············");
   
       
   ```

   <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/until.png" width="500">

5. 回调函数

   ```javascript
   作用: 可以拿到异步函数的返回值
   
   // TODO: 异步函数通过回调函数获取返回值
   function getData(callback) {
     setTimeout(() => {
       callback({
         msg: "hello node js",
       });
     });
   }
   getData(function (data) {
     console.log(data);
   });
   
   ```

   

####  Promise 

> promise 出现的目的是解决 Node.js 异步编程中回调地狱的问题。

+ promise的基本使用方法

  ```javascript
  const fs = require("fs");
  let promise = new Promise((resolve, reject) => {
    // 读取文件
    fs.readFile("D.txt", "utf8", (error, data) => {
      if (error) {
        reject(error);
      } else {
        resolve(data.toString());
      }
    });
  });
  
  promise
    .then((result) => {
      console.log(result);
    })
    .catch((error) => {
      console.log(error);
    });
  ```

+  顺序读取文件

  ```javascript
  // 难以维护 
  const fs = require("fs");
  fs.readFile("./A.txt", "utf8", (error, data) => {
    console.log(data.toString());
    fs.readFile("./B.txt", "utf8", (error, data) => {
      console.log(data.toString());
      fs.readFile("./C.txt", "utf8", (error, data) => {
        console.log(data.toString());
      });
    });
  });
  
  ```

+ 解决`Node.js`回调地狱问题

  ```javascript
  
  // promise 的基础使用 解决Node.js 的回调地狱
  
  function p1() {
    return (promise1 = new Promise((resolve, reject) => {
      // 读取文件
      fs.readFile("A.txt", "utf8", (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data.toString());
        }
      });
    }));
  }
  
  function p2() {
    return (promise2 = new Promise((resolve, reject) => {
      // 读取文件
      fs.readFile("B.txt", "utf8", (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data.toString());
        }
      });
    }));
  }
  
  function p3() {
    return (promise3 = new Promise((resolve, reject) => {
      // 读取文件
      fs.readFile("C.txt", "utf8", (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data.toString());
        }
      });
    }));
  }
  
  
  p1()
    .then((r1) => {
      console.log(r1);
      return p2();
    })
    .then((r2) => {
      console.log(r2);
      return p3();
    })
    .then((r3) => {
      console.log(r3);
    });
  ```

####  异步函数

> 异步函数就是异步编程语法的终极解决方案,它可以让我们将异步代码写成同步的形式让代码不再有回调函数嵌套，使代码变得清晰明了。

+ `async` 关键字

  1. 普通函数定义前加`async`关键字  普通函数就变成异步函数

  2.  异步函数默认返回 `promise`对象

  3.  在异步函数内部使用 `return` 关键字进行结果返回 结果会被包裹再 `promise`对象中 return 关键字代替了 `resolve()`

  4.  在异步函数内部使用 `throw` 关键字抛出程序异常

  5.  调用异步函数再链式调用 `then `方法获取异步函数执行结果

  6.  调用异步函数再链式调用 `catch`方法获取异步函数执行的错误信息

     ```javascript
     // 异步函数
     async function fn() {
       throw 'throw error infomation';
       return "return result data";
     }
     console.log(fn()); //默认输出: Promise { undifined }
     
     
     // then方法 catch方法
     fn()
       .then((data) => {
         console.log(data); // 成功: Promise { 'return result data' }
       })
       .catch((error) => {
         console.log(error); //失败: Promise { <rejected> 'throw error infomation' }
       });
     
     ```

+ `await`关键字

  1. `await`关键字`只能`出现在异步函数中
  2.  `await promise await`后面只能写`promise`对象  写其他类型的 `API` 是不可以的
  3.  `await`关键字是可以暂停异步函数向下执行 知道 `promise`返回结果

  ```javascript
  async function fn1() {
    return "fn1";
  }
  async function fn2() {
    return "fn2";
  }
  async function fn3() {
    return "fn3";
  }
  
  // 顺序执行 异步函数
  async function runFn() {
    let r1 = await fn1();
    let r2 = await fn2();
    let r3 = await fn3();
    console.log(r1, r2, r3);
  }
  
  runFn();
  
  ```

+ 使用异步函数顺序读取文件

  ```javascript
  const fs = require("fs");
  const promisify = require("util").promisify;
  const readFile = promisify(fs.readFile);
  
  async function run() {
    let r1 = await readFile("./A.txt", "utf8");
    let r2 = await readFile("./B.txt", "utf8");
    let r3 = await readFile("./C.txt", "utf8");
    console.log(r1, r2, r3);
  }
  run()
  
  ```

  

####  数据库

+ 概念

  |     术语     |                       解释说明                        |
  | :----------: | :---------------------------------------------------: |
  |  `database`  |    数据库`mongogdb` 数据库软件中可以建立多个数据库    |
  | `collection` |  集合 一组数据的集合 可以理解为 JavaScript 中的数组   |
  |  `document`  |    文档 一条具体的数据 可以理解为 JavaScript 对象     |
  |   `field`    | 字段 文档中的属性名 可以理解为 JavaScript中的对象属性 |

+ 第三方包

  + `使用 Node.js`操作Mongodb数据库需要依赖`Node.js`第三方包`mongoose`

    ```bash
    npm install mongoose
    ```

  + 启动`mongodb`服务

    ```bash
    net start mongodb
    ```

  + 关闭`mongodb`服务

    ```bash
    net stop mongodb
    ```

  + 启动遇到如下错误

    ```bash
    
    ‘环境变量’  bin/
    
    发生系统错误 5。
    
    拒绝访问。
    
    解决: 使用管理员权限启动 mongodb 服务
    
    chdir 命令: 获取 windows 的路径 == pwd
    ```

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/adminMon.png" width="600" alt="普通管理员" title="普通管理员">

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/netStartMon.png" width="600" alt="超级管理员" title="超级管理员">

+ `Nodes`连接数据库

  ```javascript
  // 引入 mongoose  模块
  const mongoose = require("mongoose");
  mongoose
    .connect("mongodb://localhost/student", {
      useNewUrlParser: true,
      useUnifiedTopology: true 
    })
    .then(() => {
      console.log("数据库连接成功");
    })
    .catch((error) => {
      console.log(error, "连接失败");
      return;
    });
  
  ```

+ 创建集合

  ```javascript
  创建集合分为两个步骤:
  	1. 对集合设定规则
      2. 创建集合
      创建 mongoose.Schema 构造函数的实例即可创建集合
  ```

  