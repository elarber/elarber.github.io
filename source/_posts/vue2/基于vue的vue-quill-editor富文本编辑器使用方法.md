---
title: 基于vue的vue-quill-editor富文本编辑器使用方法

index_img: https://img-blog.csdnimg.cn/d9e29e69d8fe496ab179fb0b777afe82.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





![](https://img-blog.csdnimg.cn/d9e29e69d8fe496ab179fb0b777afe82.png)

# 安装vue-quill-editor富文本编辑器
```
npm install vue-quill-editor
```
# 安装依赖


```
npm install quill
```
# 引入：
三个css文件一定要引入，要不没样式
- 全局引入：在main.js
```javascript
import VueQuillEditor from 'vue-quill-editor'
import 'quill/dist/quill.core.css'
import 'quill/dist/quill.snow.css'
import 'quill/dist/quill.bubble.css'
  
Vue.use(VueQuillEditor)
```

- 局部引入
```javascript
import { quillEditor } from "vue-quill-editor";
import 'quill/dist/quill.core.css'
import 'quill/dist/quill.snow.css'
import 'quill/dist/quill.bubble.css'
  
export default {
  name: "",
  components: {
    quillEditor,
  }
}
```

# 在vue页面中代码如下：
```html
<template>
  <div class="edit_container">
        <quill-editor 
            v-model="content" 
            ref="myQuillEditor" 
            :options="editorOption" 
            @blur="onEditorBlur($event)"
            @focus="onEditorFocus($event)"
            @change="onEditorChange($event)">
        </quill-editor>
        <button v-on:click="saveHtml">保存</button>
    </div>  
</template>

<script>
export default {
  name: 'App',
  data(){
     return {
        content: `<p>hello world</p>`,
         editorOption: {
		 modules: {
	        toolbar: toolbarOptions,
	       },
	       theme: "snow",
	       placeholder: "请输入正文",
	       // Some Quill optiosn...
		}
     }
  },
  computed: {
     editor() {
          return this.$refs.myQuillEditor.quill;
      },
    },
    methods: {
      onEditorReady(editor) {},// 准备编辑器
       onEditorBlur(){}, // 失去焦点事件
       onEditorFocus(){}, // 获得焦点事件
       onEditorChange(){}, // 内容改变事件
       saveHtml:function(event){
         alert(this.content);
       }
   }
}



// 工具栏配置项
// https://quilljs.com/docs/modules/toolbar/      或     https://kang-bing-kui.gitbook.io/quill/wen-dang-document/mo-kuai-modules/toolbar
const toolbarOptions = [
  // 加粗 斜体 下划线 删除线、清除文本格式
  ["bold", "italic", "underline", "strike", "clean"],
  // 链接、图片、视频
  ["link", "image", "video"],
  // 引用  代码块
  ["blockquote", "code-block"],
  // 字体颜色、字体背景颜色
  [{ color: [] }, { background: [] }],
  // 有序、无序列表
  [{ list: "ordered" }, { list: "bullet" }],
  // 上标/下标
  [{ script: "sub" }, { script: "super" }],
  // 缩进
  [{ indent: "-1" }, { indent: "+1" }],
  // 文本方向
  [{ direction: "rtl" }],
  // 对齐方式
  [{ align: [] }],
  // 字体大小
  [{ size: ["small", false, "large", "huge"] }],
  // 标题
  [{ header: [1, 2, 3, 4, 5, 6, false] }],
  // 字体种类
  [{ font: [] }],
];
</script>

<style>
</style>
```




> 官网：


---


也可以使用cdn的方式在`index.html`引入：
![](https://img-blog.csdnimg.cn/788f22c0953040a8ab231295200d49b1.png)
```javascript
  <link rel="stylesheet" href="https://unpkg.com/quill@1.3.7/dist/quill.core.css">
  <link rel="stylesheet" href="https://unpkg.com/quill@1.3.7/dist/quill.snow.css">
  <link rel="stylesheet" href="https://unpkg.com/quill@1.3.7/dist/bubble.core.css">








  <script src="https://unpkg.com/quill@1.3.7"></script>
  <script src="https://unpkg.com/vue-quill-editor@3.0.6"></script>
```


然后在`build/webpack.base.conf.js`文件配置：
![](https://img-blog.csdnimg.cn/3470db0f7bf3484fa06bdfb623402709.png)

那么项目全局都可以用啦
![](https://img-blog.csdnimg.cn/8d6b19d848d840a6a96081cf42abee45.png)



---



>还有一款：[Vditor](https://b3log.org/vditor/?utm_source=ld246.com)
>Vditor 是一款浏览器端的 Markdown 编辑器，支持所见即所得、即时渲染（类似 Typora）和分屏预览模式。它使用 TypeScript 实现，支持原生 JavaScript 以及 Vue、React、Angular 和 Svelte 等框架。
