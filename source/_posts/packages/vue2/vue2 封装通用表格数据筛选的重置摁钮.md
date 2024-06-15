---
title: vue2 封装通用表格数据筛选的重置摁钮

index_img: https://img-blog.csdnimg.cn/2e39e289dc714e689ac93606538673d2.png
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2



---











![](https://img-blog.csdnimg.cn/d0b53af8fd924eed84b9b9e12caebcd0.png)


放弃冗余代码吧，封装个[混入](https://cn.vuejs.org/v2/guide/mixins.html)


# 封装逻辑

```javascript
// 重置表格筛选参数
export const queryReset = {
  methods: {
    queryReset(form, method = "getData", fn) {
      if (!this[form]) {
        form = "queryForm";
      }

      this.$data[form] = this.$options.data()[form];

      this[form]["pageNum"] = 1;
      this[form]["pageSize"] = this.$tableDataSize;
      
      this[method]();
      if (fn && typeof fn === "function") {
        fn()
      }
    },
  }
}
```


# 在页面处引入
![](https://img-blog.csdnimg.cn/2e39e289dc714e689ac93606538673d2.png)

就图中3步，无需再定义【重置】摁扭的事件


# 说明

> queryReset() 有三个参数：`form`, `method`, `fn`
> - form是你重置的参数大对象 [默认叫queryForm]
> - 重置完参数调用接口查询列表数据的方法 [默认叫getData()]
> - 还要执行的方法（备用）

我有一个习惯，就是每个页面的表格查询方法都叫getData()，所以这个默认getData()了。每个页面表格的查询条件都放在queryForm大对象里了，所以这个默认queryForm。每个表格的查询都有分页的参数pageNum、pageSize



![](https://img-blog.csdnimg.cn/31953b19afc2415c995bb7ae99b26adb.png)



