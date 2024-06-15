---
title: css 元素溢出部分内框显示渐变

index_img: https://img-blog.csdnimg.cn/20191013105001225.gif
lazyload: true
categories:
- css


tags:
- css

---





![](https://img-blog.csdnimg.cn/20191013105001225.gif)

**html：**

```html
<div class="overflow">
    <div class="text-scroll">
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolled
      Content to be scrolledv
    </div>
  </div>
```

**css：**

```css
.overflow {
      position: relative;
    }
    .overflow::after {
      content: '';
      position: absolute;
      bottom: 0;
      width: 240px;
      height: 25px;
      background: linear-gradient(rgba(255, 255, 255, 0.001),blue); /* 溢出部分那显示渐变 */
      pointer-events: none;
    }
    .text-scroll {
      overflow-y: scroll;
      background: #fcefef;
      width: 240px;
      height: 200px;
      padding: 15px 0;
      line-height: 1.2;
      text-align: center;
    }
```

