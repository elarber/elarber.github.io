---
title: js 封装好的滚动滑动到指定位置的效果

index_img: https://img-blog.csdnimg.cn/20200221162617268.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












使用：
> rollTo(距离,时间);

例如：

> rollTo(500, 200);
> 滚动到距离页面顶部`500px`的位置 动画时间为`200ms`


源码：
```javascript
// 封装滚动的效果功能
const rollTo = (distance = 0, time) => {
	if (!time) {
		scrollTo(0, distance);
		return distance;
	}
	const spacingTime = 20; // 设置循环的间隔时间  值越小消耗性能越高
	let index = time / spacingTime; // 计算循环的次数
	let now = document.body.scrollTop + document.documentElement.scrollTop; // 获取当前滚动条位置
	let rollDistance = (distance - now) / index; // 计算每次滑动的距离
	let rollTimer = setInterval(() => {
		if (index > 0) {
			index--;
			rollTo(now += rollDistance);
		} else {
			clearInterval(rollTimer); // 清除计时器
		}
	}, spacingTime);
};
```


效果：
![js 封装好的滚动滑动到指定位置的效果](https://img-blog.csdnimg.cn/20200221162617268.gif)

