---
title: js IntersectionObserver简单案例

index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- IntersectionObserver
- dom懒加载


---













# 效果 ![](https://img-blog.csdnimg.cn/6bf0e24a2350449480a1f0620c52278c.gif#pic_center)
# 源码
```html
<!DOCTYPE html>
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<meta http-equiv="X-UA-Compatible" content="IE=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<title>IntersectionObserver</title>
		<style>
			div {
				height: 700px;
			}
		</style>
	</head>
	<body>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>

		<script>
			let observer = new IntersectionObserver((entries) => {
				entries.forEach(entry => {
					entry.target.innerText = entry.isIntersecting ? '测试' : '';
					entry.target.style["background-color"] = entry.isIntersecting ? 'red' : 'blue';
					entry.target.style["font-size"] = entry.isIntersecting ? '80px' : '';
				})
			}, {
				root: null, // 根元素，null为视口
				threshold: 0.5 //重叠率 0.0-1.0  重叠率达到要求后触发事件 
			});

			document.querySelectorAll('div').forEach(element => {
				observer.observe(element)
			});
		</script>
	</body>
</html>
```

