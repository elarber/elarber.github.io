---
title: uniapp 监听更新升级情况

index_img: https://img-blog.csdnimg.cn/20201229144420767.png
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---







放在App.vue的`onShow`里：

```javascript
/* ----------------------------- 检查程序更新情况 ----------------------------- */
const updateManager = uni.getUpdateManager();
// 当向小程序后台请求完新版本信息
updateManager.onCheckForUpdate(function(res) {
	console.log("有更新：", res.hasUpdate); // 请求完新版本信息的回调
});
// 当新版本下载完成
updateManager.onUpdateReady(function(res) {
	uni.showModal({
		title: '更新提示',
		content: '新版本已经准备好，是否重启以应用？',
		success(res) {
			if (res.confirm) {
				updateManager.applyUpdate(); // 新的版本已经下载好
			}
		}
	});
});
// 当新版本下载失败
updateManager.onUpdateFailed(function(res) {
	uni.showModal({
		title: '提示',
		content: '新版小程序下载失败\n请自行退出程序，手动卸载本程序，再运行',
		confirmText: "知道了"
	});
});
```


![](https://img-blog.csdnimg.cn/20201229144420767.png)





