---
title: vue2 动态变化标签的属性、事件

index_img: https://img-blog.csdnimg.cn/cbafb18115444c19a3bdd7bb1e1ddbbf.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





![](https://img-blog.csdnimg.cn/cbafb18115444c19a3bdd7bb1e1ddbbf.png)


```html
<template>
  <div class="">
    <el-button :[prop1]="'primary'" :[prop2]="'mini'" @[event]="doSomeing">点击</el-button>
  </div>
</template>

<script>
/**
 * @author        全易
 * @time          2022-08-30 10:32:55  星期二
 * @description   测试动态属性、事件
 **/

export default {
  name: "",
  data() {
    return {
      prop1: "type",
      prop2: "size",
      event: "click",
    };
  },
  methods: {
    doSomeing() {
      console.log("事件执行了");
    },
  },
};
</script>

<style lang="less" scoped>
</style>
```
