---
title: js 函数体里查看或修改本函数的参数

index_img: https://img-blog.csdnimg.cn/20200303213615715.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










> ##### `关键字：arguments`

示例：
```javascript
function cas(name,age,position){
	arguments[2] = "backend"; // 将小标为2的参数修改为backend
	console.log(arguments[2]);
};

cas("全易","18","frontend");
```
如图：
![js 函数体里查看或修改本函数的参数](https://img-blog.csdnimg.cn/20200303213615715.png)


