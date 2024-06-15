---
title: js 让div元素倒序排列

index_img: https://img-blog.csdnimg.cn/20191121185508633.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
  </head>
  <body>
    <ul class="container">
      <li>我</li>
      <li>喜</li>
      <li>欢</li>
      <li>你</li>
    </ul>
    <script>
      const lis= document.querySelectorAll(".container>li");
      for(let i=lis.length-1; i>-1; i--){
        document.querySelector(".container").appendChild(lis[i]);
      }
      //循环条件  i=lis.length-1; i>-1; i--   不能乱
    </script>
  </body>
</html>
```

【我喜欢你】倒过来：
![js 让div元素倒序排列](https://img-blog.csdnimg.cn/20191121185508633.png)


