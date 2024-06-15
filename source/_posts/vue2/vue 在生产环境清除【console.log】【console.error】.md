---
title: vue 在生产环境清除【console.log】【console.error】

index_img: https://img-blog.csdnimg.cn/2020071916365652.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





vue init webpack的项目：
在`build/webpack.prod.conf.js`文件里改成这样一段代码：

```javascript
uglifyOptions: {
  mangle: {
  	safari10: true
  },
  compress: {
    warnings: false,
    drop_debugger: true,//console
    drop_console: true,
    pure_funcs: ['console.log', 'console.error']//移除console
  },
},
sourceMap: config.build.productionSourceMap,
cache: true,
parallel: true
```
就是新加：2-4行，7-9行和13行


如图：
![vue 在生产环境清除 console.log console.error](https://img-blog.csdnimg.cn/2020071916365652.png)




---


vue create的项目：
在`vue.config.js`文件：

```javascript
configureWebpack: config => {
    // 生产环境取消 console.log
    if (process.env.NODE_ENV === 'production') {
      config.optimization.minimizer[0].options.terserOptions.compress.drop_console = true
    }
  },
```
