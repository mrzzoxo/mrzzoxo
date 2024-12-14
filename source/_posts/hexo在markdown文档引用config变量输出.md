---
title: hexo在markdown文档引用config变量输出
date: 2024-12-14 11:40:14
tags:
- hexo
- markdown
description: hexo在markdown文档引用config变量输出
---

1、安装 hexo-tag-config

``` shell
npm install hexo-tag-config --save
```

2、任意markdown文档引用 ```_config.yml``` 变量输出

``` markdown
博客域名：{% config url %}
```

输出效果

```
博客域名：https://blog.com
```
---

也支持自定义的变量

在 ```_config.yml``` 插入

``` yml
mail: pony@gmail.com
cdn: https://cdn.com/
html: <a href="https://cn.bing.com">必应一下</a>
```

任意markdown文档引用

``` markdown
邮箱：{% config mail %}

<img src="{% config img %}images/hexo.png" alt="hexo">

<p>{% config html %}</p>
```

输出效果

```
邮箱：pony@gmail.com

<img src="https://cdn.com/images/hexo.png" alt="hexo">

必应一下

```

---

参考来源：
<a target="_blank" rel="nofollow noopener" href="https://github.com/hexojs/hexo/issues/2756#issuecomment-451710749">github.com/hexojs/hexo/issues/2756#issuecomment-451710749</a>
<a target="_blank" rel="nofollow noopener" href="https://github.com/yoshinorin/hexo-tag-config">github.com/yoshinorin/hexo-tag-config</a>