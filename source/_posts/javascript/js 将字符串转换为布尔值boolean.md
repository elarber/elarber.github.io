---
title: js 将字符串转换为布尔值boolean

# index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---









> `Boolean();` 参数为 0、null 和无参数返回false，有参数返回true。

```javascript
Boolean("");  //输出为：false
Boolean(null);  //输出为：false
Boolean(0);  //输出为：false 
Boolean("hi");  //输出为：true
Boolean(100);  //输出为：true
Boolean(new  Object());  //输出为：true
```




