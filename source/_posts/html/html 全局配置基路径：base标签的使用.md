---
title: html 全局配置基路径：base标签的使用

# index_img: 
lazyload: true
categories:
- html
tags:
- html



---








全局全局配置基路径使用base标签即可搞定本站的所有需要路径的地方，比如img的src，a的href等

```html
<html>
	<head>
		<base href="https://baike.baidu.com" target="_blank">
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>base标签</title>
	</head>
	<body>
		<a href="/item/%E5%89%8D%E7%AB%AF/5956545" target="_self">前端</a>
		<a href="/item/后端">后端</a>
	</body>
</html>

```





