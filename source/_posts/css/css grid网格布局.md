---
title: css grid网格布局

index_img: https://img-blog.csdnimg.cn/20200201191447450.png
lazyload: true
categories:
- css


tags:
- css

---




> **display: grid;**

**搭配以下属性，实现完美布局：**
- #### ==grid-template-columns== 设置列
![css grid网格布局](https://img-blog.csdnimg.cn/20200201191447450.png)


- #### ==grid-template-rows== 设置行

![css grid网格布局](https://img-blog.csdnimg.cn/20200201191636361.png)


- #### ==column-gap== 设置列间距
![css grid网格布局述](https://img-blog.csdnimg.cn/20200201191822867.png)

- #### ==row-gap== 设置行间距
![css grid网格布局](https://img-blog.csdnimg.cn/2020020119195721.png)

---


**常用属性：** 如同[flex布局](https://blog.csdn.net/qq_42618566/article/details/103971318)的属性一样

- ==justify-content== 水平对齐方式
    **start** 将内容对齐到网格区域(grid area)的左侧
    **end** 将内容对齐到网格区域的右侧
    **center** 将内容对齐到网格区域的中间（水平居中）
    **stretch** 填满网格区域宽度（默认值）
    
- ==align-items== 垂直对齐方式
    **start** 将内容对齐到网格区域(grid area)的顶部
    **end** 将内容对齐到网格区域的底部
    **center** 将内容对齐到网格区域的中间（垂直居中）
    **stretch** 填满网格区域高度（默认值）
    
- ==justify-items== 水平排列方式
    **start** 将网格对齐到 网格容器(grid container) 的左边
    **end** 将网格对齐到 网格容器 的右边
    **center** 将网格对齐到 网格容器 的中间（水平居中）
    **stretch** 调整 网格项(grid items) 的宽度，允许该网格填充满整个 网格容器 的宽度
    **space-around** 在每个网格项之间放置一个均匀的空间，左右两端放置一半的空间
    **space-between** 在每个网格项之间放置一个均匀的空间，左右两端没有空间
    **space-evenly** 在每个栅格项目之间放置一个均匀的空间，左右两端放置一个均匀的空间

- ==align-content== 垂直排列方式
    **start** 将网格对齐到 网格容器(grid container) 的顶部
    **end** 将网格对齐到 网格容器 的底部
    **center** 将网格对齐到 网格容器 的中间（垂直居中）
    **stretch** 调整 网格项(grid items) 的高度，允许该网格填充满整个 网格容器 的高度
    **space-around** 在每个网格项之间放置一个均匀的空间，上下两端放置一半的空间
    **space-between** 在每个网格项之间放置一个均匀的空间，上下两端没有空间
    **space-evenly** 在每个栅格项目之间放置一个均匀的空间，上下两端放置一个均匀的空间

---

`place-items: center;`可以使子元素直接水平居中且垂直居中

![css grid网格布局](https://img-blog.csdnimg.cn/20200212152039586.png)
相当于 `justify-items: center; align-items: center;` 两个的作用
![css grid网格布局](https://img-blog.csdnimg.cn/20200212152304156.png)


##### [案例：数字键盘](https://blog.csdn.net/qq_42618566/article/details/103478771)

