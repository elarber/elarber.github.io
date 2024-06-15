---
title: js 通过监听storage事件，多页面之间实时数据共享

index_img: https://img-blog.csdnimg.cn/20200312121112669.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













**事件始发文件：**
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<input type="text">
	
	<script>
		const input=document.querySelector('input');

		input.onkeyup=()=>{
			localStorage.setItem("test",input.value);
		}
	</script>
</body>
</html>
```


**事件接收文件：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		//事件监听写法：
		window.addEventListener("storage",(e)=>{
			console.log(e)
			console.log("新值：",e.newValue)
		})

		//普通事件写法：
	/*	window.onstorage=(e)=>{
			console.log(e)
			console.log("新值：",e.newValue)
		}*/
	</script>
</body>
</html>
```


效果：
![js 通过监听storage事件，多页面之间实时数据共享](https://img-blog.csdnimg.cn/20200312121112669.gif)


![js 通过监听storage事件，多页面之间实时数据共享](https://img-blog.csdnimg.cn/20200312121101260.png)
