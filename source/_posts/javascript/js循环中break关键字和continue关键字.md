---
title: js循环中break关键字和continue关键字

index_img: https://img-blog.csdnimg.cn/20200303214510917.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












##### break：
间断循环

```javascript
for(let i=0; i<10; i++){
	if(i==5){
			break;
		};
	console.log(i);
};
```
![js循环中break关键字和continue关键字](https://img-blog.csdnimg.cn/20200303214510917.png)

##### continue
跳过什么继续循环

```javascript
for(let i=0; i<10; i++){
		if(i==5){
			continue;
		};
	console.log(i);
};
```
![js循环中break关键字和continue关键字](https://img-blog.csdnimg.cn/20200303214346300.png)
