---
title: uniapp 请求封装，拦截器：请求拦截、响应拦截
index_img: https://img-blog.csdnimg.cn/direct/f807585b5b564daa8dc1234f0a1ec409.png
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序



---





![](https://img-blog.csdnimg.cn/direct/f807585b5b564daa8dc1234f0a1ec409.png)


# 全局请求封装
```javascript
export function http(path, params = {}, loading = true, method = "POST") {
	console.log('%c请求拦截：', ' background:orange', params);
	if (loading) {
		uni.showLoading({
			title: "加载中",
			mask: true
		});
	};

	return new Promise((resolve, reject) => {
		uni.request({
			header: {
				Authorization: uni.getStorageSync("Authorization") || ""
			},
			url: import.meta.env.VITE_BASE_URL + path,
			method,
			data: params,
			async success(res) {
				uni.hideLoading();
				resolve(res.data);
				console.log('响应拦截：', path, params, res.data);
				if (res.data?.code !== 0) {
					uni.showToast({
						icon: "error",
						duration: 2000,
						title: res.data.msg
					});
				}

			},
			fail(err) {
				uni.hideLoading();
				uni.reLaunch({
					url: "/pages/status/service/error"
				})
				reject(err);
			},
			complete() {
				// uni.hideLoading();    // 在showToast之前执行会受影响
			}
		});
	});
};
```

# 局部业务接口封装
![](https://img-blog.csdnimg.cn/direct/a9fb2190e1a94161a6ecdde3ee802ab6.png)


# 使用接口
![](https://img-blog.csdnimg.cn/direct/791392cabd4a48e7b0b747b418eec615.png)


