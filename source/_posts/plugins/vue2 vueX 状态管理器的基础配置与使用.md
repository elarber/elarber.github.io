---
title: vue2 vueX 状态管理器的基础配置与使用

index_img: https://img-blog.csdnimg.cn/20200330191253171.png
lazyload: true
categories:
- 前端插件使用
tags:
- vueX



---











#### 初始化VueX 
1. 安装
   > 在项目目录执行命令`npm install vuex --save`



2. 配置
	```javascript
	import Vue from 'vue'
	import Vuex from 'vuex'

	Vue.use(Vuex)
		
	const store = new Vuex.Store({
		//初始的常量集
		state: {},
		//触发改变参数
    	mutations: {},
		//异步触发改变参数
	    actions: {}
	})
	
	export default store
	```
如图：
![vueX  的配置与使用](https://img-blog.csdnimg.cn/20200330191208109.png)

3. 在main.js全局引入

```javascript
	import store from '@/store/index.js'
	











	new Vue({
	  el: '#app',
	  store, // 这里
	  router,
	  render: h => h(App),
	  template: '<App/>',
	}).$mount('#app')
```

#### 使用
**存：**
定义个变量，case
![vueX  的配置与使用](https://img-blog.csdnimg.cn/20200330191253171.png)


**取：**
`this.$store.state.变量名`
![vueX  的配置与使用](https://img-blog.csdnimg.cn/20200330191318545.png)

改变case的值：
定义个add函数：
![vueX  的配置与使用](https://img-blog.csdnimg.cn/20200330191355692.png)

触发改变：
`this.$store.commit('函数名');`
![vueX  的配置与使用](https://img-blog.csdnimg.cn/20200330191421873.png)

效果：
![vueX  的配置与使用](https://img-blog.csdnimg.cn/20200330191842927.gif#pic_center)

![vueX  的配置与使用](https://img-blog.csdnimg.cn/20200330191803798.png)

---
#### VueX中的核心内容
> **state**： 存放状态
> **mutations**： state成员操作
> **getters**： 加工state成员给外界
> **actions**： 异步操作
> **modules**： 模块化状态管理

---
小型状态管理器：[https://blog.csdn.net/qq_42618566/article/details/107657250](https://blog.csdn.net/qq_42618566/article/details/107657250)

---
拓展阅读：[https://www.jianshu.com/p/2e5973fe1223](https://www.jianshu.com/p/2e5973fe1223)


---
持久化存储

` npm install --save vuex-persist `

```javascript
	import VuexPersist from 'vuex-persist';
	// 创建对象，借助浏览器缓存，存入localStorage
	const vuexLocal = new VuexPersist({
	  	storage: window.localStorage  // 可选，sessionStorage/indexDB
	})



	export default new Vuex.Store({
		state: {},
		mutations: {},
		plugins: [vuexLocal.plugin]
	})

```


