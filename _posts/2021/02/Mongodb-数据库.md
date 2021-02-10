---
title: Mongodb-数据库
date: 2021-02-10 14:00:57
tags:
- Node
- Mongodb
categories: Mongodb
top_img:
cover:
---

###   Mongodb-数据库

```bash
collection-name 自定义集合名

[ ]  可选参数
```



####  命令行

```bash
windows+r: mongo [进入交互式命令行模式]

退出: exit / ctrl + D

```



####  基础操作

+ 查询数据库

  ```javascript
  show databases;
      admin   0.000GB
      config  0.000GB
      local   0.000GB
  
  ```

+ 使用数据库

  ```javascript
  use database-name;
  
  > use admin;
  switched to db admin
  
  注意: 在 mongodb 中使用不存在的数据库时不会报错,会自动隐式创建不存在的数据库
  ```

+ 查看集合

  ```javascript
  show collections;
  ```

+ 创建集合

  ```javascript
  语法:
  	db.createCollection('collection-name');
  
  > db.createCollection('student');
  { "ok" : 1 }
  
  注意: createCollection 没有 s
  ```

+ 删除集合

  ```javascript
  语法:
  	db.collection-name.drop();
  
  -- 创建集合 c2
  > db.createCollection('c2');
  { "ok" : 1 }
  -- 查看集合 
  > show collections;
  c2
  student
  -- 删除集合 c2
  > db.c2.drop();
  true -- 返回结果为布尔值
  ```

+ 查看当前使用数据库

  ```javascript
  -- 隐式创建的数据库没有内容查看不会被显示
  db
  ```

