---
title: css 鼠标跟踪动画

index_img: https://img-blog.csdnimg.cn/20191013103626502.gif
lazyload: true
categories:
- css


tags:
- css

---






![](https://img-blog.csdnimg.cn/20191013103117133.gif)

---

![](https://img-blog.csdnimg.cn/20191013103626502.gif)

**html：**

```html
<button class="mouse-tracking">
    <span>Hover me</span>
  </button>
```

**css：**

```css
.mouse-tracking {
      position: relative;
      background: #7983ff;
      padding: 0.5rem 1rem;
      font-size: 1.2rem;
      border: none;
      color: white;
      cursor: pointer;
      outline: none;
      overflow: hidden;
    }
    .mouse-tracking span {
      position: relative;
    }
    .mouse-tracking::before {
      --size: 0;
      content: '';
      position: absolute;
      left: var(--x);
      top: var(--y);
      width: var(--size);
      height: var(--size);
      background: radial-gradient(circle closest-side, pink, transparent);
      transform: translate(-50%, -50%);
      transition: width 0.2s ease, height 0.2s ease;
    }
    .mouse-tracking:hover::before {
      --size: 90px;
    }
```

**js：**

```javascript
const btn = document.querySelector('.mouse-tracking')
btn.onmousemove = function(e) {
  var x = e.pageX - btn.offsetLeft
  var y = e.pageY - btn.offsetTop
  btn.style.setProperty('--x', x + 'px')
  btn.style.setProperty('--y', y + 'px')
}
```
知识点：主要用到了css变量，js控制css变量


