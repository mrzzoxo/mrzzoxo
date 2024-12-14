---
title: WordPress 安装 Redis Object Cache
date: 2024-11-29 19:13:43
tags:
- wordpress
- redis
description: Redis Object Cache 是一款 WordPress 插件，它利用高性能的 Redis 数据库来缓存 WordPress 对象，从而显著提升网站的访问速度。
---
什么是 Redis Object Cache？
Redis Object Cache 是一款 WordPress 插件，它利用高性能的 Redis 数据库来缓存 WordPress 对象，从而显著提升网站的访问速度。通过将频繁访问的数据存储在内存中，减少了对数据库的查询次数，有效缓解了服务器压力。

安装 Redis Object Cache
安装插件：

登录 WordPress 后台。
进入 「插件」 -> 「安装插件」 。
搜索 「Redis Object Cache」，找到并安装该插件。

配置插件

在 wp-config.php 插入
``` php
define('WP_REDIS_HOST', '127.0.0.1'); //redis服务器IP
define('WP_REDIS_PORT', 6379); // 默认端口 6379
define('WP_REDIS_DATABASE', 1); // 选择使用的 Redis 数据库
define('WP_REDIS_PASSWORD', 'Redis密码'); // 如果设置了密码
```
登录 WordPress 后台。
进入 「插件」 -> 「启用插件」 -> 「启用对象缓存」

<img src="{% config img %}images/2be16a658f43.png" alt="启用对象缓存">