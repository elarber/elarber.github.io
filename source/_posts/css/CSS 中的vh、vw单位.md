---
title: CSS 中的vh、vw单位

# index_img: 
lazyload: true
categories:
- css


tags:
- css

---



>   - **vw**：  视窗宽度的百分比（1vw 代表视窗的宽度为 1%）
>   - **vh**：   视窗高度的百分比（ 1vh 代表视窗的高度为 1%）
>   - **vmin**：当前 vw 和 vh 中较小的一个值
>   - **vmax**：当前 vw 和 vh 中较大的一个值

**vw、vh与 % 的区别**：

 1. % 是相对于父元素的大小设定的比率，vw、vh 是视窗大小决定的。
 2.  vw、vh 优势在于能够直接获取高度，而用 % 在没有设置 body高度的情况下，是无法正确获得可视区域的高度的，所以这是挺不错的优势。



