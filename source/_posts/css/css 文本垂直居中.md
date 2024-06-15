---
title: css 文本垂直居中

index_img: https://img-blog.csdnimg.cn/20190821095936133.png
lazyload: true
categories:
- css


tags:
- css

---








**给父元素添加：`vertical-align: middle;`搭配`display: table-cell;`使用，然后相关子元素就垂直居中了：**
![](https://img-blog.csdnimg.cn/20190821095936133.png)
![](https://img-blog.csdnimg.cn/20190821100012507.png)

## 效果：
![](https://img-blog.csdnimg.cn/2019082110004877.png)



---


或者：
给需要垂直居中元素的父元素加：
```css
    display: flex;
    align-items: center;
```

![](https://img-blog.csdnimg.cn/20191016145452901.png)





