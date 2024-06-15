---
title: 超好用的前端全屏插件：vue-fullscreen

index_img: https://img-blog.csdnimg.cn/cf9a3abc97b04c578dee7339f14b5d7d.gif
lazyload: true
categories:
- 前端插件使用
tags:
- vue-fullscreen



---













![](https://img-blog.csdnimg.cn/cf9a3abc97b04c578dee7339f14b5d7d.gif#pic_center)



# 官网：[vue-fullscreen](https://mirari.cc/2017/08/14/%E5%85%A8%E5%B1%8F%E5%88%87%E6%8D%A2%E7%BB%84%E4%BB%B6vue-fullscreen/)

# 安装
> npm install vue-fullscreen


# 引入
> import VueFullscreen from 'vue-fullscreen'
> Vue.use(VueFullscreen)

# 使用

```html
<template>
  <fullscreen
    :page-only="true"
    v-model="fullscreen"
    :exit-on-click-wrapper="false"
    fullscreen-class="big-view bg-white"
  >
    <div>content</div>
    <button type="button" @click="toggle">{{ fullscreen?"退出":"进入" }}全屏</button>
  </fullscreen>
</template>

<script>
/**
 * @author        全易
 * @time          2022-01-14 10:52:32  星期五
 * @description   数据大屏
 **/

export default {
  data() {
    return {
      fullscreen: false,
    }
  },
  methods: {
    toggle() {
      this.fullscreen = !this.fullscreen
    },
  },
}
</script>

<style lang="less" scoped>
.big-view {
  z-index: 99;
}
</style>
```
