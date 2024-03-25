---
author: mojj 
pubDatetime: 2024-03-25 10:00
title: WSL-Windows子系统
featured: false
draft: false
tags:
  - WSL
  - Linux
description: 
    关于在Windows中使用Linux发行版。
---

1. 背景

Windows作为主力开发机器，有时本地开发测试需要Linux环境，尤其是开发只能在Linux运行的程序，如Pingora。

WSL: 全称Windows Subsystem for Linux

[官方文档](https://learn.microsoft.com/en-us/windows/wsl/)

2. 安装
```powershell
# 可通过 wsl -l -o 查询官方支持下载的发行版，也可通过第三方本地导入，基本流程是：docker导出需要的发行版镜像，然后导入到wsl中
wsl --install -d <distribution name>
# 升级
wsl --update
# 关闭
wsl --shutdown
# 启动
wsl
```

3. 其他问题
如window本机使用代理，wsl默认使用nat模式，开启代理后，启动wsl。会提示: `wsl: 检测到 localhost 代理配置，但未镜像到 WSL。NAT 模式下的 WSL 不支持 localhost 代理。`
可通过创建或打开%USERPROFILE%\.wslconfig文件并在文件中增加以下内容解决，新增后需重启wsl。

```conf
[experimental]
autoMemoryReclaim=gradual  # gradual  | dropcache | disabled
networkingMode=mirrored
dnsTunneling=true
firewall=true
autoProxy=true
```

如需在wsl中使用代理，开启clash-verge的tun模式即可。

[VsCode in WSL](vhttps://code.visualstudio.com/docs/remote/wsl)

[WSL官方文档](https://learn.microsoft.com/en-us/windows/wsl/install)

