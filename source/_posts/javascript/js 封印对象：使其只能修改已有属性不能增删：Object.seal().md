---
title: js 封印对象：使其只能修改已有属性不能增删：Object.seal()

index_img: https://img-blog.csdnimg.cn/b26e1c3cdbe94f149784d8e6775cfee1.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












如果只是希望一个对象原有的属性值可以修改，但是不能添加或者删除属性，`Object.seal()`能够帮我们做到

![](https://img-blog.csdnimg.cn/b26e1c3cdbe94f149784d8e6775cfee1.png)


```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Object.seal</title>
	</head>
	<body>
		<script>
			let people = {
				name: "quanyi",
				position: "developer",
				age: 18
			};

			Object.seal(people);
			people.age = 12; // 可以修改f
			console.log(people.age);

			delete people.position;
			console.log(people.position); // 还在，删不了
		</script>
	</body>
</html>

```

