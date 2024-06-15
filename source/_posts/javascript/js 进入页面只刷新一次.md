---
title: js 进入页面只刷新一次

index_img: https://img-blog.csdnimg.cn/20200224192549236.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












```javascript
if (location.href.indexOf("#reloaded") == -1) {
	location.href = location.href + "#reloaded";
	location.reload();
}
```

**效果：**
注意看唰一下白屏时
![js 进入页面只刷新一次](https://img-blog.csdnimg.cn/20200224192549236.gif)
