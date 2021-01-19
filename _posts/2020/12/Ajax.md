---
title: Ajax
date: 2020-12-20 16:06:09
tags: Ajax
categories: Ajax
---

###  Ajax-Web服务器

>  [黑马] 前后端交互- AjaX技术学习

####  搭建`Ajax`环境

+ Ajax的应用场景

  ```javascript
     Ajax 的应用场景:
          1. 页面上拉加载更多数据
          2. 列表数据无刷新分页
          3. 表单项离开焦点数据验证
  ```

+ 安装`node`,自行查阅

+ 下载`express`

  ```bash
  npm install express
  
  # 下载完成后会出现 node_modules
  ```

+ 新建文件夹`public`，用于存放静态资源

+ 新建`app.js`

  ```javascript
  // 引入 express 框架
  const express = require("express");
  // 路径处理模块
  const path = require("path");
  
  // 创建WEB 服务器
  const app = express();
  // 静态资源访问服务器功能
  app.use(express.static(path.join(__dirname, "public")));
  // 监听端口
  app.listen(3000);
  // 控制台显示输出
  console.log("服务器启动成功···");
  
  // 域名访问: localhost/127.0.0.1:3000/静态文件资源名称.html
  ```

+ 启动服务

  ```bash
  node app.js
  ```

+ 效果预览

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/Ajax01.gif" width="600">

####  Ajax 运行原理

#### Ajax的实现原理

1. 创建Ajax对象

   ```javascript
   var xhr = new XMLHttpRequest();
   ```

2. 告诉Ajax亲求地址以及请求方式

   ```javascript
   // 参数1: 请求方式 参数2: 请求地址
           xhr.open('get', 'http://localhost:3000/参数2(请求地址)');
   ```

3.  发送请求

   ```javascript
   xrh.send();
   ```

4. 获取服务器端给与客户端的响应数据

   ```javascript
   xhr.onload = function () {
               console.log(xhr.responseText);
           }
   ```

####  Aja处理JSON数据

+ Ajax处理JSON数据

  ```javascript
   xhr.onload = function () {
              // console.log(xhr.responseText);
              // console.log(typeof xhr.responseText);
              var responseText = JSON.parse(xhr.responseText); // 将JSON 字符串转换为 JSON 对象
              console.log(responseText);
              var str = '<h2> ' + responseText.name + '</h2>';
              // 显示内容
              document.body.innerHTML = str;
          }
  ```

####  Ajax请求参数传递

+ 配置路由

  ```javascript
  // 参数传递
  app.get("/get", (req, res) => {
    res.send(req.query);
  });
  ```

+ `get`请求方式

  ```html
  <div>
          <p> <input type="text" id="username"></p>
          <p> <input type="text" id="age"></p>
          <p> <input type="button" id="btn" value="提交"></p>
      </div>
  ```

  ```javascript
  //path: 传递get请求参数.html
          // 获取username 
          var username = document.querySelector('#username');
          // 获取 age
          var age = document.querySelector('#age');
          // 获取按钮元素 
          var btn = document.querySelector('#btn');
          btn.onclick = function () {
              var xhr = new XMLHttpRequest();
              // username&age
              // 获取用户在文本框输入的值
              var nameValue = username.value;
              var ageValue = age.value;
              
              // 拼接请求参数
              var params = 'username=' + nameValue + '&age=' + ageValue;
              // 配置 Ajax 对象
              xhr.open('get', 'http://localhost:3000/get?' + params);
              
              
              
              // 发送请求
              xhr.send();
              // 获取服务器端相应的数据
              xhr.onload = function () {
                  console.log(xhr.responseText);
              }
          }
  ```

