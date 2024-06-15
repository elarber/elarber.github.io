---
title: css 钟表

index_img: https://img-blog.csdnimg.cn/20200503205604976.gif
lazyload: true
categories:
- css


tags:
- css

---








![css 钟表](https://img-blog.csdnimg.cn/20200503205604976.gif)


```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>纯css钟表</title>
  <style>
    body {
      background-color: bisque;
    }

    .clock {
      width: 300px;
      height: 300px;
      background-color: #b9e7ff;
      margin: 200px auto;
      border: 25px solid #ffffff;
      box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.45) inset;
      border-radius: 50%;
      filter: drop-shadow(0 0 10px rgba(0, 0, 0, 0.45));
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
    }

    .num {
      position: absolute;
      color: #0044a9;
      font-weight: bold;
    }

    .num:nth-child(1) {
      top: 27px;
      right: 71px;
    }

    .num:nth-child(2) {
      top: 77px;
      right: 20px;
    }

    .num:nth-child(3) {
      top: 140px;
      right: 5px;
    }

    .num:nth-child(4) {
      bottom: 66px;
      right: 29px;
    }

    .num:nth-child(5) {
      bottom: 19px;
      right: 80px;
    }

    .num:nth-child(6) {
      bottom: 5px;
      left: 143px;
    }

    .num:nth-child(7) {
      bottom: 19px;
      left: 80px;
    }

    .num:nth-child(8) {
      bottom: 66px;
      left: 29px;
    }

    .num:nth-child(9) {
      top: 140px;
      left: 5px;
    }

    .num:nth-child(10) {
      top: 77px;
      left: 20px;
    }

    .num:nth-child(11) {
      top: 27px;
      left: 71px;
    }

    .num:nth-child(12) {
      top: 5px;
      left: 140px;
    }

    .point {
      width: 20px;
      height: 20px;
      background-color: black;
      box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.45);
      border-radius: 50%;
    }

    /*----------- 表针 -----------*/
    .hour,
    .minute,
    .second {
      height: 5px;
      background-color: black;
      border-top-right-radius: 100%;
      border-bottom-right-radius: 100%;
      position: absolute;
      top: 7px;
      left: 11px;
      transform-origin: left;
    }

    .hour {
      width: 70px;
      transform: rotateZ(10deg);
      animation: hour 86400s infinite;
    }

    .minute {
      width: 100px;
      transform: rotateZ(40deg);
      animation: minute 3600s infinite;
    }

    .second {
      width: 120px;
      transform: rotateZ(100deg);
      animation: second 60s infinite;
    }

    /*----------- 动画 -----------*/
    @keyframes hour {
      from {
        transform: rotateZ(0deg);
      }

      to {
        transform: rotateZ(360deg);
      }
    }

    @keyframes minute {
      from {
        transform: rotateZ(0deg);
      }

      to {
        transform: rotateZ(360deg);
      }
    }

    @keyframes second {
      from {
        transform: rotateZ(0deg);
      }

      to {
        transform: rotateZ(360deg);
      }
    }

  </style>
</head>

<body>
  <div class="clock">
    <span class="num">1</span>
    <span class="num">2</span>
    <span class="num">3</span>
    <span class="num">4</span>
    <span class="num">5</span>
    <span class="num">6</span>
    <span class="num">7</span>
    <span class="num">8</span>
    <span class="num">9</span>
    <span class="num">10</span>
    <span class="num">11</span>
    <span class="num">12</span>
    <div style="position: relative;">
      <div class="point"></div>
      <div class="hour"></div>
      <div class="minute"></div>
      <div class="second"></div>
    </div>
  </div>
</body>

</html>
```




