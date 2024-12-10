---
title: Debian开启BBR加速
date: 2024-11-25 11:58:40
tags:
- debian
- bbr
description: BBR (Bottleneck Bandwidth and Round-trip propagation time) 是一种由 Google 开发的 TCP 拥塞控制算法。
---

什么是 BBR？
BBR (Bottleneck Bandwidth and Round-trip propagation time) 是一种由 Google 开发的 TCP 拥塞控制算法。它能够更有效地利用网络带宽，减少丢包，提高网络传输的稳定性和速度，尤其适用于高带宽的应用场景。

为什么在开启 BBR？
提升网络性能： BBR 可以显著提高网络传输速度和稳定性。
降低延迟： 减少数据包丢失，降低网络延迟。
优化带宽利用率： 更充分地利用网络带宽。

确保内核版本是 4.19 以上
``` shell
uname -r
```
编辑文件
``` shell
nano /etc/sysctl.conf
```
最下面粘贴
``` shell
net.core.default_qdisc=fq
net.ipv4.tcp_congestion_control=bbr
```
保存生效
``` shell
sysctl -p
```
输出为 "bbr"，则表示 BBR 已成功启用。
``` shell
cat /proc/sys/net/ipv4/tcp_congestion_control
```
为了使更改完全生效，建议重启系统。