---
title: vue2 使用ref获取并操作DOM元素

index_img: https://img-blog.csdnimg.cn/20190705211822159.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





获取元素的方法有很多，但在vue中最好用vue提供的方法：ref。
如下图，给想要操作的标签一个属性ref，然后给个值（就是你起的名字，下面要通过这个名字获取，跟原生的方法中class、id一样)
![](https://img-blog.csdnimg.cn/20190705211000910.png)
起好名字后一定要去**mounted**钩子里操作，因为页面执行到这个钩子的时候已经渲染出DOM了。
如下图：
![](https://img-blog.csdnimg.cn/20190705211707858.png)
那么下载这个h3标签已经改成红色了
![](https://img-blog.csdnimg.cn/20190705211822159.png)
