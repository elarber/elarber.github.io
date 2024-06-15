---
title: vue 导航守卫配置

index_img: https://img-blog.csdnimg.cn/20200712235030460.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





# 全局导航守卫
![全易](https://img-blog.csdnimg.cn/20200712235030460.png)


```javascript
/* -------------------------------- 导航守卫 -------------------------------- */
import router from './index';


// 全局前置守卫
router.beforeEach((to, from, next) => {
    if (sessionStorage.getItem("token")) {
        next()
    } else {
        if (to.path !== '/login') {
            alert("未登录，请先登录！")
            next({ path: '/login' })
        } else {
            next()
        }
    }
})

/* // 全局解析守卫
router.beforeResolve((to, from) => {
    console.log(to,from)
})

// 全局后置钩子
router.afterEach((to, from) => {
    console.log(to,from)
}) */
```
**入口文件挂载：**
![全易](https://img-blog.csdnimg.cn/20200713110624371.png)



---


### 局部导航守卫
是写在页面文件，与生命周期同级：
![vue 导航守卫](https://img-blog.csdnimg.cn/20200712235414716.png)


```javascript
<script>
export default {
  data() {
    return {
      calendarTimes: new Date()
    };
  },
  beforeRouteEnter(to, from, next) {
    console.log(to, from);
    next();
    // 在渲染该组件的对应路由被 confirm 前调用
    // 不！能！获取组件实例 `this`
    // 因为当守卫执行前，组件实例还没被创建
  },
  beforeRouteUpdate(to, from, next) {
    console.log(to, from);
    next();
    // 在当前路由改变，但是该组件被复用时调用
    // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
    // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
    // 可以访问组件实例 `this`
  },
  beforeRouteLeave(to, from, next) {
    console.log(to, from);
    next();
    // 导航离开该组件的对应路由时调用
    // 可以访问组件实例 `this`
  },
  created() {}，
  mounted() {}
};
</script>
```


---


### 独享导航守卫
是直接在配置路由文件写：
![独享导航守卫](https://img-blog.csdnimg.cn/20200823172134811.png#pic_center)
![独享导航守卫](https://img-blog.csdnimg.cn/20200823172708182.png#pic_center)
