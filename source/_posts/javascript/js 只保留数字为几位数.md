---
title: js 只保留数字为几位数

index_img: https://img-blog.csdnimg.cn/20200312125058466.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












> toPrecision()

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	
	<script>
		var number=3.14159169999999999999999999;
		console.log(number.toPrecision(10));
	</script>
</body>
</html>
```
保留10位数，**不包括小数点的10位数**，自动进行了四舍五入
![js 只保留数字为几位数](https://img-blog.csdnimg.cn/20200312125058466.png)

