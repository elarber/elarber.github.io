---
title: js 获取浏览器屏幕的宽度和高度

index_img: https://img-blog.csdnimg.cn/20191016131903372.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













分两种：
1. ==不包括==滚动条和工具栏的宽度或高度：
```javascript
	window.innerWidth;  // 宽
	window.innerHeight;  // 高
```
就是`红框`内的部分：
![](https://img-blog.csdnimg.cn/20191016131903372.png)

 2. ==包括==滚动条和工具栏的宽度或高度：

```javascript
	window.outerWidth;  // 宽
	window.outerHeight; // 高
```
就是`蓝框`内的部分：
![](https://img-blog.csdnimg.cn/20191127104904289.png)
