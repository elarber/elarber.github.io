---
title: js 批量覆盖元素的原样式

index_img: https://img-blog.csdnimg.cn/20200201182745915.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---









> **div.style.cssText = "color:white; background-color:green;";**

![js 批量覆盖元素的原样式](https://img-blog.csdnimg.cn/2020020118333562.png)


![js 批量覆盖元素的原样式](https://img-blog.csdnimg.cn/20200201183258932.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>测试</title>
</head>
<style>
  .test-1 {
    background-color: red;
    color: green;
    padding: 50px;
  }

</style>

<body>
  <div class="test-1">
    啦啦啦啦啦啦啦啦啦
  </div>


  <script>
    const div = document.querySelector('.test-1');
    div.style.cssText = `
      color:white;
      background-color:green;
      padding:100px;
      box-shadow:0 0 80px #333;
    `;
  </script>
</body>

</html>

```
![js 批量覆盖元素的原样式](https://img-blog.csdnimg.cn/20200201182745915.png)



