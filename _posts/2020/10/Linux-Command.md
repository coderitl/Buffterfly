---
title: Linux Command
date: 2020-10-17 22:20:21
tags: Linux
categories: "Linux"
top_img:
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Linux.jpg
---

```bash
username: Centos

passwd: aidou123456
```

```bsh
# 超级用户提示符

$ 普通用户提示符

~ 当前所在家目录
```

### Centos 7 安装后没有网络的解决方案：

```bash
检测网络状态
	
	ping xxx

没有 ifconfig 使用: ip addr 

切换目录： cd etc/sysconfig/network-scripts

显示: ls

	ifcfg-ens33
	
编辑: ifcfg-ens33

	vi ifcfg-ens33
```



### Linux 常用命令:

+ 文件处理命令

  ```bash
  创建目录: mkdir -p [目录名] (-p递归创建)
  
  删除目录: rm -rf 【目录名】  【-r 删除目录   -f 强制】
  
  复制: cp [选项] [原文件或目录] [目标目录]
  
  		[-r 复制目录 -p 连带文件属性复制 -d 若源文件是链接文件，则复制链接属性 -a == -pdr]
  
   ll = ls -l
   
  剪切: mv [原文件或目录] [目标目录]
  
  重命名: mv
  
  ```

  ### 目录：

  ```bash
   + /根目录
   + /bin 命令保存目录(普通用户就可以读取)
   + /boot 启动目录，启动相关文件
   + /dev 设备文件保存目录
   + /etc 配置文件保存目录
   + /home 普通用户家目录
   + /lib 系统库保存目录
   + /mnt 系统挂载目录
   + /media 挂载目录
  ```

+ 文件搜索命令

  ```bash
  文件搜索命令: locate 文件名[只能是文件名]
  
  命令搜索命令 whereis 与 which
  
  文件搜索命令 find
  
  字符串搜索命令 grep
  
  find 命令与 grep 命令的区别
  
  
  搜命令的搜索：
  
  	whereis 命令名
  	
  	which is
  	
  find 命令:
  	
  	find 【搜索范围】 【搜索条件】
  	
  	find / -name 具体文件名
  	
  通配符:
  	
      * ? []
      
      find /路径 -name "*"  任意多个
      
      find /root -iname 具体文件名（忽略大小写）
      
      find /root -nouser 没有所有者文件
      
      find /var/log/ -mtime +10 （10天前修改的文件）
      
      -10: 10 内修改的文件
       10 10天当天修改的文件
      +10 10天前修改的文件
      
  	按照文件大小搜索:
  	
  	find . -size 25k(k,M 单位)
  	+25(大于)
  	-25(小于)
  	
  PATH: 环境变量
  ```

  ```bash
  grep 命令:
  	grep 【选项】 字符串 文件名
  	
  	选项:
  		
  		-i 忽略大小写
  		
  		-v 排除指定字符串
  		
  grep "size" 文件名（xxx）（在xxx 中查找 size 相关的字符串 ）
  
  grep -v "size" 文件名（xxx）（在 xxx 中不查找 size 相关的字符串 ）
  ```

  `find`与`grep` 的区别:

  ```bash
  find 命令: 在系统当中搜索费和条件的文件名，如果需要匹配，使用通配符匹配，通配符是完全匹配
  
  grep 命令:  在文件当中搜索符合条件的字符串，如果需要匹配，使用正则表达式进行匹配，正则表达式包含匹配
  ```

  

+ 帮助命令

  ```bash
  man 
  
  help
  ```

