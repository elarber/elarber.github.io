---
title: vue axios接口请求 跨越配置

index_img: https://img-blog.csdnimg.cn/20200630131310680.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





![vue axios接口请求 跨越配置](https://img-blog.csdnimg.cn/20200630131310680.png)


==proxyTable==里配置：
```json
 '/api': {
   target: 'http://192.168.11.250:9090', // 接口请求的基路径
   changeOrigin: true, // 开启跨越
   pathRewrite: {
     '^/api': '' //用 /api 代替上面targe的路径，我们调接口时路径直接用/api代替。 比如我要调用'http://192.168.11.250:9090/user/add'接口，那直接写/api/user/add即可
   }
 }
```


axios封装时直接用了`/api`
![vue axios接口请求 跨越配置](https://img-blog.csdnimg.cn/20200630132023360.png)
