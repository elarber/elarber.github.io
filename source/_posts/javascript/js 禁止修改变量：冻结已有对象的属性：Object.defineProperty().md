---
title: js 禁止修改变量：冻结已有对象的属性：Object.defineProperty()

index_img: https://img-blog.csdnimg.cn/6c68daee04824fbb8828f695b4504a20.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











`Object.defineProperty()`的使用

![](https://img-blog.csdnimg.cn/6c68daee04824fbb8828f695b4504a20.png)


```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<script>
			let people = {
				name: "quanyi",
				position: "developer",
				age: 18
			};

			Object.defineProperty(people, "age", {
				enumerable: false,    //  是否出现在对象的枚举属性中
				configurable: false,  // 是否可以被删除
				writable: false,      // 是否可以被修改
				// value: 2              // 定义该属性的值
			});

			people.age = 3;
			console.log(people.age) // 不会被改
		</script>
	</body>
</html>

```


