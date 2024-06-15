---
title: js 进入一个页面自动执行触发点击事件

index_img: https://img-blog.csdnimg.cn/20191028173939988.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











进入页面自动执行点击事件，**跳转的有些快**，注意看那一瞬间的变化！
```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>测试</title>
</head>

<body>

	<a id="aid" href="https://blog.csdn.net/qq_42618566" οnclick="alert('clicked');">触发onclick</a>

	
	<script>
		// 进入页面立即触发
		(()=>{
			// 兼容IE
		    if(document.all) {
		        document.getElementById("aid").click();
		    }
		    // 兼容其它浏览器
		    else {
		        var e = document.createEvent("MouseEvents");
		        e.initEvent("click", true, true);
		        document.getElementById("aid").dispatchEvent(e);
		    }
		})();


	/*	// 也可写个定时器进行触发
		setTimeout(()=>{
			// 兼容IE
		    if(document.all) {
		        document.getElementById("aid").click();
		    }
		    // 兼容其它浏览器
		    else {
		        var e = document.createEvent("MouseEvents");
		        e.initEvent("click", true, true);
		        document.getElementById("aid").dispatchEvent(e);
		    }
		},3000); // 3秒后执行	*/
	</script>
</body>

</html>
```


立即执行：
![js 进入一个页面自动执行触发点击事件](https://img-blog.csdnimg.cn/20191028173939988.gif)



定时执行：
![js 进入一个页面自动执行触发点击事件](https://img-blog.csdnimg.cn/20191028174138674.gif)

