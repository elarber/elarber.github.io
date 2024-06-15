---
title: 原生js 自定义页面右击的菜单

index_img: https://img-blog.csdnimg.cn/20191023113543571.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











**本来是这样的：**
![](https://img-blog.csdnimg.cn/20190930114521838.png)
**自定义：**


```html
	<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>自定义菜单栏</title>
	<style>
		#menu {
			height: 180px;
			overflow-x: hidden;
			border: 1px solid #cacaca;
			box-shadow: 2px 2px 5px #d4d4d4;
			position: absolute;
			/*自定义菜单相对与body元素进行定位*/
			display: none;
		}

		#menu ul {
			padding: 0;
			list-style: none;
		}

		#menu ul li {
			width: 130px;
			height: 25px;
			line-height: 25px;
			padding: 0 10px;
		}
	</style>

</head>

<body>
	<div id="menu">
		<ul>
			<a href="#">
				<li>菜单1</li>
			</a>
			<a href="#">
				<li>菜单2</li>
			</a>
			<a href="#">
				<li>菜单3</li>
			</a>
			<a href="#">
				<li>菜单4</li>
			</a>
			<a href="#">
				<li>菜单5</li>
			</a>
			<a href="#">
				<li>菜单6</li>
			</a>
			<a href="#">
				<li>菜单6</li>
			</a>
			<a href="#">
				<li>菜单6</li>
			</a>
			<a href="#">
				<li>菜单6</li>
			</a>
			<a href="#">
				<li>菜单6</li>
			</a>
		</ul>
	</div>




	<script>
		const menu = document.querySelector("#menu");

		window.oncontextmenu = function (e) {
			e.preventDefault();  //去掉浏览器默认的contextmenu事件，否则会和自定义的右键事件同时出现
			const menuHeight = menu.offsetHeight;
			const menuWidth = menu.offsetWidth;

			if (menuWidth + e.clientX > window.innerWidth) {
				menu.style.left = e.clientX - menuWidth + 5 + 'px';
			} else {
				menu.style.left = e.clientX + 'px';
			}
			if (menuHeight + e.clientY > window.innerHeight) {
				menu.style.top = e.clientY - menuHeight + 5 + 'px';
			} else {
				menu.style.top = e.clientY + 'px';
			}

			menu.style.width = '125px';
			menu.style.display = 'block';
		}
		window.onclick = function () {
			menu.style.display = 'none';
		}
	</script>
</body>

</html>
```

效果：
![](https://img-blog.csdnimg.cn/20191023113543571.gif)

