---
title: css 改变滚动条的默认样式

index_img: https://img-blog.csdnimg.cn/20191010163133801.png
lazyload: true
categories:
- css


tags:
- css

---



#### 比如改变body的默认滚动条样式：

```css
/*滚动条整体样式*/
body::-webkit-scrollbar {
  width: 10px;
  /*高宽分别对应横竖滚动条的尺寸*/
  height: 1px;
}

/*滚动条里面的滚动的块样式*/
body::-webkit-scrollbar-thumb {
  border-radius: 10px;
  background-color: skyblue;
  background-image: -webkit-linear-gradient(45deg,
      rgba(255, 255, 255, 0.2) 25%,
      transparent 25%,
      transparent 50%,
      rgba(255, 255, 255, 0.2) 50%,
      rgba(255, 255, 255, 0.2) 75%,
      transparent 75%,
      transparent);
}

/*滚动条里面轨道*/
body::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.2);
  background: #ededed;
  border-radius: 10px;
}
```
效果：
![](https://img-blog.csdnimg.cn/20191010163133801.png)


