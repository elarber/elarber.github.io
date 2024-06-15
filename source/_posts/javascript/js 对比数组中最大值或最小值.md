---
title: js 对比数组中最大值或最小值

index_img: https://img-blog.csdnimg.cn/20191018130254983.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












> 使用`Math.max()`、`Math.min()`

![](https://img-blog.csdnimg.cn/20191018130254983.png)

```javascript
	var arr = [1,2,3,4,5,6,7,8,9];
	
	console.log(Math.max(...arr));
	console.log(Math.min(...arr));
```

输出结果：
![](https://img-blog.csdnimg.cn/20191018130001529.png)
