---
title: Vscode-注释颜色斜体修改
date: 2020-12-31 17:37:03
tags:
- vscode
- 开发工具
categories: vscode
---

###  Vscode-注释颜色斜体修改

+ 修改后的注释显示状态

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231173933.png">

+ 添加的具体步骤

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231174252.png">

+ 找不见请搜索`settings.json`

  <img src="https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/20201231174559.png">

+ `json`添加

  ```json
   "editor.tokenColorCustomizations": {
          "comments": "#62f5a2", // 注释
         // "keywords": "#0a0", // 关键字
         // "variables": "#f00", // 变量名
          // "strings": "#e2d75dbd", // 字符串
           "functions": "#5b99fcc9", // 函数名
           "numbers": "#AE81FF", // 数字
              "textMateRules": [
              {
                  "name": "Comment",
                  "scope": [
                      "comment",
                      "comment.block",
                      "comment.block.documentation",
                      "comment.line",
                      "comment.line.double-slash",
                      "punctuation.definition.comment",
                  ],
                  "settings": {
                   "fontStyle": ""
                  }
              },
          ]
      }
  ```

  

###  目前在用 Vscode 插件安装

1. TODO: 注释一下 `Todo Highlighter`

   <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/todo.png">

2. `Bracket Pair Colorizer 2`

   <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/kh.png">

3. 汉化插件`Chinese`

4.  对齐，提高阅读 `Indent-Rainbow`

   <img src="https://gitee.com/wang_hong_bin/repo-bin/raw/master/iR.png">

5.  代码格式化插件`Prettier`
6.  css 定义颜色直观显示`Color Highlight`

7. Vue 高亮插件`Vetur`

8. 运行各种代码 `Code Runner`

9.  `Open-In-Browser`

10.  可视化`git` 提交 `Git Graph`
12.  `koroFileHeader`,这个插件主要用于自动的插入头文件开头的说明和函数的说明