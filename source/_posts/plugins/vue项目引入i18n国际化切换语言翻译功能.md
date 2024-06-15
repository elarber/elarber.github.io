---
title: vue项目引入i18n国际化切换语言翻译功能

index_img: https://img-blog.csdnimg.cn/20200812132552657.gif
lazyload: true
categories:
- 前端插件使用
tags:
- i18n



---













![vue项目引入i18n国际化切换语言翻译功能](https://img-blog.csdnimg.cn/20200812132552657.gif#pic_center)


安装：
```javascript
npm install vue-i18n --save    
```

建立语言资源： `src/assets/languages` 
例如中文和英文文件：
![vue项目引入i18n国际化切换语言翻译功能](https://img-blog.csdnimg.cn/20200812120729720.png#pic_center)


英文文件：
```javascript
export default {
  menu: {
    home: "home",
    msg: "this is an about page"
  },
  content: {
    main: "this is content"
  }
}
```
中文文件：
```javascript
export default {
  menu: {
    home: "首页",
    msg: "这是一个关于页面"
  },
  content: {
    main: "这里是内容"
  }
}

```



配置语言资源：
![vue项目引入i18n国际化切换语言翻译功能](https://img-blog.csdnimg.cn/20200812121159181.png#pic_center)


```javascript
import Vue from 'vue';
import VueI18n from 'vue-i18n';
import elEN from 'element-ui/lib/locale/lang/en'
import elZH from 'element-ui/lib/locale/lang/zh-CN'
import zh from './zh';
import en from './en';




Vue.use(VueI18n);


// 创建vue-i18n实例
export default new VueI18n({
  locale: localStorage.getItem('language') || 'zh', // 设置默认语言
  messages: {
    zh: Object.assign(zh, elZH),
    en: Object.assign(en, elEN),
  }
})
```


入口文件`main.js`注册：
![vue项目引入i18n国际化切换语言翻译功能](https://img-blog.csdnimg.cn/2020081212093447.png#pic_center)


```javascript
import i18n from './assets/languages/index'



Vue.use(ElementUI, {
  i18n: (key, value) => i18n.t(key, value)
});
```

使用：
![vue项目引入i18n国际化切换语言翻译功能](https://img-blog.csdnimg.cn/20200812132931465.png#pic_center)



```html
<template>
  <div class="index">
    <h1>{{ $t('menu.home') }}</h1>
    <div>{{ $t(msg) }}</div>
    <div class="tab">
       <span @click="tab('zh')">中文</span>|
       <span @click="tab('en')">英文</span>
     </div>
  </div>
</template>

<script>
export default {
  name: "Index",
  data() {
    return {
      language: "zh",
      options: [
        {
          value: "zh",
          label: "中文",
        },
        {
          value: "en",
          label: "英文",
        },
      ],
      msg: "content.main",
	}
  },
  methods: {
    tab(type) {
      localStorage.setItem("language", type); // 语言选择记录
      this.$i18n.locale = type;
    }
  }
}

</script>
```
