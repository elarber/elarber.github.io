---
title: 使用go()和back()两种返回上一页的区别

index_img: https://img-blog.csdnimg.cn/2019060615521724.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













## go(-1): 原页面表单中的内容会丢失；
history.go(-1):后退+刷新；

history.go(1) ：前进
## back(): 原页表表单中的内容会保留；
history.back():后退 ；

history.back(0) 刷新； 

history.back(1)：前进
![](https://img-blog.csdnimg.cn/2019060615521724.png)