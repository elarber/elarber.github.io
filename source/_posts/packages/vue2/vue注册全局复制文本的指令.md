---
title: vue注册全局复制文本的指令

index_img: https://img-blog.csdnimg.cn/7abac119d329411abfc0e18a590c4ee8.gif
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue
- vue2


---











![](https://img-blog.csdnimg.cn/7abac119d329411abfc0e18a590c4ee8.gif#pic_center)



![](https://img-blog.csdnimg.cn/6bb6e69a88f443cdae37f64fcdd9f859.png)


```javascript
  // 复制文本
  copy(el) {
    el.onclick = function () {
      if (!el.innerText) return;

      let textarea = document.createElement("textarea");
      textarea.readOnly = 'readonly';
      textarea.value = el.innerText;
      el.appendChild(textarea);
      textarea.select();
      const result = document.execCommand("Copy");
      if (result) {
        ELEMENT.Message.success('已复制');
      } else {
        ELEMENT.Message.info('复制失败');
      }
      el.removeChild(textarea);
    }
  }
```


使用：` <div v-copy>1111111111111</div> `



>  [全局指令](https://blog.csdn.net/qq_42618566/article/details/107785500)

