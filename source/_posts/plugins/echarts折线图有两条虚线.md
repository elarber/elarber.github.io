---
title: echarts折线图有两条虚线

index_img: https://img-blog.csdnimg.cn/20200918095413183.png
lazyload: true
categories:
- 前端插件使用
tags:
- echarts



---












![echarts折线图有两条虚线](https://img-blog.csdnimg.cn/2020091809570972.png#pic_center)



```javascript
itemStyle: {
	normal: {
		lineStyle: { //系列级个性化折线样式
			width: 2,
			type: 'dashed' // 虚线
		}
	}
}
```

![echarts折线图有两条虚线](https://img-blog.csdnimg.cn/20200918095413183.png#pic_center)

