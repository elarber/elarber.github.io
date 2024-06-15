---
title: vue2 中的ref和$refs

# index_img: 
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





**定义：**

> **ref：** 
> 用来给元素或子组件注册引用信息， 引用信息将会注册在父组件的 $refs 对象上。
> **如果是在普通的DOM元素上使用，引用指向的就是DOM 元素，如果是在子组件上，引用就指向组件的实例。**

> **$refs：**
> 是一个对象，持有已注册过 ref 的所有的子组件。

**示例：**

 1. 用在普通的DOM标签上：
 [https://blog.csdn.net/qq_42618566/article/details/94765315](https://blog.csdn.net/qq_42618566/article/details/94765315)

 2. 用在子组件的标签上：
[https://blog.csdn.net/qq_42618566/article/details/101055876](https://blog.csdn.net/qq_42618566/article/details/101055876)
