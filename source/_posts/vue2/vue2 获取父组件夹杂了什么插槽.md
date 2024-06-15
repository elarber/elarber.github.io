---
title: vue2 获取父组件夹杂了什么插槽

index_img: https://img-blog.csdnimg.cn/4b80d86b7dd3421fa2c94f523aab7a89.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





在子组件打印一下：

```javascript
mounted(){
    console.log(this.$scopedSlots);
 },
```
![](https://img-blog.csdnimg.cn/4b80d86b7dd3421fa2c94f523aab7a89.png)
说明用到了两个插槽：`left`和`columns`
