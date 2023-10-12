---
author: mojj 
pubDatetime: 2023-10-12 10:00
title: git解决远程仓库存在无用文件问题
featured: false
draft: false
tags:
  - git
description: 
    git日常使用。
---

1. 背景
   
   初次提交项目时，不小心将无用文件夹提交至github，需要解决。

2. 步骤

   ```shell
   # --cached：保留本地文件
   git rm -r --cached <folder/file>
   git add .
   git commit -m "msg"
   git push
   ```