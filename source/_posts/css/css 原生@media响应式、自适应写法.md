---
title: css 原生@media响应式、自适应写法

index_img: https://img-blog.csdnimg.cn/20191011162040234.png
lazyload: true
categories:
- css


tags:
- css

---





```css
/* 小于等于 769px */
 @media (max-width: 767px) {
/* 你的样式 */
 }
/* 小屏幕（平板，大于等于 768px） */
@media screen and (min-width: 768px) {
  /* 你的样式 */
}

/* 中等屏幕（桌面显示器，大于等于 992px） */
@media screen and (min-width: 992px) {
  /* 你的样式 */
}

/* 大屏幕（大桌面显示器，大于等于 1200px） */
@media screen and (min-width: 1200px) {
/* 你的样式 */
}

/*  769px到992px之间  */
@media (min-width:768px) and (max-width: 992px){
  /* 你的样式 */
}
```
![](https://img-blog.csdnimg.cn/20191011162040234.png)

![](https://img-blog.csdnimg.cn/2019101116205666.png)

![](https://img-blog.csdnimg.cn/20191011162123336.png)


横屏竖屏：[https://blog.csdn.net/qq_42618566/article/details/105292822](https://blog.csdn.net/qq_42618566/article/details/105292822)
