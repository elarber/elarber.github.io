---
title: vue加载进度条   插件vue-nprogress的使用方法

index_img: https://img-blog.csdnimg.cn/20190703135214559.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





**1.在你的项目根目录安装此插件**

```
npm install nprogress --save 
```
如下图：
![](https://img-blog.csdnimg.cn/20190703135214559.png)
**2.待插件安装完毕后在min.js文件中全局引入并配置**

```
import NProgress from 'nprogress'
import 'nprogress/nprogress.css'







		//     ajax请求progress
Vue.http.interceptors.push((request, next) => {
  NProgress.start();
  
  next((response)=>{
    NProgress.done();
  });
});



	//    路由请求progress
router.beforeEach(transition => {
  NProgress.start();
});
 
router.afterEach(transition => {
  NProgress.done();
});
```
如下图：
![](https://img-blog.csdnimg.cn/20190703134816480.png)
