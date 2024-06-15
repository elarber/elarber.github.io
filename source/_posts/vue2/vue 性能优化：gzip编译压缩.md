---
title: vue 性能优化：gzip编译压缩

index_img: https://img-blog.csdnimg.cn/20200723091944121.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





 1. 安装1.1.2版本的`compression-webpack-plugin`插件：
高版本会报错
```javascript
npm install --save-dev compression-webpack-plugin@1.1.2
```

2. 打开==config/index.js==文件，找到build对象中的productionGzip属性，值改成`true`：
![vue 性能优化：gzip编译压缩](https://img-blog.csdnimg.cn/20200723091944121.png)


3. 打开==build/webpack.prod.conf.js==文件，CompressionWebpackPlugin实例的`asset`属性名，改为`filename`：
![vue 性能优化：gzip编译压缩](https://img-blog.csdnimg.cn/20200723092037644.png)

---

至此，可以编译看看：
编译项目后会发现生成的静态文件里面新增了后缀为`.gz`的文件就是前端方面配置成功了
![vue 性能优化：gzip编译压缩](https://img-blog.csdnimg.cn/2020072309244965.png)


如果此时将项目部署到已开启了`gzip`的服务器如`nginx`里面之后，访问浏览器即可看到浏览器响应头的信息是已压缩的文件：
![](https://img-blog.csdnimg.cn/20210708111703778.png)
