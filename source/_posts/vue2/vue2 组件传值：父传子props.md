---
title: vue2 组件传值：父传子props

index_img: https://img-blog.csdnimg.cn/20190707010110479.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





组件怎么使用[点这页](https://blog.csdn.net/qq_42618566/article/details/94776310)，本页就直奔主题了啊

#### 一、基本传值：
1.在父组件的标签上定义属性，值就是你要传的数据，如下：
![](https://img-blog.csdnimg.cn/20190707005653362.png)
2.然后在子组件通过props属性接收传来的值，如下：
![](https://img-blog.csdnimg.cn/20190707010110479.png)
父传子的基本传值就完事啦
看效果：
![](https://img-blog.csdnimg.cn/20190707010224495.png)
#### 二、指定类型传值，就是指定传来的值是数字、对象、字符串、、、
首先在父组件上有两步操作，如下图：
![](https://img-blog.csdnimg.cn/20190707011352487.png)
然后在子组件上也有两步操作，如下：
![](https://img-blog.csdnimg.cn/20190707012441391.png)
效果如下：
![](https://img-blog.csdnimg.cn/20190707012612579.png)
指定类型可以是下列原生构造函数中的任意：
 - String 
 - Number 
 - Boolean 
 - Array 
 - Object 
 - Date 
 - Function 
 - Symbol

---


**完整代码：**
--------------父组件的：
html部分：
```html
<ADD :num="nums" :str="strs" :concurrently="con" :obj="obj" />
```
js的data部分：

```javascript
 nums: 9,
 strs: '11111111111111111111111111111111111111111111111111111',
 con: '',
 obj: {
   name:'沙虎',
   age:22
 },
```
--------------子组件的：
html部分：
```html
<p>指定数字类型: {{ num*5 }}</p>
<p>定字符串类型: {{ str }}</p>
<p>支持多种数据类型: {{ concurrently*6 }}</p>
<p>指定对象类型： {{ obj.name }}</p>
```
js的props部分：

```javascript
    num: Number, // 指定数字类型，是可以运算的
    str: String, // 指定字符串类型，不能计算
    // concurrently: [ Number, String ], // 支持多种数据类型：就数组方式指定
    concurrently: { // 指定此传值功能为必选项类型（指定必选就必须按要求的类型传值，否则报错）
      type: [Number, String],
      required:true
    }, 
    obj: {
      type:Object,
      default: function () {
        name:'未知'
      }
    }
```

#### 不知道怎么[子传父？](https://blog.csdn.net/qq_42618566/article/details/94943480)
