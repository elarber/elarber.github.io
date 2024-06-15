---
title: js 原生开发：实现页面带参跳转：从传参到接参

index_img: https://img-blog.csdnimg.cn/2019111620000896.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












目前我知道有两种方法：
#### 1.通过地址栏的跳转链接带参
![js 原生开发：实现页面带参跳转：从传参到接参](https://img-blog.csdnimg.cn/20191116184811222.png)
==index.html==

```html
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>带参跳转过去</title>
	<style>
		body{
			text-align: center;
		}
	</style>
</head>
<body>
	<h1>我是准备<a href="">跳转</a>的页面</h1>
	<script>
		// 定义的要传过去的参数
		var param ={
			name:'quanyi',
			age:'666'
		} ;
		
		
		document.querySelector('a').onclick = ()=>{
			a.href = `./new_file.html?name=${param.name}&&age=${param.age}`; // a标签点击时给herf属性赋值：链接和参数     【传参】
		}
	</script>
</body>
</html>
```

==new_file.html==

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>接收跳过来带的参数</title>
		<style>
			body{
				text-align: center;
			}
		</style>
	</head>
	<body>
		<h1>我是跳转过来的页面，还带了刚才的参数过来</h1>
		<h4>注意看地址栏，参数追加在链接 ? 的后面</h4>
		<h4>带过来的参数是：<span></span></h4>
		<script>
			var url = location.search.slice(1); // 从location对象中的search属性得到地址栏里 ? 后面的参数       【接参】
			document.querySelector('span').innerText = url; // 输出到span标签上看看
		</script>
	</body>
</html>
```
效果如下：
![js 原生开发：实现页面带参跳转：从传参到接参](https://img-blog.csdnimg.cn/20191116185054486.gif)

---

#### 2.通过localStorage传参
![js 原生开发：实现页面带参跳转：从传参到接参](https://img-blog.csdnimg.cn/20191116202225915.png)

==index.html==

```html
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>准备跳过去的页面</title>
	<style>
		body{
			text-align: center;
		}
	</style>
</head>
<body>
	<h1>我是准备<a href="./new_file.html">跳转</a>的页面</h1>
	
	<script>
		// 定义要传的参数
		const param = {
			name:'全易',
			age:'23',
			sex:'girl',
			position:'font-end developer',
			blogurl:'https://blog.csdn.net/qq_42618566'
		}
		/* //如果是多条数据加上这个数组JSON.stringify(param)改为JSON.stringify(array)
		var array = [];
		array.push(param); */
		const params = JSON.stringify(param); // 因为localStorage只能存字符串，所以需要转化成JSON 字符串。
		localStorage.setItem('params',params);
	</script>
</body>
</html>
```

==new_file.html==

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>跳过来的页面</title>
		<style>
			body{
				text-align: center;
			}
		</style>
	</head>
	<body>
		<h1>我是跳转过来的页面</h1>
		<h4>取的参数如下：</h4>
		<div style="min-width: 480px; max-width: 36%;margin: 0 auto; text-align: left;">
			<h4>姓名：<span class="name"></span></h4>
			<h4>性别：<span class="sex"></span></h4>
			<h4>职业：<span class="position"></span></h4>
			<h4>csdn：<a class="link" href=""></a></h4>
		</div>
		
		<script>
			// 取参并转为json对象
			const param = JSON.parse(localStorage.params);
			// 获取页面元素并赋值
			document.querySelector('.name').innerText = param.name;
			document.querySelector('.sex').innerText = param.sex;
			document.querySelector('.position').innerText = param.position;
			document.querySelector('.link').innerText = param.blogurl;
			document.querySelector('.link').href = param.blogurl;
		</script>
	</body>
</html>
```
该方式的原理就是两个页面之间有个中转站，就相当于**快递员**(存数据的页面)**把快递**(数据)**放到了快递站**(localStorage)，**然后你**(取数据的页面)**去快递站**(localStorage)**去取。**
效果如下：
![js 原生开发：实现页面带参跳转：从传参到接参](https://img-blog.csdnimg.cn/2019111620000896.gif)

