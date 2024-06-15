---
title: js 监听屏幕旋转变化（横屏/竖屏）

index_img: https://img-blog.csdnimg.cn/20200403153456140.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











![js 监听屏幕旋转变化（横屏/竖屏）](https://img-blog.csdnimg.cn/20200403153456140.png)


```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		console.log(screen.orientation);
		window.addEventListener('onorientationchange', ()=>{
			console.log(screen.orientation);
		}, true);
	</script>
</body>
</html>
```

|angle值| 代表的屏幕方向 |
|:--|:--|
| 0 | 竖屏 |
| 90 | 向左横屏 |
| -90/270 | 向右横屏 |
| 180 | 倒屏 |






