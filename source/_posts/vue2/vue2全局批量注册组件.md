---
title: vue2全局批量注册组件

index_img: https://img-blog.csdnimg.cn/20200729094425312.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





![vue-cli 全局封装组件及调用](https://img-blog.csdnimg.cn/20200729094425312.png)

```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Hello',
  data () {
    return {
      msg: '6666666666666666666666666666666666666666'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

```


![vue-cli 全局封装组件及调用](https://img-blog.csdnimg.cn/20200729094502987.png)

```javascript
// 全局设置组件
import Hellow from './Hello.vue'

const components = {
    Hellow
}

export default {
    install(Vue) {
        Object.keys(components).forEach(item => {
            Vue.component(components[item].name, components[item])
        })
    }
}

```

![vue-cli 全局封装组件及调用](https://img-blog.csdnimg.cn/20200729094600900.png)

```javascript
import useCompoents from './components/index'





Vue.use(useCompoents);
```





效果：
![vue-cli 全局封装组件及调用](https://img-blog.csdnimg.cn/20200729094754817.png)
