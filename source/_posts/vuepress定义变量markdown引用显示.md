---
title: vuepress定义变量markdown引用显示
date: 2024-12-13 12:59:28
tags:
- vuepress
- markdown
description: vuepress定义变量markdown引用显示
---

编辑 ```docs\.vuepress\config.js```

``` js
  theme: defaultTheme({
    mail: 'pony@gmail.com',
    img: 'https://img.com/',
    html: '<a href="https://cn.bing.com/" taeget="_blank">必应一下</a>'
  })
```

markdown文档引用输出

``` markdown
<!--直接输出-->
邮箱：{{$theme.img}}

<!--url引用-->
<img :src="$theme.img + 'images/images/vuepress.png'" alt="vuepress">

<!-- v-html 输出运行html代码-->
<p v-html="$theme.html"></p>
```

输出效果

```
邮箱：pony@gmail.com

<img src="https://img.com/images/vuepress.png" alt="vuepress">

必应一下
```