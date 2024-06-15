---
title: uniapp微信小程序唤起微信界面的聊天客服

index_img: https://img-blog.csdnimg.cn/583420e92beb4570b8564a09807091a3.png
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---






### 一、在微信[小程序后台](https://mp.weixin.qq.com/wxamp/wakf?token=2127178594&lang=zh_CN)配置客服人员：
![](https://img-blog.csdnimg.cn/20210121162303829.png)

![](https://img-blog.csdnimg.cn/20210121162440428.png)

### 二、代码部分：

```html
<button open-type="contact" show-message-card session-from send-message-path send-message-title>在线客服</button>
```



![](https://img-blog.csdnimg.cn/583420e92beb4570b8564a09807091a3.png)









