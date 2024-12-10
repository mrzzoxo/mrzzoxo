---
title: iperf3网络测试工具
date: 2024-11-21 11:58:55
tags:
- iperf3
description: iperf3 是一个用于测量最大TCP和UDP带宽的工具，常用于评估网络性能、排查网络问题。它能够提供详细的带宽报告、延迟抖动和数据包丢失信息。
---

iperf3 是一个用于测量最大TCP和UDP带宽的工具，常用于评估网络性能、排查网络问题。它能够提供详细的带宽报告、延迟抖动和数据包丢失信息。

1、Debian安装：
``` shell
apt install iperf3 -y
```
2、服务发送端 启用指令：
``` shell
iperf3 -s
```
3、用户下载端 测试指令：
``` shell
iperf3 -c 192.168.1.100 -f M -t 30
```
常用参数：
```
-c 192.168.1.100
目标IP

-p 7890
指定端口(默认是5201)

-P 4
多线程 设置并行连接数

-t 30
持续时间丨单位为秒

-f M
指定单位
```
官网下载：<a target="_blank" rel="nofollow noopener" href="https://iperf.fr/iperf-download.php">https://iperf.fr/iperf-download.php</a>
Windows端：<a target="_blank" rel="nofollow noopener" href="https://github.com/ar51an/iperf3-win-builds">https://github.com/ar51an/iperf3-win-builds</a>