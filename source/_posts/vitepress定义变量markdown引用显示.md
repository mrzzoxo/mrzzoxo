---
title: vitepress定义变量markdown引用显示
date: 2024-12-10 23:24:30
tags:
- vitepress
- markdown
description: vitepress定义变量markdown引用显示
---

编辑 .vitepress\config.mts定义变量

``` mts
  themeConfig: {
    mail: 'pony@gmail.com',
    html: '<a href="http://cn.bing.com" target="_blank">必应一下</a>',
    domain: 'https://cdn.demo.com/',

  }
```

任意markdown文档引用输出

``` markdown
<!--引入数据-->
<script setup>
import { useData } from 'vitepress'
const { theme } = useData()
</script>

<!--直接输出变量内容-->
邮箱：{{theme.mail}}

<!--v-html 可以直接输出运行html代码-->
<p v-html="theme.html"></p>

<!--img引用-->
<img :src="theme.domain + 'images/demo.png'" alt="demo">
```

输出效果

``` 
邮箱：pony@gmail.com

必应一下

<img src="https://cdn.demo.com/images/demo.png" alt="demo">
```