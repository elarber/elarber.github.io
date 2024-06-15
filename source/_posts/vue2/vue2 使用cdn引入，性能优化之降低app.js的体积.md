---
title: vue2 使用cdn引入，性能优化之降低app.js的体积

index_img: https://img-blog.csdnimg.cn/37e6116b9ca44618904d5e87d02388bd.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





# 配置
## vue.config.js文件：
![](https://img-blog.csdnimg.cn/37e6116b9ca44618904d5e87d02388bd.png)

```javascript
  chainWebpack: config => {
    config.plugin('html').tap(args => {
      args[0].CDNs = CDNs;
      return args
    });
  }
```

## index.html文件：
![](https://img-blog.csdnimg.cn/b905181102a342ed89211a0f7a0ffdb5.png)


```html
<!DOCTYPE html>
<html lang="">

<head>
  <title><%= VUE_APP_TITLE %></title>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=7">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <meta name="author" content="亿度物联" />
  <meta name="description" content="这是一个轻量级的操作平台前端解决方案，适用于多数开发场景。基于vue2x开发框架和热门的 element-ui组件库实现。内置了Vue全家桶技术栈、打包Gzip技术，引入了bootstrap-icons、Font Awesome4等图标库，封装了动态路由、权限验证、请求拦截、响应拦截、接口封装和复制文本、数字千位符、cdn方法、全局监听摁钮的防抖、事件节流等实用小功能。集成了一系列常用好用的小插件，免去技术选型和技术试错的困扰。运用了vue过滤器、vue指令、vue混入、vue组件，将vue的优势发挥的淋漓尽致。最大的优点就是足够轻量，易拓展、好上手、可塑性强">
  <meta name="keywords" content="vue,vue全家桶,开源vue架构,初始化vue架构,vue底层配置,vue项目">
  <meta name="copyright" content="版权亿度物联所有。All Rights Reserved" />
  <link rel="icon" type="image/x-ico" href="/img/logo.icon">
  <% for (let path of htmlWebpackPlugin.options.CDNs.css) { %>
    <link href="<%= path %>" rel="preload" as="style" />
    <link href="<%= path %>" rel="stylesheet" />
  <% } %>
</head>

<body>
  <div id="app"></div>






  <% for (let path of htmlWebpackPlugin.options.CDNs.js) { %>
    <script defer src="<%= path %>"></script>
  <% } %>
</body>

</html>
```



重启项目，调试面板看看
# 效果
![](https://img-blog.csdnimg.cn/c74b290fee16424c928b1634f7456db5.png)
