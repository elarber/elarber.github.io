---
title: js 函数节流

index_img: https://img-blog.csdnimg.cn/20200311191513865.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










不管你滚轮滚动有多快，都保持每秒打印一次，保持自己的节奏：
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title></title>
	<style>
		
	</style>
</head>
<body style="height: 5000px">
	

	<script>
		const body=document.querySelector('body');
		var flag=true;

		body.onscroll=()=>{
			if (flag) {
				console.log("匀速打印");
				flag=false;
				setTimeout(()=>{
					flag=true;
				},1000)
			}
		}
	</script> 
</body>
</html>
```
![js 函数节流](https://img-blog.csdnimg.cn/20200311191513865.gif)


