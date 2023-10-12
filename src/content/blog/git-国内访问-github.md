---
author: mojj 
pubDatetime: 2023-10-11 16:11
title: git由于网络问题认证github失败
featured: false
draft: false
tags:
  - git
  - github cli
description: 
    git日常使用，由于国内网络原因，github认证失败。无法上传、下载项目。
---

1. 现状
   
   由于国内网络原因，使用git管理github仓库时，授权及项目同步总是超时，以下是解决方案。

2. 解决思路及实现步骤
   
   1. 解决网络问题（vpn，机场，配置hosts等）
   2. 使用github cli管理授权
      1. 安装github cli
      2. 使用github cli管理git认证。
   
3. 具体操作
   
   ```shell
   gh auth login 
   ```

4. 其他

    国内git clone代码满的解决方案，url前增加 <text>https://ghproxy.com/<text>
    [官网](https://ghproxy.com)

5. 参考文档
   
   1. [github cli manual gh_auth_login](https://cli.github.com/manual/gh_auth_login)
