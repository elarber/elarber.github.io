---
title: js原生深拷贝方法：structuredClone() 告别自写时代

index_img: https://img-blog.csdnimg.cn/direct/6eb524ecf5d147409eb9335affd84cf9.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












![](https://img-blog.csdnimg.cn/direct/6eb524ecf5d147409eb9335affd84cf9.png)
> [自2022年3月起，该功能适用于最新的设备和浏览器版本。此功能可能无法在较旧的设备或浏览器中工作。](https://developer.mozilla.org/zh-CN/docs/web/api/structuredClone)


# 例子

```javascript
// Create an object with a value and a circular reference to itself.
const original = { name: "MDN" };
original.itself = original;

// Clone it
const clone = structuredClone(original);

console.assert(clone !== original); // the objects are not the same (not same identity)
console.assert(clone.name === "MDN"); // they do have the same values
console.assert(clone.itself === clone); // and the circular reference is preserved
```



