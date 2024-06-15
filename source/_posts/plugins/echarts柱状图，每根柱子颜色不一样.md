---
title: echarts柱状图，每根柱子颜色不一样

index_img: https://img-blog.csdnimg.cn/20200918094728305.png
lazyload: true
categories:
- 前端插件使用
tags:
- echarts


---
















![echarts柱状图，每根柱子颜色不一样](https://img-blog.csdnimg.cn/20200918094728305.png#pic_center)


```javascript
itemStyle: {
	normal: {
			color: function(params) {
				let colors = ['#23b2ff', '#6de5b7', '#f1af5a'];
				return colors[params.dataIndex];
			}
		}
	}
```

![echarts柱状图，每根柱子颜色不一样](https://img-blog.csdnimg.cn/20200918094623140.png#pic_center)
