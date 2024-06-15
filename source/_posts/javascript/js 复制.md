---
title: js 复制

index_img: https://img-blog.csdnimg.cn/20200427103200454.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










![js 复制](https://img-blog.csdnimg.cn/20200427103200454.gif#pic_center)


```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<button onClick="copy(this)">复制</button>
	<div class="content">我被复制</div>
	<input id="copy_box" type="text" value="" style="position: fixed;top: -100px;"/>
	
	<script>
		function copy() {
			let content=document.querySelector(".content").innerText;
		    let input =  document.getElementById("copy_box");
		    input.value = content;  //复制的内容赋值给input，因为input值有select()功能  
		    input.select();	//选中input框的内容
		    document.execCommand("Copy");	// 执行浏览器复制命令
		}
	</script>
</body>
</html>
```
**input不能直接display:none!!!**





