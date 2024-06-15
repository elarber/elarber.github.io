---
title: js 封印对象，使其不能拓展属性：Object.preventExtensions()

index_img: https://img-blog.csdnimg.cn/68beb8879d1f458491ba4d61d9f381d1.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











如果只是不允许添加属性，`Object.preventExtensions()`方法让一个对象变的不可扩展，也就是永远不能再添加新的属性。

![](https://img-blog.csdnimg.cn/68beb8879d1f458491ba4d61d9f381d1.png)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Object.preventExtensions</title>
	</head>
	<body>
		<script>
			let people = {
				name: "quanyi",
				position: "developer",
				age: 18
			};

			Object.preventExtensions(people);
			people.age = 12; // 可以修改f
			console.log(people.age);

			delete people.position;
			console.log(people.position); // 删了

			people.aa = "aa";
			console.log(people);
		</script>
	</body>
</html>

```


