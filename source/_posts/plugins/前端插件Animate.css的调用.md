---
title: 前端插件Animate.css的调用

index_img: https://img-blog.csdnimg.cn/20191108121124811.gif
lazyload: true
categories:
- 前端插件使用
tags:
- Animate.css



---











**引入：**

```html
<head>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.2/animate.min.css">
</head>
```
或者：`npm install animate.css --save`

**调用：**
为元素设置动画需要添加==animated==到元素的类上。然后追加动画名称、延迟时间、动画速度
```html
<div class="animated fadeInDown delay-2s fast"></div>
```
延迟时间和动画速度不加就代表按照默认执行

延迟时间：
![](https://img-blog.csdnimg.cn/20191108115722416.png)

动画速度：
![](https://img-blog.csdnimg.cn/20191108115742695.png)
![](https://img-blog.csdnimg.cn/20191108121124811.gif)

----
最简单的例子：

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.2/animate.min.css">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>前端插件Animate.css的调用</title>
	<style type="text/css">
		h1{
			padding: 50px 0;
			background-color: aquamarine;
			text-align: center;
			margin: 0 auto;
			color: #0072ff;
		}
	</style>
</head>
<body>
	<h1 class="animated bounceInUp delay-2s fast">前端插件Animate.css的调用测试测</h1>
</body>
</html>
```

![](https://img-blog.csdnimg.cn/20191116131053390.gif)


