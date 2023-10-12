---
author: mojj 
pubDatetime: 2023-10-12 08:50
title: git当前分支修改内容移动到其它分支
featured: false
draft: false
tags:
  - git
description: 
    git日常使用。
---

1. 背景
   
   git管理项目代码，开发需求前忘记切换到开发分支，需将当前分支更改内容切换到目的开发分支。

2. 实现原理
   
   当前分支更改内容包括两部分，每部分解决原理：
   1. 未纳入git管理的新增文件
   
   这部分内容，先使用 `git add` 将新增文件暂存，然后按照第二部分处理。

   2. 纳入git管理的文件，包括commit和未commit的内容
   
   此部分需使用 `git stash` 将修改内容存储到栈，将工作空间恢复到 `head` commit。然后切换到目标分支，使用 `git stash pop` 将上一个stash拉取并应用到当前分支。

3. 操作步骤
   ```shell
   git add .
   git stash
   git checkout <target branch>
   git stash pop
   ```
