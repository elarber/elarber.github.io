---
title: js 判断首次加载和刷新

index_img: https://img-blog.csdnimg.cn/20210406144950129.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---








![](https://img-blog.csdnimg.cn/20210406144950129.png)

```javascript

  // console.log(performance);
  switch (performance.navigation.type) {
    case 0:
      console.log("首次加载出来了");
      break;
    case 1:
      console.log("页面刷新完了");
      break;
  }

```


![](https://img-blog.csdnimg.cn/20210406145215322.gif#pic_center)





