---
title: 基于js的原生插件：canvas绚丽的动态气泡背景

index_img: https://img-blog.csdnimg.cn/20191205170816300.gif
lazyload: true
categories:
- 前端插件使用
tags:
- bubbly-bg



---












![基于js的原生插件：canvas绚丽的动态气泡背景](https://img-blog.csdnimg.cn/20191205171155365.gif)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>js</title>
</head>
<body>


  <script src="https://cdn.jsdelivr.net/npm/bubbly-bg@1.0.0/dist/bubbly-bg.js"></script>
  <script>bubbly();</script>
  
</body>
</html>
```

![基于js的原生插件：canvas绚丽的动态气泡背景](https://img-blog.csdnimg.cn/20191205170816300.gif)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>js</title>
</head>
<body>

  <canvas id="demo" width="400" height="300"></canvas>


  <script src="https://cdn.jsdelivr.net/npm/bubbly-bg@1.0.0/dist/bubbly-bg.js"></script>
  <script>
    bubbly({
     canvas: document.getElementById("demo")
    });
  </script>
</body>
</html>
```
使用文档：[https://github.com/tipsy/bubbly-bg](https://github.com/tipsy/bubbly-bg)
