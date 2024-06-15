---
title: js 闭包案例

index_img: https://img-blog.csdnimg.cn/2020030322211418.png
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
		function square(num1,num2){
			function squares(x){
				return x*x;
			}
			return squares(num1)+squares(num2);
		};
		console.log(square(3,6));  // 3的平方加6的平方

	</script>
</body>
</html>
```

![js 闭包案例](https://img-blog.csdnimg.cn/20200303221359119.png)


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
		function one(){
			let name = "全易";
			function two(){
				return name;   // 此时two()含有了全易值
			}
			return two();     // 此时one()含有了全易值
		};

		console.log(one());

	</script>
</body>
</html>
```

![js 闭包案例](https://img-blog.csdnimg.cn/2020030322211418.png)
