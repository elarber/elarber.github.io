---
title: vue2项目全局监听click点击事件，将其防抖处理

index_img: https://img-blog.csdnimg.cn/7d3990985979406ea22ae900055b94e9.gif
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





比如控制在3s内只执行一次：
![](https://img-blog.csdnimg.cn/7d3990985979406ea22ae900055b94e9.gif#pic_center)



那么在`main.js`里放入：
```javascript
// 防抖处理 - 先执行
const on = Vue.prototype.$on;
Vue.prototype.$on = function (event, fn) {
  // console.log(event,fn);
  let newFN = fn;
  // 全局所有点击事件
  if (event === 'click') {
    let timer;
    let flag = true;
    newFN = function () {
      if (flag) {
        fn.apply(this, arguments)
        flag = false
      }
      clearTimeout(timer)
      timer = setTimeout(function () {
        flag = true
      }, 800)
    }
  }
  on.call(this, event, newFN)
}
}
```

> 全局所有click事件已经被自动监听到，别的地方什么都不用加
