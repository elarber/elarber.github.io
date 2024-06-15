---
title: vue做SEO网络优化【prerender-spa-plugin】

index_img: https://img-blog.csdnimg.cn/20200715114628130.png
lazyload: true
categories:
- 前端插件使用
tags:
- rerender-spa-plugin



---










#### 一、安装插件：
```json
npm install --save prerender-spa-plugin
npm install --save vue-meta-info
```

### 二、`webpack.prod.conf.js`文件中配置两个：

 1. 
```javascript
const PrerenderSPAPlugin = require('prerender-spa-plugin')
const Renderer = PrerenderSPAPlugin.PuppeteerRenderer
```
2. 

```javascript
new PrerenderSPAPlugin({
      // Required - The path to the webpack-outputted app to prerender.
      staticDir: path.join(__dirname, '../dist'),
      // Required - Routes to render.
      routes: [ '/', '/cart', '/list'],
      renderer: new Renderer({
        inject: {
          foo: 'bar'
        },
        headless: false,
        // 在 main.js 中 document.dispatchEvent(new Event('render-event'))，两者的事件名称要对应上。
        renderAfterDocumentEvent: 'render-event'
      })
}),
```

如图：
![全易](https://img-blog.csdnimg.cn/20200715113717136.png)

### 三、在main.jswenjian 中添加加载使用:

```javascript
import MetaInfo from 'vue-meta-info'
Vue.use(MetaInfo);



new Vue({
  el: '#app',
  router,
  components: { App },
  template: '<App/>',
  mounted() {
    document.dispatchEvent(new Event('render-event'))
  },
}).$mount('#app')
```

如图：![vue做SEO网络优化【prerender-spa-plugin】](https://img-blog.csdnimg.cn/20200715113926904.png)

### 四、然后去页面文件中添加seo的代码：
比如首页：

```json
  metaInfo: {
    title: "我是首页头", // set a title
    // set meta
    meta: [
      {
        name: "keyWords",
        content: "我是首页关键字"
      },
      {
        name: "description",
        content: "我是首页描述"
      }
    ]
  },
```

如图：
![vue做SEO网络优化【prerender-spa-plugin】](https://img-blog.csdnimg.cn/20200715114129427.png)


至此可以执行编译命令，自己起一个服务看看效果了
比如我的node服务：
![vue做SEO网络优化【prerender-spa-plugin】](https://img-blog.csdnimg.cn/20200715114628130.png)


