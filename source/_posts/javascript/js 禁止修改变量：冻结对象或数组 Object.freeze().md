---
title: js 禁止修改变量：冻结对象或数组 Object.freeze()

index_img: https://img-blog.csdnimg.cn/a0bae2f3162e47f78056c397f06fa7b0.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---









`Object.freeze()`的使用


### 数组：

![](https://img-blog.csdnimg.cn/62ed30abca1a4275ad4a66825ca8ccd7.png)


```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Object.freeze</title>
	</head>
	<body>
		<!-- 
		 https://juejin.cn/post/6844904142993883143
		 -->
		<script>
			let fruits = ["apple", "bananar", "ananas"]
			Object.freeze(fruits)
			fruits[0] = "aaaaa";
			fruits[1] = "bbb";
			console.log(fruits[0]);
			console.log(fruits);
		</script>
	</body>
</html>

```


### 对象：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Object.freeze</title>
	</head>
	<body>
		<script>
			let people = {
				name: "quanyi",
				position: "developer",
				age: 18
			};

			Object.freeze(people);
			people.age = 12; // 可以修改f
			console.log(people.age);

			delete people.position;
			console.log(people.position);

			people.aa = "aa";
			console.log(people);
		</script>
	</body>
</html>

```
![](https://img-blog.csdnimg.cn/a0bae2f3162e47f78056c397f06fa7b0.png)




