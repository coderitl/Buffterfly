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

  

