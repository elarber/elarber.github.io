---
title: js 正则匹配，从字符串中提取数字

index_img: https://img-blog.csdnimg.cn/20200727142725316.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










#### 效果：
![js 正则匹配，从字符串中提取数字](https://img-blog.csdnimg.cn/20200727142725316.png)


#### 正则：

> `/[^\d.]/g`


#### 代码：
```javascript
let string = "谷(2588.7元/kwh)";
let num = string.replace(/[^\d.]/g, "");
console.log(num);
```






