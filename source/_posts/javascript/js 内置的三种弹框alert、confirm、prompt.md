---
title: js 内置的三种弹框：alert、confirm、prompt

index_img: https://img-blog.csdnimg.cn/20201223145832686.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












>confirm()

```javascript
if (confirm("提示文字")) {
 	console.log("点击了确定");
 } else {
   console.log("点击了取消");
 }
```

![](https://img-blog.csdnimg.cn/202012231455144.gif#pic_center)


---

> alert()


```javascript
console.log(alert("提示文字"));

if (alert("提示文字")) {
  console.log("点击了确定");
} else {
  console.log("点击了取消");
}
```

![](https://img-blog.csdnimg.cn/20201223145832686.gif#pic_center)

---

> prompt()

```javascript
let value = prompt("提示文字");
if (value) {
   console.log("点击了确定", "输入了" + value);
 } else {
   console.log("点击了取消");
 }
```

![](https://img-blog.csdnimg.cn/20201223150516177.gif#pic_center)



