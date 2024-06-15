---
title: vue2 让组件自动按需加载

index_img: https://img-blog.csdnimg.cn/direct/858f28de6a62489f9652d5284579dd34.gif
lazyload: true
categories:
- vue2


tags:
- web
- vue2



---




# 插件
> unplugin-vue-components

# 配置
在vue.config.js文件：

```javascript
const AutoComponents = require('unplugin-vue-components/webpack');
// const { ElementUiResolver } = require('unplugin-vue-components/resolvers')

module.exports = defineConfig({


  configureWebpack: {
     plugins: [
       AutoComponents({
        // resolvers: [ElementUiResolver()]
       })
     ]
  }
})
```
这样就实现了你自定义的组件自动并且按需加载了
在components目录里开发完，在使用的地方不必引入和注册，可以直接用，标签名就是文件名

# 效果
比如` <power-station-select> `组件
![](https://img-blog.csdnimg.cn/direct/50c17fe8f87345be91cfb01946a4cdaf.png)


![](https://img-blog.csdnimg.cn/direct/bc59bf63329f45de866e60bc15332c28.png)




看，在使用的地方才加载：

![](https://img-blog.csdnimg.cn/direct/858f28de6a62489f9652d5284579dd34.gif#pic_center)