+ `post`请求方式

  + 配置路由

    ```javascript
    // post 所需要
    const bodyParser = require("body-parser");
    
    
    //  post 请求参数
    app.post("/post", (req, res) => {
      res.send(req.body);
    });
    
    ```

  + 请求报文

    ```bash
    在 HTTP 请求和响应的过程中传递的数据块就叫报文,包括要传送的数据和一些附加信息,这些数据和信息要遵守规定好的格式
    ```

  + 实例

    ```javascript
     //path: 传递get请求参数.html
            // 获取username 
            var username = document.querySelector('#username');
            // 获取 age
            var age = document.querySelector('#age');
            // 获取按钮元素 
            var btn = document.querySelector('#btn');
            btn.onclick = function () {
                var xhr = new XMLHttpRequest();
                // username&age
                // 获取用户在文本框输入的值
                var nameValue = username.value;
                var ageValue = age.value;
                // 拼接请求参数
                var params = 'username=' + nameValue + '&age=' + ageValue;
                // 配置 Ajax 对象
                xhr.open('post', 'http://localhost:3000/post');
                // 设置请求参数格式的类型(post 请求必须要设置)
                xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
                // 发送请求
                xhr.send(params);
                // 获取服务器端相应的数据
                xhr.onload = function () {
                    console.log(xhr.responseText);
                }
            }
    ```

+ `JSON`参数格式传递

  + 配置路由

    ```javascript
    app.use(bodyParser.json()); // 解析 JSON 格式
    
    // json 格式参数
    app.post("/json", (req, res) => {
      res.send(req.body);
    });
    ```

  + 实例

    ```javascript
    
            // 1. 创建Ajax对象
            var xhr = new XMLHttpRequest();
            // 2. 告诉Ajax亲求地址以及请求方式
            // 参数1: 请求方式 参数2: 请求地址
            xhr.open('post', 'http://localhost:3000/json');
            // 通过请求头告诉服务器端客户端向服务器传递的请求参数格式是 json 
            xhr.setRequestHeader('Content-Type', 'application/json');
            // JSON.stringify() 将 json 对象转换为 json 字符串
            // 3.  发送请求
            xhr.send(JSON.stringify({ name: 'lisi', age: 50 }));
            // 4. 获取服务器端给与客户端的响应数据
            xhr.onload = function () {
                console.log(xhr.responseText);
            }
    ```

####  Ajax错误处理

+ 网络畅通

  ```javascript
  网络畅通，服务器端能接收到请求m服务器端返回的结果不是预期结果
  
  可以判断服务器返回的状态码,分别进行处理, xhr.status 获取 http 状态码
  
  ```

  + 路由配置

    ```javascript
    // 错误处理
    app.get("/error", (req, res) => {
      res.status(400).send("not ok");
    });
    
    ```

  + 实例

    ```javascript
    var btn = document.querySelector('#btn');
            btn.onclick = function () {
                // Ajax错误处理.html  
                var xhr = new XMLHttpRequest();
                xhr.open('get', 'http://localhost:3000/error');
                xhr.send()
                xhr.onload = function () {
                    console.log(xhr.responseText);
                    // 获取状态码
                    if (xhr.status == 400) {
                        alert('请求出错···');
                    }
                }
            }
    ```

+ 网络畅通,·`404`

  ```javascript
  
  网络畅通,服务器端没有接收到请求,返回 404 状态码
  
  检查请求地址是否错误
  
  // 地址写错
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/notfond.png">

+ 网络畅通,服务器端能接收到请求,服务器返回 500 状态码，找服务器端开发人员

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/internal.png">

+ 网络中断,请求无法发送到服务器端

  ```javasc
  会触发 xhr 对象下面的 onerror 事件,在 onerror 事件处理函数中对错误进行处理
  ```

  ```javascript
   // 网络中断处理
              xhr.onerror = function () {
                  alert('网络中断,无法发送 Ajax 请求···');
              }
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/offline.png">

+ 状态码

  ```javascript
  Ajax 状态码: 表示Ajax 请求的过程状态, ajax 对象返回的
  
  Http 状态码: 表示请求的处理结果 是服务器端返回的
  ```

####  低版本`IE` 浏览器的缓存问题

