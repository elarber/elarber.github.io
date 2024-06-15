---
title: js 获取鼠标位置的各种值

index_img: https://img-blog.csdnimg.cn/20200114124133802.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












- ==clientX/Y：==
鼠标触发点相对浏览器可视区域的X、Y坐标。当然其中不包括工具栏和滚动栏。
![js 获取鼠标位置的各种值](https://img-blog.csdnimg.cn/20200114124133802.png)
- ==screenX/Y：==
鼠标触发点相对于显示器的X、Y坐标
![js 获取鼠标位置的各种值](https://img-blog.csdnimg.cn/20200114124229894.png)
- ==pageX/Y：==
鼠标触发点相对于当前整个网址页面的X、Y坐标
![js 获取鼠标位置的各种值](https://img-blog.csdnimg.cn/20200114124418450.png)
- ==layerX/Y：==
鼠标触发点相对于被触发元素的左上角的距离。值和offsetX/Y是相同的。`要求其元素的postion为retative或者absolute，否则返回相对html文档区域左上角距离`
![js 获取鼠标位置的各种值](https://img-blog.csdnimg.cn/20200114124617334.png)
- ==offsetX/Y：==
鼠标触发点相对于被触发元素的左上角的距离。`一般左上角基准点不包括边框，在边框上会返回负值。`
![js 获取鼠标位置的各种值](https://img-blog.csdnimg.cn/20200114124736925.png)
[js 获取元素在页面种的位置](https://blog.csdn.net/qq_42618566/article/details/104432442)
