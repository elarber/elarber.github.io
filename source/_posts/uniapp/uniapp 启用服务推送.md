---
title: uniapp 启用服务推送

# index_img: 
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---






# 一定要放在事件直接执行的地方，比如点击事件
```javascript
// 一定要放在事件直接执行的地方，比如点击事件
uni.requestSubscribeMessage({
  tmplIds: [''],  // 需要订阅的消息模板的id的集合
  success (res) {
    console.log(res);
    // 然后业务代码
  }
})
```

[官方说明](https://uniapp.dcloud.io/api/other/requestSubscribeMessage?id=requestsubscribemessage)




