---
title: vue2 获取父组件挂载了什么事件

index_img: https://img-blog.csdnimg.cn/9e5316a90d154bd5a46366ddd7ba1d4a.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





```javascript
mounted(){
  console.log(this.$listeners);
}
```

父组件
![](https://img-blog.csdnimg.cn/9e5316a90d154bd5a46366ddd7ba1d4a.png)

子组件打印看看：
![](https://img-blog.csdnimg.cn/7c2cbe1a8b024a6a9b782cbd62bfd48e.png)


![](https://img-blog.csdnimg.cn/a320da4b4cb14ba59643bce68dae0b24.png)
