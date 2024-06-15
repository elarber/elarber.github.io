---
title: html写法 点击跳转到新页面的具体指定位置  ||  视图区域：添加锚点

index_img: https://img-blog.csdnimg.cn/20191028134337178.gif
lazyload: true
categories:
- html
tags:
- html



---











比如从**子页面**跳到**首页**的==用户需求==
![html写法 点击跳转到新页面的具体指定位置  ||  视图区域：添加锚点](https://img-blog.csdnimg.cn/20191028134337178.gif)

要跳转到哪个页面的视图区域，就在哪个页面的视图标签上定义好 ==id==
![html写法 点击跳转到新页面的具体指定位置  ||  视图区域：添加锚点](https://img-blog.csdnimg.cn/20191028144058536.png)

然后在当前页面跳转标签==a标签==的路径后面紧跟追加上 ==#名字==（ 例如 ==../index.html **#need**== ）
![html写法 点击跳转到新页面的具体指定位置  ||  视图区域：添加锚点](https://img-blog.csdnimg.cn/2019102814440622.png)

**原理：**
a标签使用锚点定位： `<a href="#id名">跳转</a>`，就跳到哪个`<div id="名"></div>`上


---





#### 来个简单小案例：
![html写法 点击跳转到新页面的具体指定位置  ||  视图区域：添加锚点](https://img-blog.csdnimg.cn/20191116110849494.gif)

```html
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>导航栏定位视图区域</title>
	<style>
		body{
			padding: 0;
			margin: 0;
		}
		#one, #two, #three, #foure, #five, #six{
			height: 400px;
			text-align: center;
			padding: 100px 0;
			margin: 40px 0;
		}
		#two{
			background: darkred;
		}
		#three{
			background: lightblue;
		}
		#foure{
			background: yellowgreen;
		}
		#five{
			background: sandybrown;
		}
		#six{
			background: lawngreen;
		}
		header{
			text-align: center;
			padding: 20px 0;
			background: aliceblue;
		}
	</style>
</head>
<body>
	<header>
		<a href="#one">去one</a>
		<a href="#two">去two</a>
		<a href="#three">去three</a>
		<a href="#foure">去foure</a>
		<a href="#five">去five</a>
		<a href="#six">去six</a>
	</header>
	<div id="one">
		<h3>我是one</h3>
	</div>
	<div id="two">
		<h3>我是two</h3>
	</div>
	<div id="three">
		<h3>我是three</h3>
	</div>
	<div id="foure">
		<h3>我是foure</h3>
	</div>
	<div id="five">
		<h3>我是five</h3>
	</div>
	<div id="six">
		<h3>我是six</h3>
	</div>
</body>
</html>
```



