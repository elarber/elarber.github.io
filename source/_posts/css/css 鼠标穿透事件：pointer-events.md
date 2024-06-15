---
title: css 鼠标穿透事件：pointer-events

# index_img: 
lazyload: true
categories:
- css


tags:
- css

---






发现个有意思的css属性：==pointer-events==
语法：

> pointer-events: none 或者 auto;

特性：
- 阻止用户的点击动作产生任何效果
- 阻止缺省鼠标指针的显示
- 阻止CSS里的 hover 和 active 状态的变化触发事件
- 阻止JavaScript点击动作触发的事件

示例：

```html
<!DOCTYPE html>
<html>
<head>
	<title>示例</title>
	<style>
	 a[href="http://example.com"] {
       pointer-events: none;
  	}
	</style>
</head>
<body>
   <ul>
	    <li><a href="https://www.baidu.com/">百度 能点击</a></li>
	    <li><a href="http://example.com">这是不能点击的链接</a></li>
	</ul>
</body>
</html>
```


