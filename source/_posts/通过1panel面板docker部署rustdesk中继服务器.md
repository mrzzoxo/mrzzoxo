---
title: 通过 1panel 面板 docker 部署 rustdesk 中继服务器
date: 2024-11-18 11:02:10
tags:
- 1panel
- docker
- rustdesk
description: 通过 1panel 面板 docker 部署 rustdesk 中继服务器
---

RustDesk – 开源远程桌面访问软件
旨在提供安全便捷的自建方案。

1 、安装 1Panel 面板：1Panel-install
2 、登录 1Panel 面板：应用 - 搜索 rustdesk - 安装 （无特殊需求 参数默认即可）
3 、 1Panel 面板 - 主机 - 防火墙 - 创建端口规则：开放 tcp 协议 21115-21119 端口

![开放21115-21119端口](/images/20241118110210-3.png)

4 、 创建端口规则：开放 udb 协议 21116 端口

![开放udb协议21116端口](/images/20241118110210-4.png)

5 、进入安装目录，打开 data/hbbs 目录，

![打开data/hbbs目录](/images/20241118110210-5.png)

6 、打开 .pub 文件 可以看到 key

![打开.pub文件](/images/20241118110210-6.png)

7 、电脑下载安装 rustdesk：<a target="_blank" rel="nofollow noopener" href="https://github.com/rustdesk/rustdesk/releases/latest">rustdesk-download</a>

8 、设置 - 网络 - 应用 保存即可

ID 服务器：IP:21116

中间服务器：IP:21117

![设置网络](/images/20241118110210-8.png)

9 、常规 - 重新启动服务

![重新启动服务](/images/20241118110210-9.png)

10 、显示 就绪 就是连接上自建的中继服务器了。

![连接中继服务器](/images/20241118110210-10.png)