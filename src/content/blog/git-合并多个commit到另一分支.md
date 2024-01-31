---
author: mojj 
pubDatetime: 2024-01-26 14:31
title: 合并多个commit到另一分支
featured: true
draft: false
tags:
  - git
  - 管理流程
description: 
    git合并指定commit到另一分支
---

1. 现状
   
   从A分支创建B分支，开发代码后需将B分支代码合并到C分支，A,C分支代码不同，A分支包含C分支不需要的代码

2. 解决思路及实现步骤
   
   1. cherry pick
        将一个或多个提交应用到另一个分支，此命令会创建新的commit，commit具有新的hash值，
        考虑使用 -x 选项，将挑选的提交的来源信息包含在新的提交中，以便更容易追踪。
   2. rebase
        重新应用一系列提交到另一个分支，可指定commit范围，所有的commit以当前head为基地。
        **不要在公共分支上使用此命令**，因为这会改变提交的历史，可能会影响其他团队成员的工作。
      
   
3. 具体操作
   
   ```shell
   # 单个commit
   git cherry-pick <commit-hash>
   # 多个commit
   git cherry-pick <commit-hash1> <commit-hash2> ...
   # commit范围
   git cherry-pick <commit-hash1>..<commit-hash2>
   ```

4. 其他

    > 产生此问题的原因为：  
    从fat创建了新需求的开发分支，上线时需要合并到release，但是fat历史提交中存在release的不需要的代码。  

    >公司 git 管理的规矩为（从公司角度），fat为测试环境分支，release 为生产环境分支，需求开发时各开发人员建立自己的开发分支，所有的开发分支均会合并到fat，其中也包括一些不上线的功能。  
    功能开发流程为，所有功能开发完成后，将功能开发分支合并到fat，进行测试，包括上线的不上线的，等到上线时，再将自己上线功能的分支自己合并到release。  

    **问题反思：**  
    1. git管理流程不合理
       1. fat分支应与release保持一致，只有上线的内容才会被push fat；如存在临时功能或下次上线内容也应该从fat新建分支进行开发。
        确保fat只存在当前版本内容，此版本封版后，再合并下版本内容。
    2. 需完善的部分
       1. release需要有一系列版本分支。（可通过tag标记）
       2. release merge代码时，不同版本间需要有明确merge info。   
       （可通过 git merge --no-ff <branch-name> 每次合并生成一个新commit，更好的追踪代码来源）
    3. 定期清理分支

5. 参考文档
   
   
