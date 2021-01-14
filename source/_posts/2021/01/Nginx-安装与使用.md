---
title: Nginx-安装与使用
date: 2021-01-13 20:06:57
tags:
- Nginx
categories: HTML
---



###   Nginx-安装与使用

+ 前提: 拥有服务器(推荐阿里云)

+ 连接服务器

+ 搜索`nginx`

  ```bash
  yun search nginx
  ```

+ 安装`nginx`

  ```bash
  yum install nginx
  ```

+ 查看`nginx`的具体信息

  ```bash
  yum info nginx
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/nginx.png" width="600" height="300" alt="nginx">

+ 启动`nginx`服务

  ```bash
  nginx
  ```

  + 通过公网`IP`访问,进入首页

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/rehatNginx.png" width="600" heihgt="200" alt="nginx">

  + 访问不了的话查看安全组(`添加端口号: 80`,阿里云防火墙只开启 `22`)

+ 停止`nginx`服务

  ```bash
  nginx -s stop
  ```

+ 卸载`nginx`

  ```bash
  yum remove nginx
  ```

+ 查看已安装软件

  ```bash
  yum list installed
  ```

+ 搜索某个软件是否安装

  ```bash
  yum list installed | grep search-name
  ```

+ 静态资源存放路径

  ```bash
  /usr/share/nginx/html
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/nginxHt.png">

###  其他软件方法

```bash

# 搜索
yum search install-package-name 
# 下载
yum install -y install-package-name 
# 卸载
yum remove -y uninstall-package-name

# 参数意义
-y 遇到自动 yes

# 搜索 python
yum search python3 | grep programing # 源代码构建安装

# 软件更新,更新所有
yum update -y 

```

