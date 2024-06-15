---
title:  vue2 小型状态管理器

index_img: https://img-blog.csdnimg.cn/20200729103403917.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





大型项目中的数据状态会比较复杂，一般都会使用 `vueX` 来管理。但在一些小型项目或状态简单的项目中，为了管理几个状态而引入一个库，显得有些笨重。
在 2.6.0+ 版本中，新增的 `Vue.observable` 可以帮助我们解决这个尴尬的问题，它能让一个对象变成响应式数据

#### 建立`store`文件：
![vue 小型状态管理器](https://img-blog.csdnimg.cn/20200729103403917.png)

```javascript
import Vue from 'vue'

export const state = Vue.observable({
  count: 0
})

export const mutations = {
  SET_COUNT(number) {
    if (number > 0) {
      state.count = number
    }
  }
}

```

#### 使用：
![vue 小型状态管理器](https://img-blog.csdnimg.cn/20200729103545276.png)

```html
 <div>
  {{ count }}
   <el-button @click="setCount">加</el-button>
 </div>

<script>
import { state, mutations } from "@/store";

export default {
computed: {
  count() {
     return state.count;
   },
 },
 methods: {
  setCount() {
    mutations.SET_COUNT(100);
  },
 }
}
</script>
```
