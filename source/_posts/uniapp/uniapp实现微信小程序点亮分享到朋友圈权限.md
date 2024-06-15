---
title: uniapp实现微信小程序点亮分享到朋友圈权限

index_img: https://img-blog.csdnimg.cn/20201127160130967.png
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---






在可分享的页面文件里写：

```javascript
onShareAppMessage(){
	return {
		from:"menu"
	}
},
onShareTimeline(){},
```
![uniapp实现点亮分享到朋友圈权限](https://img-blog.csdnimg.cn/20201127155933184.png)
微信官方文档：
![](https://img-blog.csdnimg.cn/2020112716011381.png)
![](https://img-blog.csdnimg.cn/20201127160130967.png)

---

效果：
![](https://img-blog.csdnimg.cn/20201127160204190.png)









