---
title: js柯里化函数

index_img: https://img-blog.csdnimg.cn/2020030322430636.png
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
	<title>Document</title>
</head>
<body>
	<script>
		function currying(num1){
			return function (num2){
				return function(num3){
					return num1+num2+num3;
				}
			}
		};

		//测试
		console.log(currying(3)(5)(1));
		console.log(currying(3)(5)(2));

		//优点：将currying()返回值存入一个变量确定前几位的计算值
		var number=currying(12)(9);
		console.log(number(3));  //然后可以不断的修改后值
		console.log(number(4));
		console.log(number(5));
	</script>
</body>
</html>
```
![js柯里化函数](https://img-blog.csdnimg.cn/2020030322430636.png)
