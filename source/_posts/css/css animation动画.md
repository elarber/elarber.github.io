---
title: css animation动画

index_img: https://img-blog.csdnimg.cn/20191011180948218.png
lazyload: true
categories:
- css


tags:
- css

---







 引用动画：
```css
animation：动画名称 动画时间 运动曲线 何时开始 播放次数 是否反方向;
```

定义动画： 
```css
 @keyframs 动画名称  {
	 0% {
	 
	 }
　　50%{
	　　
	}
　　100%{
　　
	}
}
```

例如：

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<style> 
#myDIV{
	width:300px;
	height:200px;
	background:red;
	animation:mymove 3s infinite;
}

@keyframes mymove
	{
	/*
		from {background-color:red;}
		to {background-color:blue;}
	*/
		0%{
			background-color:red;
		}
		50%{
		background-color:blue;
		}
		100%{
			background-color:red;
		}
	}
</style>

</head>
<body>

<p>背景颜色逐渐地从红色变化到蓝色：<p>
<div id="myDIV"></div>

</body>
</html>
```

效果：
![](https://img-blog.csdnimg.cn/20200122170538810.gif)

---

运动曲线：
![](https://img-blog.csdnimg.cn/20191011180902336.png)
播放次数：
![](https://img-blog.csdnimg.cn/20191011180926810.png)

是否反方向：

![](https://img-blog.csdnimg.cn/20191011180948218.png)


