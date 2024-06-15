---
title: js 函数防抖

index_img: https://img-blog.csdnimg.cn/20200311183318484.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












其实就是延后执行。但不是把延后过程中的所有事情都延后然后执行出来，而是延后执行你最后一次操作


例如用户输入搜索，不是每次打字都搜出来，而是搜最后一次结果
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title></title>
	<style>
		
	</style>
</head>
<body>
	<input type="text">
	<button>搜索</button>

	<script>
		const inp=document.querySelector('input');
		const btn=document.querySelector('button');
		var counDown;
		inp.onkeyup=()=>{
			clearTimeout(counDown)
			counDown=setTimeout(()=>{
				console.log(inp.value);
			},2000);
		}
	</script> 
</body>
</html>
```
![js 函数防抖](https://img-blog.csdnimg.cn/20200311183318484.gif)
