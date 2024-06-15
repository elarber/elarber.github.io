---
title: js 获取元素在页面中的位置

index_img: https://img-blog.csdnimg.cn/20200221182629703.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











![js 获取元素在页面中的位置](https://img-blog.csdnimg.cn/20200221182629703.png)



```html
<!DOCTYPE html>
<html>

<head>
 <meta charset="utf-8">
</head>
<style>
	div{
		width: 100px;
		height: 120px;
		background-color: red;
		margin: 193px auto;
	}

</style>

<body>

	<div onclick="test">测试</div>

	<script>
		const div = document.querySelector("div");


		console.log("高度：",div.offsetHeight);
		console.log("宽度：",div.offsetWidth);
		console.log("距左边:",div.offsetLeft);
		console.log("距顶部：",div.offsetTop);

	 
	 
	</script>



</body>

</html>
```

没有距离右边和底边的距离值

