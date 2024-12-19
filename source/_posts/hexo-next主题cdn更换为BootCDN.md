---
title: hexo next主题cdn更换为BootCDN
date: 2024-12-11 14:23:45
tags:
- hexo
- next
- cdn
- bootcdn
description: BootCDN 是一个免费、开源、且内容丰富的 CDN（内容分发网络），主要提供 Bootstrap、jQuery、Vue.js 等流行前端框架和库的托管服务。
---
BootCDN 是一个免费、开源、且内容丰富的 CDN（内容分发网络），主要提供 Bootstrap、jQuery、Vue.js 等流行前端框架和库的托管服务。它通过将这些文件缓存到全球各地的服务器上，极大地加快了网页加载速度，提升了用户体验。BootCDN 所收录的开源项目主要同步于 cdnjs 开源项目仓库。

1、编辑next主题配置文件 ```_config.next.yml```

``` yml
internal: custom 

plugins: custom

custom_cdn_url: https://cdn.bootcdn.net/ajax/libs/${cdnjs_name}/${version}/${cdnjs_file}
```

- BootCDN有备案 国内速度嘎嘎快

---

备用：staticfile

``` yml
custom_cdn_url: https://cdn.staticfile.net/${cdnjs_name}/${version}/${cdnjs_file}
```