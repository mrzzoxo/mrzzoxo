---
title: Windows git 配置多平台多账号
date: 2024-12-04 18:11:29
tags:
- windows
- git
- ssh
- github
- gitee
description: Windows git 配置多平台多账号
---
1 、 Windows 下载安装 git：<a target="_blank" rel="nofollow noopener" href="https://git-scm.com/downloads/win">git-scm.com/downloads/win</a>
国内镜像：<a target="_blank" rel="nofollow noopener" href="https://mirrors.huaweicloud.com/git-for-windows/">mirrors.huaweicloud.com/git-for-windows</a>

2 、打开 git bash

3 、生成 SSH 密钥：```ssh-keygen -t rsa -C "邮箱" -f ~/.ssh/名称```
比如 GitHub，名字可自定义，能记住是用于那个平台的就行

``` shell
ssh-keygen -t rsa -C "pony@gmail.com" -f ~/.ssh/github
```

回车会提示设置密码，留空则不设置密码

4 、打开密钥目录 ```（~/.ssh = C:\Users\用户\.ssh）```

5 、新建 config 文件 （无后缀）, 内容：

```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/github
```

6 、登录 GitHub：```Settings - SSH and GPG keys - New SSH keys```
keys 内容 打开 github.pub 可以看到，全选复制保存到 GitHub 就行

7 、测试连接 （这里的 github.com 是 config 里面的 Host 设置的名称）

``` shell
ssh -T git@github.com
```
回车提示是否连接：yes

8 、提示 successfully 就是连接成功。
```
Hi pony! You've successfully authenticated, but GitHub does not provide shell access.
```
9 、再添加一个 gitee 账号，还是一样生成密钥
名字可自定义，能记住是用于那个平台的就行
```
ssh-keygen -t rsa -C "pony@163.com" -f ~/.ssh/gitee
```
10 、编辑 config 文件, 添加 gitee 配置信息进去
```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/github

Host gitee.com
  HostName gitee.com
  User git
  IdentityFile ~/.ssh/gitee
  ```
11 、登录 gitee：账号设置 - SSH 公钥
公钥内容在 gitee.pub

12 、测试连接
``` shell
ssh -T git@gitee.com
```
如还需要其他平台或者其他账号，重复步骤添加配置即可

---

同平台不同账号，config 里面的 Host 名称不可有重复的 （可以修改任意名字）

如：
```
Host github_xiaoming
  HostName github.com
  User git
  IdentityFile ~/.ssh/github_xiaoming

Host github_xiaohong
  HostName github.com
  User git
  IdentityFile ~/.ssh/github_xiaohong
  ```
测试链接
``` shell
ssh -T git@github_xiaoming
ssh -T git@github_xiaohong
```
clone 和 push 地址也要改

原：```git@github.com:xiaoming/demo.git```
改：```git@github_xiaoming:xiaoming/demo.git```

原：```git@github.com:xiaohong/demo.git```
改：```git@github_xiaohong:xiaohong/demo.git```