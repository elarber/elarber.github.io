---
title: vue2 父组件调用子组件的模态框：子与父组件之间来回传值

index_img: https://img-blog.csdnimg.cn/20191029135607692.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





**定义打开模态框的动作：**
在父组件：
![vue-cli 父组件调用子组件的模态框：子与父组件之间来回传值](https://img-blog.csdnimg.cn/20191029135433367.png)在子组件：
![vue-cli 父组件调用子组件的模态框：子与父组件之间来回传值](https://img-blog.csdnimg.cn/20191029135607692.png)
**定义关闭模态框的动作：**
在子组件：
![vue-cli 父组件调用子组件的模态框：子与父组件之间来回传值](https://img-blog.csdnimg.cn/20191029140019549.png)

在父组件:
![vue-cli 父组件调用子组件的模态框：子与父组件之间来回传值](https://img-blog.csdnimg.cn/20191029140258333.png)

---

**代码：**
父组件：

```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <a
          href="https://vuejs.org"
          target="_blank"
        >
          Core Docs
        </a>
      </li>
      <li>
        <a
          href="https://forum.vuejs.org"
          target="_blank"
        >
          Forum
        </a>
      </li>
      <li>
        <a
          href="https://chat.vuejs.org"
          target="_blank"
        >
          Community Chat
        </a>
      </li>
      <li>
        <a
          href="https://twitter.com/vuejs"
          target="_blank"
        >
          Twitter
        </a>
      </li>
      <br>
      <li>
        <a
          href="http://vuejs-templates.github.io/webpack/"
          target="_blank"
        >
          Docs for This Template
        </a>
      </li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li>
        <a
          href="http://router.vuejs.org/"
          target="_blank"
        >
          vue-router
        </a>
      </li>
      <li>
        <a
          href="http://vuex.vuejs.org/"
          target="_blank"
        >
          vuex
        </a>
      </li>
      <li>
        <a
          href="http://vue-loader.vuejs.org/"
          target="_blank"
        >
          vue-loader
        </a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
        >
          awesome-vue
        </a>
      </li>
    </ul>
    <h2><el-button type="primary" @click="showModel = true">点击打开 Dialog</el-button></h2>
     <ModelSon :site="showModel" @AlertBox="closeModel" />
  </div>
</template>

<script>
import ModelSon from './model'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      showModel:false
    }
  },
  components:{
    ModelSon
  },
  methods:{
    closeModel(siteChenge) {
        this.showModel = siteChenge
      },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
```
子组件：

```html
<template>
  <div class="model">
    <el-dialog
      title="提示"
      :visible.sync="site"
      width="30%">
      <span>这是一段信息</span>
      <span slot="footer" class="dialog-footer">
        <el-button type="primary" @click="closeModel">关 闭</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: 'model',
  data () {
    return {
      
    }
  },
  props:{
    site:{
      type:Boolean,
      default:false
    }
  },
  methods:{
    closeModel() {
      this.$emit("AlertBox", false);
    },
  }
}
</script>

<style scoped>

</style>

```
