---
title: js数组 数据量大进行切片重组

index_img: https://img-blog.csdnimg.cn/14400795f53048c0bdba7cb3fbd1af62.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- 数组切片



---











![](https://img-blog.csdnimg.cn/14400795f53048c0bdba7cb3fbd1af62.png)



```javascript
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>数组切片</title>
	</head>
	<body>
		<button onclick="dataSplite()">切片</button>


		<script>
			function dataSplite() {
				let data = []; // 准备假数据
				for (let i = 1; i <= 105; i++) {
					data.push({
						id: i,
						name: "🍊" + i,
					})
				}
				console.log(data);




				// 梳理逻辑
				// splitedData.push(data.slice(0, 10))
				// splitedData.push(data.slice(10, 20))
				// splitedData.push(data.slice(20, 30))
				// splitedData.push(data.slice(30, 40))
				// splitedData.push(data.slice(40, 50))
				// splitedData.push(data.slice(50, 60))
				// splitedData.push(data.slice(60, 70))
				// splitedData.push(data.slice(70, 80))
				// splitedData.push(data.slice(80, 90))
				// splitedData.push(data.slice(90, 100))
				// splitedData.push(data.slice(100, data.length))

				const max = 10; // 每片多少
				const length = Math.ceil(data.length / max); // 一共几片
				// 处理切片
				let splitedData = [];
				for (let index = 0; index < length; index++) {
					console.log(index * max, index * max + max);
					splitedData.push(data.slice(index * max, index * max + max))
				}
				console.log(splitedData);
			}
		</script>
	</body>
</html>
```


