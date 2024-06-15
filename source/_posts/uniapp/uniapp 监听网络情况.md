---
title: uniapp 监听网络情况

index_img: https://img-blog.csdnimg.cn/202012291452288.png
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---






#### 局部监听：
放在页面文件的`onShow()`里即可
网络有变化`uni.onNetworkStatusChange()`就会执行输出网络情况
```javascript
uni.onNetworkStatusChange(function (res) {
    console.log(res.isConnected);
    console.log(res.networkType);
});
```

---

#### 全局监听
放在App.vue的`onShow()`里，搭配vueX使用：
![](https://img-blog.csdnimg.cn/202012291452288.png)






