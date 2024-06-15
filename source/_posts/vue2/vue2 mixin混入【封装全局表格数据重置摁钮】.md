---
title: vue2 mixin混入【封装全局表格数据重置摁钮】

index_img: https://img-blog.csdnimg.cn/f2c7497508c44ba0b23497099eb83f37.gif
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





# 需求说明
![](https://img-blog.csdnimg.cn/039387d4dd3144babe0aa4824efbabe0.png)

基本上每个页面都有筛选数据的功能
![](https://img-blog.csdnimg.cn/f2c7497508c44ba0b23497099eb83f37.gif#pic_center)
那么每个页面都写一遍重置按钮的方法吗？那就太臃肿了
此处有更优方案，使用[`mxin`](https://cn.vuejs.org/v2/guide/mixins.html)：
![](https://img-blog.csdnimg.cn/af07b4f7b7e24f8aaa8f1c750008cbf4.png)

# 功能封装

```javascript
export default {
  methods: {
    resetFilter(form, method = "getData", fn) {
      if (!this[form]) {
        form = "queryForm";
      }

      for (let item in this[form]) {
        this[form][item] = "";
        if (item === "pageNum") {
          this[form]["pageNum"] = 1;
        }
        if (item === "pageSize") {
          this[form]["pageSize"] = 20;
        }
      }
      this[method]();
      if (fn && typeof fn === "function") {
        fn()
      }
    },
  }
}
```

# 使用
在需要的页面导入即可
![](https://img-blog.csdnimg.cn/cf121de8c1114cf2b12d7cd61ba4e56b.png)



注意：
![](https://img-blog.csdnimg.cn/38ac59904cdd4f0da07ec4441e93f070.png)


# 效果
![](https://img-blog.csdnimg.cn/8137411568c244979fc678615f8b9d1d.gif#pic_center)
