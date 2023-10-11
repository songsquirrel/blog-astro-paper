---
author: mojj 
pubDatetime: 2023-10-11T13:11:00Z
title: git本地项目首次同步至远程仓库
postSlug: git-本地项目-首次-同步至远程仓库
featured: true
draft: false
tags:
  - git
  - github cli
description: 
    git日常使用，本地项目配置远程仓库，免去网页操作。
---

1. 现状
   
   本地创建的项目（远程库未存在），希望直接在终端推送至远程仓库，省去浏览器创建仓库这一步。

2. 基本实现流程
   
   1. 创建远程仓库（通过github cli直接在终端创建）
   2. 初始化本地仓库
   3. 本地库与远程库关联
   4. 将本地内容推送至远程仓库。
3. 具体操作
   
   ```shell
   gh repo create <remote repo name> --public 

   cd <local repo>
   git init

   git remote add origin <remote repo>

   git add .
   git commit -m "msg"
   git push --set-upstream origin master
   ```

4. 参考文档
   
   1. [github cli manual](https://cli.github.com/manual/)
