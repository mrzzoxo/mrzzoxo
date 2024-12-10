---
title: Debian安装Samba
date: 2024-11-28 18:14:53
tags:
- debian
- samba
description: Debian安装Samba
---
1 、安装 samba
```shell
apt install samba
```
2 、创建 samba 用户组
```shell
groupadd samba
```
3 、创建不可登录账号 mrzz, 并加入 samba 用户组
```shell
useradd -M -g samba -s /sbin/nologin mrzz
```
4 、设置 mrzz 用户密码
```shell
smbpasswd -a mrzz
```
5 、创建共享目录
```shell
mkdir /mrzz
```
6 、赋予权限
```shell
chmod 777 /mrzz
```
7 、备份原 smb.conf
```shell
cd /etc/samba && cp smb.conf smb.conf.bak
```
8 、编辑 smb.conf，最下面插入新共享参数
```shell
nano /etc/samba/smb.conf
```
配置参数
```shell
#名称
[mrzz]
#分享描述
comment = 明日之子目录
#分享路径
path = /mrzz
#允许访问用户
valid users = mrzz
#允许写入用户
write list = mrzz
```
无需登录的共享目录配置参数

```shell
#名称
[samba]
#分享描述
comment = 无需登录的共享目录
#分享路径
path = /samba
#可写权限
writable = yes
#匿名访问
guest ok = yes
#新文件权限为 777
create mask = 0777
#新目录权限为 777
directory mask = 0777
```
9 、重启 smb 服务
```shell
systemctl restart smbd
```
更多参数设置
```shell
comment = Guest Directories ; 共享描述，当鼠标悬浮在目录上时会显示
path = /home/guest          ; 共享目录路径
browseable = yes/no         ; 设置共享是否可浏览，如果 no 就表示隐藏，需要通过 IP+共享名称进行访问
writable = yes/no           ; 设置共享是否具有可写权限
read only = yes/no          ; 设置共享是否具有只读权限
valid users = username      ; 设置允许访问共享的用户，例如 valid users = user1,user2,@group1,@group2（多用户或组使用逗号隔开，@group 表示 group 用户组）
write list = username       ; 设置在共享具有写入权限的用户，例如例如 write list  = user1,user2,@group1,@group2（多用户或组使用逗号隔开，@group 表示 group 用户组）
invalid users = username    ; 设置不允许访问共享的用户
public = yes/no             ; 设置共享是否允许匿名访问
guest ok = yes/no           ; 功能同 public 一样
create mask = 0777          ; 创建的文件权限为 777
directory mask = 0777       ; 创建的目录权限为 777
```