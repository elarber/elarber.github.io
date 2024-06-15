---
title: js 页面滚动

# index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











> **window.scrollTo();**

**语法1:**   `window.scrollTo(x,y);`
　
    x 是文档中的横轴坐标。
   y 是文档中的纵轴坐标。

例子：
　　window.scrollTo(0,1000); // 垂直滚动到1000的位置


---


**语法2：**  `window.scrollTo({object});`

   `top` 等同于  y
   `left` 等同于  x
   `behavior`  表示滚动行为,传String类型。支持参数 smooth(平滑滚动)、instant(瞬间滚动)、默认值auto,实测效果等同于instant

 例子：
```javascript
window.scrollTo({ 
    top: 1000, 
    behavior: "smooth" 
});
```

 如果某个元素滚动到某个位置，也可以用： `元素.scrollTo();`