+ 压缩与解压缩命令

  ```bash
  压缩:
      .zip 
      .rar
      .bz2
  
      .tar.gz
      .tar.bz2
      
     zip 压缩文件名.zip 源文件
     
     zip -r 压缩文件名 源目录 
  ```

  + zip 使用

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201018113743290.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

  + zip file

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201018113743458.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)
    
    

  ```bash
  解压缩:
  
  	unzip 压缩文件
  ```

  + 解压目录压缩文件 `unzip one.zip` 

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020101811374235.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

    

  + 解压文件 `unzip newFile.zip`

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201018113743372.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)
    
    

  ```bash
  gzip 源文件
  
  # 压缩为 .gz 格式的压缩文件，源文件会消失
  
  gzip -c 源文件 > 压缩文件
  
  # 压缩为 .gz 格式 源文件保留
  
  gzip -r 目录 # 测试未通过
  
  # 压缩目录下所有的子文件 但不能压缩目录
  
  
  # 解压缩:
  	
  	gzip -d 压缩文件
  	
  	gunzip 压缩文件
  	
  	
  # 压缩
  
  bzip 源文件 # 压缩为 .bz2 格式 不保留源文件
  
  bzip2 -k 源文件 (不能压缩目录) 
  
  # 解压缩
  
  bzip2 -d 压缩文件（-k 保留压缩文件）
  
  bunzip2 压缩文件 （-k 保留压缩文件）
  	
  ```

  ### <font color="red">常用压缩格式:</font>

  ```bash
  
  .tar.gz
  
  .tar.bz2
  
  ```

  + 使用格式

    ```bash
    tar -cvf 打包文件名 源文件
    
    选项: 
    	
    	-c 打包
    	
    	-v 
    	
    	-f 指定打包的文件名
    ```

  + `.tar.gz` 格式

    ```bash
    # .tar.gz 压缩格式
    
    其实 .tar.gz 格式是先打包为 .tar 格式,在压缩为 .gz 格式
    
    tar -zcvf 压缩包名 .tar.gz 源文件
    
    选项: 
    	
    	-z 压缩为 .tar.gz 格式
    	
    	-x 解压缩为 .tar.gz 格式
    	
    ```

  + `tar zcvf `

  ![tar-gz格式压缩](https://img-blog.csdnimg.cn/20201018144436364.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

  + `zxvf tar-gz`

    ![解压缩](https://img-blog.csdnimg.cn/20201018144620489.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

  + `.tar.bz2` 压缩格式

    ```bas
    tar -jcvf 压缩包名.tar.bz2 源文件
    
    选项；
    
    	-z 压缩为 .tar.bz2 格式
    	
    tar -jxvf 压缩包名.tar.bz2
    	
    	-x 解压缩为 .tar.bz2 格式
    	
    ```

  + 解压到指定位置

    ```bash
    tar -jxvf 文件名.tar.bz2 -C xxx/xxx/xxx ( xxx--> 指定的文件路径)
    
    ** 注意: -C 的位置
    
    ```

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020101814505577.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)

+ 关机和重启命令

  ```bash
  关机:
  
  	shutdown -r now
  
  重启: 
  
  	reboot
  ```

###  配置`VIM`编辑器

```bash
# 配置 vim

# 创建文件
touch .vimrc
# 写入一下配置信息
vim .vimrc

    set nu # 显示行号
    syntax on # 高亮显示
    set ts=4 # 制表位
    set expandtab # 自动转换 tab
    set ruler # 显示光标
    set nohls # 关闭搜索高亮
```

###  末行模式

+ 显示关闭行号(`按下Esc后执行`)

  ```bash
  # --------------- S: Esc ---------------------
  
  set nonu # 关闭行号
  set nu # 显示行号
  
  ```

+ 制表键位数设置

  ```bash
  set ts=4
  ```

+ `vim`下代码高亮显示

  ```bash
  syntax on # 开启
  syntax off # 关闭
  ```

+ 光标所在位置

  ```bash
  set ruler # 显示光标所在位置
  
  set noruler # 关闭光标显示
  
  # --------------- E: Esc ---------------------
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/ruler.png">

+ 命令模式

  + 移动光标

    ```bash
    G # 光标移到文件末尾
    200G # 光标移动到第 200行
    gg # 光标移动到行首
    
    h 左
    j 下
    k 上
    l 右
     
     ctrl + y / ctrl + e 移动一行
     ctrl + f / ctrl + b 翻一页
     
     0 光标移动到行首
     $ 光标移动到行尾
     w 光标移动到下一个单词
    ```

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/LinuxD.png" title="慕课网截图">

  + 删除

    ```bash
    dd # 删除光标所在行
    100dd 从光标所在删除 100 行
    ```

  + 复制

    ```bash
    yy # 复制光标所在行
    
    10yy # 光标所在行开始复制 10 行
    
    p # 粘贴
    10p # 粘贴 10 遍
    
    ```

  + 撤销恢复

    ```bash
    u # 撤销
    ctrl + r # 恢复
    ```

  + 映射快捷键

    ```bash
    map <F2> gg99999dd # 回到行首 删除 9999行
    
    inoremap _main if __name__ == '__main__' 
    ```

  + 多文件操作

    ```bash
    :ls # 查看当前打开的所有文件（类似于windows的 windows + Tab,在linux只显示文件名称）
    :b 数字 # 显示指定文件
    ```

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/lsAllfile.png">

  + 窗口显示(分屏)

    + 水平拆分

      ```bash
      sp
      
      # 切换窗口
      ctrl + ww
      ```

    + 垂直拆分

      ```bash
      vs # 垂直拆分窗口
      ```

    + 退出窗口

      ```bash
      qa # 水平拆分垂直窗口
      
      wqa # 保存并退出所有窗口
      ```

  + 中断恢复

    + `shift + r`

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/recover.png">

    + 删除隐藏文件

      ```bash
      # 显示隐藏文件 
      ls -a
      
      rm -y 上一次中断的执行文件.后缀名.swp
      
      ```

+ 命令别名

  ```bash
  # 别名: 简化输入
  alias 别名 = '命令'
  
  # alias nl='ls -laR' # 递归显示,
  ```

+ 查找替换

  ```bash
  # 全文替换
  :1,$s/替换目标/替换为/ci # c确认 i 忽略大小写
  
  # 前 n 替换
  :1,10s/替换目标/替换为/ci # c确认 i 忽略大小写 
  
  # 一行有多个需要替换就需要添加 g 参数
  :1,10s/替换目标/替换为/cg # c确认 g 全局 global
  
  # 直接替换
  :1,$s/替换目标/替换为
  
# 查找
  ? 或 /
  ```

+ 快捷键

  ```bash
  shift + v | V # 选中光标所在行
  
  shift + g | G # 向下选择
  ```

+ `vim`主题

  ```bash
  # 末行模式下
  
  :colorscheme (空格一下，按下 ctrl + d)
  
  # 显示可选主题
      blue       default    desert     evening    koehler    murphy     peachpuff  shine      torte
      darkblue   delek      elflord    industry   morning    pablo      ron        slate      zellner
  
  # 可以从网络下载主题
  
  https://github.com/flazz/vim-colorschemes
  
  # 可写入 .vimrc 文件永久配置 存入 git 进行版本控制, 以后方便使用
  
  # 开源: https://github.com/liuchengxu/space-vim (以后配置)
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/autoindent.png" title="python 文件未能实现自动换行">

+ `Vim`插件配置

  ```bash
  # https://github.com/sbdchd/neoformat vim 代码格式化插件
  ```

  

###  宏：

+ 录制宏

  ```bash
  末行模式: q其他字母
  ```

+ `python`注释宏录制

  + `vim`文件

  + 按下`q`，在键入其他字母`Eg. a 寄存器名称`

  + 按下`i`

  + 添加注释 `#`

  + 按下`ESC`，按下`j`进入下一行

  + 按下`q`结束宏

    

  + 播放宏

    + 数字 `@a`

  + 演示

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/hong.gif">

### 挂载:

```bash
mount # 显示
```

### Shell基础:

```bash
 管道符；
 	
 	;
 	
 	&&
 	
 	||
 	
 	
 检测:
 
 	ls && echo "yes" || echo "no"
	
	# 如果 ls 正确执行 输出 yes 否则 no
```

```bash
通配符:

	?
	*
	[]
```



### 用户和用户组:

```bash
# 用户: 使用操作系统

# 用户组: 具有相同系统权限的一组用户
```

```bash
# 创建用户组
	groupadd 组名
# 修改用户组名称
	groupmod -n 新组名 旧组名
# 添加组编号
	groupmod -g 668(组编号) 组名
# 创建用户组 并添加组编号
	groupadd -g 888 组名
# 删除用户组
	groupdel 组名(必须先删除用户)
```

```bash
# 用户
# 创建用户组
	groupadd 组名
# 添加用户
	useradd -g 组名 用户名1
	useradd -g 组名 用户名2
	
# 添加用户 并指定用户个人文件夹
	useradd -d /hone/xxx (用户组 可省略) 用户名
	
# 查看
	cat /etc/passwd
	
# 对用户添加备注
	usermod -c 备注信息 用户名
# 修改用户的文件夹路径
	usernod -d /home/xxx 用户名
# 修改用户的所属用户组
	usermod -g 新用户组名 旧用户组名
# 删除用户和用户文件夹
	userdel -r 用户名
	
```

```bash
# 禁止除了root 其他用户登录

touch /etc/nologin
```

### 进阶：

```bash
# 锁定用户
	passwd -l 用户名 
# 解锁用户
	password -u 锁定的用户名
# 无密码登录
	passwd -d 用户名
```



