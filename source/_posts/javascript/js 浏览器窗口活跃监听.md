---
title: js 浏览器窗口活跃监听

index_img: https://img-blog.csdnimg.cn/20200403143443994.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










![js 浏览器窗口活跃监听](https://img-blog.csdnimg.cn/20200403143443994.gif#pic_center)


```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		/*window.onblur=()=>{
			document.title = '放入后台';
		}

		window.onfocus=()=>{
			document.title = '进入页面';
		}*/



		window.addEventListener('blur', ()=>{
			document.title = '放入后台';
		}, true);

		window.addEventListener('focus', ()=>{
			document.title = '进入页面';
		}, true);
	</script>
</body>
</html>
```