+ 问题

  ```javascript
  在低版本的IE 浏览器中m Ajax 请求存在后严重的缓存问题,即在请求地址不发生变化的情况下,只有第一次请求会真正发送到服务器端,后续的请求都会从浏览器的缓存中获取结果,即使在服务器端的数据更新了,客户端依然拿到的是缓存中的旧数据
  ```

+ 解决方案

  ```javascript
  在请求地址的后面添加请求参数,保证每一次请求中的请求参数值不相同
  
  xhr.open('get','http://?t='+Math.random());
  
  ```

  + 配置路由

    ```javascript
    const fs = require('fs');
    
    // IE 缓存
    app.get("/cache", (req, res) => {
      fs.readFile("./hello.txt", (err, result) => {
        res.send(result);
      });
    });
    ```

  ```html
  <button id="btn"> 发送 Ajax 请求 </button>
  ```

  ```javascript
  var btn = document.querySelector('#btn');
          btn.onclick = function () {
              // Ajax错误处理.html
              //  创建
              var xhr = new XMLHttpRequest();
              // 
              xhr.open('get', 'http://localhost:3000/cache?t=' + Math.random());
              // 发送
              xhr.send()
              xhr.onreadystatechange = function () {
                  if (xhr.readyState == 4 && xhr.status == 200) {
                      alert(xhr.responseText);
                  }
              }
  
          }
  ```

####  同步异步

+ 同步

  ```javascript
  一个人同一时间只能做一件事,只有一件事情做完,才能做另一件事。
  ```

+ 异步

  ```javascript
  异步代码虽然需要花时间去执行,但程序不会等待异步代码执行完成后再继续执行后续代码,而是直接执行后续代码,当后续代码执行完成后再回头来看异步代码是否返回结果,如果已有返回结果,再调用事先准备好的回调函数处理异步代码执行的结果。
  ```

  ##### Ajax封装

  + 问题: 发送一次请求代码过多,发送多次请求代码冗余且重复

  + 解决方案: 将请求代码封装到函数中,发送请求时调用函数即可

  + 第一次封装

    ```javascript
      function ajax(options) {
                // 创建 Ajax 对象
                var xhr = new XMLHttpRequest();
                // 配置 Ajax 对象
                xhr.open(options.type, options.url);
                // 发送请求
                xhr.send();
                // 监听 xhr 下面的 onload 事件
                // 当 xhr 对象接受完响应数据后触发
                xhr.onload = function () {
                    options.success(xhr.responseText);
                }
            }
            // 调用 ajax()
            ajax({
                // 请求类型
                type: 'get',
                // 请求地址
                url: 'http://localhost:3000/responseData',
                success: function (data) {
                    console.log('获取参数: ' + data);
                }
            })
    
    ```

  + 第二次封装

    ```javascript
      function ajax(options) {
                // 创建 Ajax 对象
                var xhr = new XMLHttpRequest();
                // 传递参数
                var params = '';
                // 遍历参数 对象用 for in
                for (var attr in options.data) {
                    console.log(attr);
                    // 将参数转换为字符串格式
                    params += attr + '=' + options.data[attr] + '&';
                }
                // 将参数最后面的 & 截取掉
                // 将截取的结果重新赋值给 params 变量
                params = params.substr(0, params.length - 1);
                // 判断请求格式
                if (options.type == 'get') {
                    options.url = options.url + '?' + params;
                }
                // 配置 Ajax 对象
                xhr.open(options.type, options.url);
                if (options.type == 'post') {
                    xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
                    xhr.send(params);
                } else {
                    xhr.send();
                }
                // 监听 xhr 下面的 onload 事件
                // 当 xhr 对象接受完响应数据后触发
                xhr.onload = function () {
                    options.success(xhr.responseText);
                }
            }
            // 调用 ajax()
            ajax({
                // 请求类型
                type: 'get',
                data: {
                    name: 'zs',
                    age: 20
                },
                // 请求地址
                url: 'http://localhost:3000/first',
                success: function (data) {
                    console.log('获取参数: ' + data);
                }
            })
    ```

    

