---
title: vue2 组件传值：子传父 $emit( )

index_img: https://img-blog.csdnimg.cn/20190714184804189.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





**子组件：**
首先在data中声明要传给父组件的数据，然后使用$emit函数。如下图：
![](https://img-blog.csdnimg.cn/20190714183814657.png)

**父组件：**
![](https://img-blog.csdnimg.cn/20190714184516398.png)

效果：
对比图1里msg声明的数据，是不是显示出来了？
![](https://img-blog.csdnimg.cn/20190714184804189.png)

#### 不知道怎么[父传子](https://blog.csdn.net/qq_42618566/article/details/94920082)
