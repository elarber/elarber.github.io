---
title: css 调用外部字体、自定义字体

index_img: https://img-blog.csdnimg.cn/20191029104216168.png
lazyload: true
categories:
- css


tags:
- css

---





比如使用下图字体：
![css 调用外部字体、自定义字体](https://img-blog.csdnimg.cn/20191029104216168.png)
怎么弄？如下：
![css 调用外部字体、自定义字体](https://img-blog.csdnimg.cn/20191029104036773.png)

效果：
![css 调用外部字体、自定义字体](https://img-blog.csdnimg.cn/20191029104056615.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>测试</title>
	<style>
		@font-face{
			font-family: test;
			src:url('./方正胖头鱼简体.ttf');
		}
		p{
			font-family: test;
		}
	</style>
</head>

<body>
	<p>我是方正胖头鱼简体.ttf字体 我是方正胖头鱼简体.ttf字体 我是方正胖头鱼简体.ttf字体</p>
</body>

</html>
```

