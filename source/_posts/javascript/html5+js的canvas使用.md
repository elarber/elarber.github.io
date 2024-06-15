---
title: html5+js的canvas使用

index_img: https://img-blog.csdnimg.cn/20191116150516414.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>canvas</title>
</head>

<body>
    <canvas id="canvas" width="300" height="200"></canvas>
    <script>
        var ctx = document.querySelector("#canvas").getContext("2d"); //获取画布、设置画笔

        // 画太极图
        // 1.绘制整个的圆
        ctx.beginPath()
        ctx.arc(100, 100, 60, 0, Math.PI * 2, true)
        ctx.stroke()
        ctx.closePath()
        // 2.绘制下半圆
        ctx.beginPath()
        ctx.arc(100, 100, 60, 0, Math.PI, false)
        ctx.closePath()
        ctx.fillStyle = '#000'
        ctx.fill()
        // 3.绘制上半圆右侧
        ctx.beginPath()
        ctx.arc(130, 100, 30, 0, Math.PI, true)
        ctx.closePath()
        ctx.fill()
        // 4.绘制小圆点
        ctx.beginPath()
        ctx.arc(130, 100, 5, 0, Math.PI * 2, true)
        ctx.closePath()
        ctx.fillStyle = '#fff'
        ctx.fill()
        // 5.绘制下半圆左侧
        ctx.beginPath()
        ctx.arc(70, 100, 30, 0, Math.PI, false)
        ctx.closePath()
        ctx.fill()
        // 6.绘制小圆点
        ctx.beginPath()
        ctx.arc(70, 100, 5, 0, Math.PI * 2, true)
        ctx.closePath()
        ctx.fillStyle = '#000'
        ctx.fill()


        /* ctx.font = '40px 微软雅黑'
        ctx.fillText('Hello world', 10, 40)
        ctx.strokeText('Hello world', 10, 80) */


        /* // 二次贝塞尔曲线
        ctx.beginPath();
        ctx.moveTo(75,25);
        ctx.quadraticCurveTo(25,25,25,62.5);
        ctx.quadraticCurveTo(25,100,50,100);
        ctx.quadraticCurveTo(50,120,30,125);
        ctx.quadraticCurveTo(60,120,65,100);
        ctx.quadraticCurveTo(125,100,125,62.5);
        ctx.quadraticCurveTo(125,25,75,25);
        ctx.stroke(); */


        /* //三次贝塞尔曲线
        ctx.beginPath();
        ctx.moveTo(75,40);
        ctx.bezierCurveTo(75,37,70,25,50,25);
        ctx.bezierCurveTo(20,25,20,62.5,20,62.5);
        ctx.bezierCurveTo(20,80,40,102,75,120);
        ctx.bezierCurveTo(110,102,130,80,130,62.5);
        ctx.bezierCurveTo(130,62.5,130,25,100,25);
        ctx.bezierCurveTo(85,25,75,37,75,40);
        ctx.fill(); */


        // 三角形
        /* pen.beginPath();
        pen.moveTo(20, 20);
        pen.lineTo(30, 30);
        pen.lineTo(20, 40);
        pen.lineTo(20, 20);
        pen.closePath();//不使用closePath结束绘制，左上角的会有缺口，用closePath的时候可以不用进行结尾，即最后一笔可以不画
        pen.lineWidth = '2'; //线条粗细
        pen.strokeStyle = 'red';//线条颜色
        pen.fillStyle = "yellow";//内容填充色
        pen.stroke();//描边结束
        pen.fill(); //绘制结束 */
    </script>
</body>

</html>
```
![htm5、js的canvas使用](https://img-blog.csdnimg.cn/20191116150516414.png)

