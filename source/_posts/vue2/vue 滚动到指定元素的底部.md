---
title: vue 滚动到指定元素的底部

index_img: https://img-blog.csdnimg.cn/20200713105517965.gif
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





自定一个滚动指令：`v-scroll`

```javascript
directives: {
    scroll: {
      inserted(el) {
        el.scrollIntoView({
          block: "end",
          behavior: "smooth"
        });
      }
    }
  },
```
![vue 滚动到指定元素的底部](https://img-blog.csdnimg.cn/20200713105328206.png)

![vue 滚动到指定元素的底部](https://img-blog.csdnimg.cn/20200713105517965.gif)
