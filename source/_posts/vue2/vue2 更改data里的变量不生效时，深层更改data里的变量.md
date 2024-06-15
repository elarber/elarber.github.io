---
title: vue2 更改data里的变量不生效时，深层更改data里的变量

index_img: https://img-blog.csdnimg.cn/20200108173240380.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





如下图，当data里的数据多层嵌套
![vue 更改data里的变量不生效时，深层更改data里的变量](https://img-blog.csdnimg.cn/20200108173240380.png)
语法：

> this.$set(位置,'属性','值');

示例：
```javascript
this.$set(this.schoolBag[0].bagData[2],'value','666');
```
解释：
设置第一个schoolBag数组里 的第三个bagData里 的value为666
