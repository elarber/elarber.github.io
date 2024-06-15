---
title: uniapp 游客模式下的数据封装

index_img: https://img-blog.csdnimg.cn/20200930114640536.png
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---



1. 建立游客模式的数据：
![](https://img-blog.csdnimg.cn/20200930114640536.png#pic_center)
![](https://img-blog.csdnimg.cn/20200930115103453.png#pic_center)

2. 全局请求封装
![](https://img-blog.csdnimg.cn/eb383ebf953a4a278df10d08d3154162.png)



3. 全局接口封装：
主要就是在这区分调用线上数据还是本地假数据
![](https://img-blog.csdnimg.cn/20200930115033410.png#pic_center)





#### 调用：
调用没区别，还是本来的调法，不用任何改动
如图：
![](https://img-blog.csdnimg.cn/20200930115309531.png#pic_center)











