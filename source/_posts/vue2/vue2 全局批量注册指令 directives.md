---
title: vue2 全局批量注册指令 directives

index_img: https://img-blog.csdnimg.cn/20200804141914937.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web
- 指令


---





![vue 全局批量注册指令](https://img-blog.csdnimg.cn/20200804141914937.png)

```javascript
const directives = {
  focus: (el) => {
    el.focus();
  },
  
}



export default {
  install(Vue) {
    Object.keys(directives).forEach(item => {
      Vue.directive(item, {
        inserted: directives[item]
      })
    })
  }
}
```


![vue 全局批量注册指令](https://img-blog.csdnimg.cn/20200804141957596.png)

```javascript
import directives from './directives/index'



Vue.use(directives);
```

使用方式：
![vue 全局批量注册指令](https://img-blog.csdnimg.cn/20200804142033865.png)

效果：
![vue 全局批量注册指令](https://img-blog.csdnimg.cn/20200804142139613.gif)
