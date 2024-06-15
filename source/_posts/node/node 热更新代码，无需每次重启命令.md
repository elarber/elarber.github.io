---
title: node 热更新代码，无需每次重启命令

index_img: https://img-blog.csdnimg.cn/20200411184217748.png
lazyload: true
categories:
- node
tags:
- node
- 热更新



---












在node中，每次改完代码都需要执行node命令，才能看效果。安装`supervisor`实现热更新

执行`npm install -g supervisor`进行全局安装supervisor
![](https://img-blog.csdnimg.cn/20200411184217748.png)


然后在启动node时使用`supervis`代替node命令：
![](https://img-blog.csdnimg.cn/20200411184528397.png)

这次在代码中改完就可以直接去页面刷新了：
![](https://img-blog.csdnimg.cn/20200411184755678.gif#pic_center)