+ 删除数据库

  ```javascript
  use drop-database-name;
  db.dropDatabase();
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/monfo.png">



####  集合的增删改查

+ 集合增加数据

  + 插入一条数据

    ```javascript
    语法: db.collection-name.insert(json-data);
    注意: 集合存在则直接插入数据,集合不存在则隐式创建
    
    -- 显示可用集合
    show collections;
    
    
    -- 插入数据
    db.test.insert({"name":"zahngsan"});
    
    
    
    
    result: WriteResult({ "nInserted" : 1 })
    
    注意: 数据库和集合不存都会隐式创建，对象的键统一不加引号方便看，但是查看集合数据时系统会自动添加双引号
    ```

  + 插入多条数据

    ```javascript
    
    // 集合插入多条数据 db.collection-name.insert({})
    db.emp.insert([
        {
            name: "张三",
            age: 20,
            gender: "男"
        },
        {
            name: "李四",
            age: 18,
            gender: "女"
        },
        {
            name: "王五",
            age: 10,
            gender: "男"
        },
        {
            name: "王麻子",
            age: 38,
            gender: "男"
        }
    ]);
    ```

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/insertMore.png" width="600">

  + 快速输出` n `条数据

    ```javascript
    // 快速插入 10 条数据 支持 js 语法
    for (var i = 0; i < 10; i++) {
        print(i); // 测试输出
    }
    
    ```

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/mongojs.png" width="400">

  + 快速在指定集合插入`n `条数据

    ```javascript
    
    // 在指定集合中快速插入 n 条数据
    for (var i = 0; i < 10; i++) {
        db.dept.insert({
            deptno: "deptno" + i, // 字符拼接的形式
            age: i + 1
        });
    }
    
    // 查询结果集
    db.dept.find();
    
    ```

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/jsMon.png">

  + 查看集合内容

    ```javascript
    db.collection-name.find();
    
    > db.test.find();
    { "_id" : ObjectId("602380e157486fb18cef5489"), "name" : "zhangsan" }
    { "_id" : ObjectId("6023839257486fb18cef548a"), "name" : "lisi", "age" : 18, "gender" : "男" }
    
    _id: 可以被覆盖,进行自定义 _id: value (不推荐修改) 
    _id: 
    	组成原理: 时间戳 机器 PID 计数器
    ```

  + 条件查询

    ```javascript
    语法: db.collection-name.find(条件,[查询的列])
    ```

    ```javascript
    查询所有数据:  {} 可省略
    查询特定条件的值:  {条件: value}
    多条件查询: {条件1:value,条件2:value,····}
    
    查询列:
    [
        不写列 查询全部
        {某列名称: 1} 只显示 该列
        {某列名称: 0} 除了该列,显示其他列
    ]
    ```

  1. 查询所有数据

     ```javascript
     db.dept.find({});
     ```

  2.   只显示 `age` 列数据

     ```javascript
     db.dept.find({}, {
         age: 1
     });
     ```

  3. 显示所有非 `age`列数据

     ```javascript
     db.dept.find({}, {
         age: 0
     });
     ```

  4.  条件列

     | 运算符 |   作用   |
     | :----: | :------: |
     | `$gt`  |   大于   |
     | `$gte` | 大于等于 |
     | `$lt`  |   小于   |
     | `$lte` | 小于等于 |
     | `$ne`  |  不等于  |
     | `$in`  |   `in`   |
     | `$nin` | `not in` |

     ```javascript
     db.collection-name.find(
     	键: {运算符: 值}
     );
     ```

     + 查询年龄大于`8`的列数据`$gt`运算符

       ```javascript
       db.dept.find({
           age: {
               $gt: 8
           }
       });
       ```

       <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/$gt.png">

  5. 特定范围`&in` 运算符

     ```javascript
     // 特定范围内 Eg. 7, 8, 9
     db.dept.find({
         age: {
             $in: [7, 8, 9]
         }
     })
     
     
     ```

     <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/$in.png">

+ 修改集合

  > 
  >
  > 基础语法: `db.collection-name.update(条件,新数据[，是否新增,是否修改多条])`
  >
  > 是否新增: 指条件匹配不到数据则插入(`true`是插入,`false`不插入 默认)
  >
  > 是否修改多条：指将匹配成功的数据都修改(`true`是,`false`否 默认)
  >
  > 

  + 准备测试数据

    ```javascript
    // 创建新集合
    db.createCollection('testInfo');
    
    // 通过 for 循环插入 n 条测试数据
    for (var i = 0; i < 10; i++) {
        db.testInfo.insert({
            name: "name" + i,
            age: i + 1
        });
    }
    
    ```

  + 数据更新`update`

    ```javascript
    // 将 name: "name0" 改为 name: "name11"
    // 替换操作 并不能实现数据修改
    db.testInfo.update({
        name: "name0"
    }, {
        name: "name11"
    });
    ```

    <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/changeMon.png" width="600">

    + 数据修改

      ```javascript
      db.collection-name.update({条件}，{
                                
                                新数据【修改器】:{键: 值}}
      )
      ```

      ```javascript
      // 将 name: "name9" 改为 name: "name01"
      
      db.testInfo.update({name:"name9"},{$set:{name:"name01"}});
      
      ```

      <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/updateMon.png">

    + 多列数据更新

      ```javascript
      // 修改 name:name4 age:5 修改为 name:"name04",age:40
      db.testInfo.update({
          name: "name4",
          age: 5
      }, {
          $set: {
              name: "name04",
              age: 40
          }
      });
      
      --------------------------------------- S: 输出 -------------------------------------------------------
      
      > db.testInfo.find({name:"name04"});
      { "_id" : ObjectId("6023a1de167e00002a003d48"), "name" : "name04", "age" : 40 }
      >
      --------------------------------------- E: 输出 ------------------------------------------------------
      ```

    + 根据条件,对数据进行 `+5/-5`  `$inc`操作符

      ```javascript
      db.testInfo.find({
          name: "name01"
      }, {
          $inc: {
              age: 5/ [  -5 原基础减 5 ]
          }
      });
      
      ```

      <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/update$inc.png" width="600">

    |  修改器   |   作用   |
    | :-------: | :------: |
    |  `$inc`   |   递增   |
    | `$rename` | 重命名列 |
    |  `$set`   | 修改列值 |
    | `$unset`  | 删除字段 |

    + 所有操作符进行练习

      ```javascript
      
      ```

      <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/optionA.png">

    + `true`

      ```javascript
      db.testInfo.update({
          name: "name20",
          age: 5
      }, {
          $set: {
              name: "name04",
              age: 40
          }
      }, true);
      // 第三个条件 true: 没有找到则进行添加
      ```

      <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/updateTrue.png" width="600">

    + 第四个参数`true/false`

      ```javascript
      db.testInfo.update({name:"name2"},{$set:{age:22}},false,true);
      
      false: 没有不添加
      true: 允许修改多条
      
      ```

      <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/trueOrFalse.png" width="600">

+ 删除数据

  ```javascript
  语法: db.collection-name.remove();
  
      db.testInfo.remove({name:"name2"},true); // 只删除一条数据
      db.testInfo.remove({name:"name2"}); // 删除多条数据
  
  ```

  <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/removeMon.png" width="600">

+ 删除集合

  ```javascript
  // 删除集合语法 
  db.collection-name.drop();
  // 删除成功显示 true
  db.testInfo.drop(); 
  ```

  