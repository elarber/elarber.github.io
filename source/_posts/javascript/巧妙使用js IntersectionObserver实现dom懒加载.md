---
title: 巧妙使用js 巧妙使用js IntersectionObserver实现dom懒加载实现dom懒加载

index_img: https://img-blog.csdnimg.cn/45a5a374c0b74b639184f6e68eab8e20.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- IntersectionObserver
- dom懒加载



---













# 效果
![请添加图片描述](https://img-blog.csdnimg.cn/45a5a374c0b74b639184f6e68eab8e20.gif)


# 源码

```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>IntersectionObserver</title>
	</head>
	<body style="text-align: center">
		<div id="container"></div>
		<div id="load">加载中...</div>
	</body>
	<script>
		const containerDOM = document.querySelector('#container');
		const loadingDOM = document.querySelector('#load');
		let index = 0;

		const loading = (count) => {
			[...Array(count).keys()].forEach((key) => {
				const h1DOM = document.createElement('h1');
				h1DOM.innerHTML = `${key + index}`;
				containerDOM.appendChild(h1DOM)
			})
			index += count;
		}

		const observer = new IntersectionObserver((entries) => {
			entries.forEach(entrie => {
				if (entrie.isIntersecting) {
					loading(25);
				}
			})
		});
		observer.observe(loadingDOM)
	</script>
</html>
```
