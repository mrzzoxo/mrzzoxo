---
title: hexo安装配置sitemap
date: 2024-12-11 00:19:58
tags:
- hexo
- sitemap
description: hexo安装配置sitemap
---
1、执行指令安装
``` shell
npm install hexo-generator-sitemap
```

2、编辑 _config.yml 加入配置信息
``` yml
sitemap:
  path: 
    - sitemap.xml
    - sitemap.txt
  template: ./sitemap_template.xml
  template_txt: ./sitemap_template.txt
  rel: false
  tags: true
  categories: true
  ```

  参数说明
  ```
path：定义了生成的sitemap文件的路径和名称，这里有两个路径，一个是sitemap.xml，另一个是sitemap.txt。
template：指定了用于生成XML格式的sitemap的模板文件，路径为./sitemap_template.xml。
template_txt：指定了用于生成TXT格式的sitemap的模板文件，路径为./sitemap_template.txt。
rel：这个配置项设置为false，通常用于指定是否在生成的sitemap中包含rel="alternate"的链接，这里表示不包含。
tags：设置为true，表示在sitemap中包含标签（tags）的链接。
categories：设置为true，表示在sitemap中包含分类（categories）的链接。
  ```

  如果不想 ```页面/文章``` 生成，插入 ```sitemap: false```

```
---
title: 
date: 
sitemap: false
---
```

sitemap_template.xml 模板代码

<details>
  <summary>点击展开/折叠</summary>
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {% for post in posts %}
  <url>
    <loc>{{ post.permalink | uriencode }}</loc>
    {% if post.updated %}
    <lastmod>{{ post.updated | formatDate }}</lastmod>
    {% elif post.date %}
    <lastmod>{{ post.date | formatDate }}</lastmod>
    {% endif %}
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>
  {% endfor %}

  <url>
    <loc>{{ config.url | uriencode }}</loc>
    <lastmod>{{ sNow | formatDate }}</lastmod>
    <changefreq>daily</changefreq>
    <priority>1.0</priority>
  </url>

  {% for tag in tags %}
  <url>
    <loc>{{ tag.permalink | uriencode }}</loc>
    <lastmod>{{ sNow | formatDate }}</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.2</priority>
  </url>
  {% endfor %}

  {% for cat in categories %}
  <url>
    <loc>{{ cat.permalink | uriencode }}</loc>
    <lastmod>{{ sNow | formatDate }}</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.2</priority>
  </url>
  {% endfor %}
</urlset>
```
</details>

sitemap_template.txt 模板代码

``` txt
{% for post in posts %}{{ post.permalink | uriencode }}
{% endfor %}{{ config.url | uriencode }}
{% for tag in tags %}{{ tag.permalink | uriencode }}
{% endfor %}{% for cat in categories %}{{ cat.permalink | uriencode }}
{% endfor %}
```

执行指令看看sitemap文件有没有正常生成到 public

``` shell
hexo generate
```
来源：<a target="_blank" rel="nofollow noopener" href="https://github.com/hexojs/hexo-generator-sitemap">github.com/hexojs/hexo-generator-sitemap</a>