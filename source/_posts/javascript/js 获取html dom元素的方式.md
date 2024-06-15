---
title: js 获取html dom元素的方式

# index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---








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

	<div>
		<a href="#"></a>
		<a href="#"></a>
		<a href="#"></a>
		<a id="aid" class="aclass" name="aname" href="http://www.sinmeng.net" οnclick="alert('clicked');">触发onclick</a>
	</div>
	

	<script>
		// (function fn(){
		// 	for(let i=1; i<10; i++){
		// 		document.write('<li>我是li的第 '+i+' 行</li>')
		// 	}
		// })();

		// 两秒后自动点击
		setTimeout(function() {
		    // IE浏览器
		    if(document.all) {
		        document.getElementById("clickMe").click();
		    }
		    // 其它浏览器
		    else {
		        var e = document.createEvent("MouseEvents");
		        e.initEvent("click", true, true);
		        document.getElementById("clickMe").dispatchEvent(e);
		    }
		}, 2000);
	</script>
</body>

</html>
```


**比如获取上面html的的a标签：**
 1. 通过ID获取（getElementById）   

	```javascript
				const aID = document.getElementById('aid');
				console.log(aID);
	
	```

    2. 通过name属性（getElementsByName）
	```javascript
				const aName = document.getElementsByName('aname')[0];
				console.log(aName);
	```
    3. 通过标签名（getElementsByTagName）
	```javascript
		const a = document.getElementsByTagName('a')[0];
				console.log(a);
	```
    4. 通过类名（getElementsByClassName）
	```javascript
			const aClass = document.getElementsByClassName('aclass')[0];
			console.log(aClass);
	
	```
    5. 通过选择器获取一个元素（querySelector）
   
	```javascript
			const querySelector = document.querySelector('#aid');
			console.log(querySelector);
	```
 
    6. 通过选择器获取一组元素（querySelectorAll）
	```javascript
			const SelectorAll = document.querySelector('div');
			console.log(SelectorAll);
	```

    7. 获取html的方法（document.documentElement）是专门获取< html>  这个标签的
	```javascript
			const html= document.documentElement;
			console.log(html);
	```
    8. 获取body的方法（document.body）是专门获取< body>这个标签的。
	```javascript
			const body= document.body;
			console.log(body);
	```




