---
title: uni-app 地图拖拽后，回到我的位置

index_img: https://img-blog.csdnimg.cn/20210225110936702.gif
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---




![](https://img-blog.csdnimg.cn/20210225110936702.gif#pic_center)


html部分：
这里注意map标签要加上`show-location`
```html
<map class="map" id="map" ref="map" :latitude="latitude" :longitude="longitude" show-location show-compass enable-3D enable-overlooking enable-poi :markers="covers" @markertap="markerFunc" :style="{ 'height': setHeight + 'px' }">
	<cover-view class="my-location">
		<cover-image class="img" src="https://course.jchen.art/static/images/icon-location.png" @click="getMyLocation"></cover-image>
	</cover-view>
</map>
```

css部分：
```css
.my-location {
	position: fixed;
		right: 30rpx;
		bottom: 30rpx;
	
		.img {
			width: 50rpx;
			height: 50rpx;
		}
	}
```

js部分：
```css
// 在onReady里：
this.map = uni.createMapContext("map", this);   // 得到map对象



// 方法：
getMyLocation() {
	this.map.moveToLocation();
}
```


---

使用文档：[https://uniapp.dcloud.io/api/location/map?id=createmapcontext](https://uniapp.dcloud.io/api/location/map?id=createmapcontext)
![](https://img-blog.csdnimg.cn/20210225110635974.png)





