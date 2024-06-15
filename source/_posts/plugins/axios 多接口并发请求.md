---
title: axios 多接口并发请求

index_img: https://img-blog.csdnimg.cn/1808569b65564e0a8b4fb89de98c2988.png
lazyload: true
categories:
- 前端插件使用
tags:
- axios
- 并发请求



---













`axios.all`结合`axios.spread`非常完美

```javascript
const APIs = [axios.post("https://api.github.com/users/ejirocodes")]; // 放多个要请求的promise接口
 axios.all(APIs).then( // 执行并发
   axios.spread((test1, test2, test3) => {
     console.log("----- 所有请求完成 -----");
     console.log("请求1结果", test1);
     console.log("请求2结果", test2);
     console.log("请求3结果", test3);
   })
 );
```


![](https://img-blog.csdnimg.cn/1808569b65564e0a8b4fb89de98c2988.png)

