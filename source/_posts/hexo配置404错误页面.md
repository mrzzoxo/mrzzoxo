---
title: hexo配置404错误页面
date: 2024-12-11 12:36:57
tags:
- hexo
- 404
description: hexo配置404错误页面
---
1、保存 404.html 到 ```\source\_posts``` 目录下

<details>
  <summary>点击展开/折叠</summary>
``` html
<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>404 - 未找到相关页面</title>
    <style>
        /* 全局样式 */
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        h1 {
            color: #333;
        }

        p {
            color: #666;
        }

        /* 404 元素样式 */
        #error {
            font-size: 100px;
            color: #ccc;
        }

        /* 按钮样式 */
        a {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 20px;
            transition: background-color 0.3s ease;
            text-decoration: none;
        }

    </style>
</head>

<body>
    <div id="error">404</div>
    <h1>未找到相关页面</h1>
    <p>抱歉，您访问的页面可能不存在或者被删除！</p>
    <a href="/" >返回首页</a>

</body>

</html>
```

</details>

2、```_config.yml``` 跳过渲染404页面文件，如果不设置 hexo会把404.html当成md文件渲染。

``` yml
skip_render: 
  - 404.html
```

3、hexo渲染生成看效果
``` shell
hexo generate
```