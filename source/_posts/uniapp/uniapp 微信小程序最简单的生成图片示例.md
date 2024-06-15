---
title: uniapp 微信小程序最简单的生成图片示例

index_img: https://img-blog.csdnimg.cn/dddda31f81ab4d85aefe1abe836f421c.gif
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---


![](https://img-blog.csdnimg.cn/dddda31f81ab4d85aefe1abe836f421c.gif#pic_center)



```html
<view  v-show='!toPicture'>
	<!-- 页面的内容 -->
</view>
<canvas v-show='toPicture' canvas-id="save-picture" :disable-scroll="true" style='width:375px;height:580px'></canvas>




<button @tap="toIMG">转图片</button>
```



```javascript
// 变量
toPicture: false




// 按钮点击事件
toIMG() {
	this.toPicture = true;
	uni.showLoading({
		mask: true,
		title: "生成中..."
	});


	// 开始绘画
	const ctx = uni.createCanvasContext("save-picture");
	ctx.fillText('Hello', 20, 20); //描绘文本
	ctx.fillText("能不能？图片啊啊啊啊呀呀呀", 50, 20);
	// ctx.drawImage(_this.imgs, 50, 50); //描绘图片




	// 将绘画转为图片
	const _this = this;
	ctx.draw(false, () => {
		uni.canvasToTempFilePath({
			canvasId: "save-picture",
			width: 376 * 4,
			height: 500 * 4,
			quality: 1,
			fileType: 'jpg',
			success: (res) => {
				console.log(res.tempFilePath);
				uni.hideLoading();
				uni.previewImage({
					urls: [res.tempFilePath],
					longPressActions: {
						itemList: ['发送给朋友', '保存图片', '收藏'],
						success(data) {
							console.log("点击了第" + (data.tapIndex + 1) + "个按钮");
						}
					}
				})
			},
		}, _this);
	});
}
```






