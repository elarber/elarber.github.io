---
title: uniapp 微信小程序配置条件编译

index_img: https://img-blog.csdnimg.cn/07cf2e70b9204635a1befda1fa47e7ce.png
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---




1. [项目中增加`package.json`文件](https://uniapp.dcloud.net.cn/collocation/package.html)
![](https://img-blog.csdnimg.cn/07cf2e70b9204635a1befda1fa47e7ce.png)


2. 在[编辑器](https://www.dcloud.io/hbuilderx.html)中的==运行==菜单下就会有你配置的环境了
![](https://img-blog.csdnimg.cn/17219642e7b442ac90d73c4fb71d360e.png)

3. 点击运行，那么程序就会有你的运行条件了
我运行的是`WX-TEST`，那么`WX-PRODUCTION`的条件就不运行。如图：
![](https://img-blog.csdnimg.cn/0d3ee7011d4045f8a1cac5844dd8f465.png)


```json
{
	"uni-app": {
		"scripts": {
			"wx-test": {
				"title": "【微信】测试版",
				"env": {
					"UNI_PLATFORM": "mp-weixin",
					"AAAAA":"123"
				},
				"define": {
					"WX-TEST": true
				}
			},
			"wx-production": {
				"title": "【微信】正式版",
				"env": {
					"UNI_PLATFORM": "mp-weixin",
					"VUE_APP_BASE_URL": "https://www.edo-iot.com"
				},
				"define": {
					"WX-PRODUCTION": true
				}
			}
		}
	}
}

```






