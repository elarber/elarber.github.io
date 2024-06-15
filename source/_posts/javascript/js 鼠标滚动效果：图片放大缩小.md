---
title: js 鼠标滚动效果：图片放大缩小

index_img: https://img-blog.csdnimg.cn/20191218170534622.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













![js 鼠标滚动效果：图片放大缩小](https://img-blog.csdnimg.cn/20191218171313380.gif)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
      .container{
        width: 40%;
        height: 300px;
        overflow: hidden;
        margin: 100px auto;
      }
    </style>
</head>

<body>
<!--   <div class="box">
    <input type="text" value="1" name="inp">
  </div> -->
  <div class="container">
    <img src="./1.png" alt="">
  </div>




  <script>
      /*const box = document.querySelector(".box");
      const inp = document.querySelector(".inp");*/

     /* box.onmouseover = function (ev) {
        var ev = window.event || ev;
        var tag = ev.target;
        tag.onmousewheel = function (ev) {
          var sc = ev.wheelDelta;
          console.log(ev.wheelDelta);
          sc < 0 ? (sc = -1) : sc = 1;
          console.log(sc)
          var x = parseInt(tag.value);
          tag.value = x + sc;
        }
      }*/


      const container = document.querySelector(".container");
      const img = document.querySelector("img");
      var widthW=100; // 初始化默认宽度
      img.style.width = `${widthW}%`;  // 赋值默认宽度
      container.onmouseover = ()=> {  // 鼠标经过事件
        img.onmousewheel = (b)=> {  // 鼠标滚动事件
          console.log(b); // 打印 b ，可以看到鼠标滚动得很多信息
          b.wheelDelta < 0 ? widthW-- : widthW++;  // 其中 wheelDelta 对象的值就是判断滚轮往前滚还是往后滚：   <0 是往后滚， >0是前滚
          img.style.width = `${widthW}%`;
        }
      }
  </script>
</body>

</html>
```

打印鼠标滚动的信息看看：
![js 鼠标滚动效果：图片放大缩小](https://img-blog.csdnimg.cn/20191218170534622.png)