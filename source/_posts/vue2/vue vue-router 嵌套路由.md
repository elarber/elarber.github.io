---
title: vue vue-router 嵌套路由

index_img: https://img-blog.csdnimg.cn/20190707225818899.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





在router目录下的index.js路由配置文件里使用children嵌套路由，如下：
![](https://img-blog.csdnimg.cn/20190707224429487.png)

嵌套路由配置好，就需要在**嵌套的页面**展示**被嵌套**的页面了
![](https://img-blog.csdnimg.cn/20190707230410601.png)

router-view 为什么写这？因为刚在配置路由的时候是在child下配置的呀。

效果如下：
![](https://img-blog.csdnimg.cn/20190707225152918.png)
![](https://img-blog.csdnimg.cn/20190707225228983.png)
![](https://img-blog.csdnimg.cn/20190707225253220.png)
![](https://img-blog.csdnimg.cn/2019070722531038.png)


到此有个问题来了，点击进入child页面时（图2）是不是发现右侧时空白的？此时是不是需要默认进这个页面时右侧显示成图3那样呢？
那么就需要**重定向**一下了。让一进child页面时定向到one页面。

操作如下：
![](https://img-blog.csdnimg.cn/20190707225818899.png)
此时点击进child页面就是图2效果了。
