---
title: css 类似优惠券邮票那样的内抠圆角样式，内凹圆角处理

index_img: https://img-blog.csdnimg.cn/20191205152707596.png
lazyload: true
categories:
- css


tags:
- css

---




### 1.优惠券如图这样：
![css 类似优惠券邮票那样的内抠圆角样式，内凹圆角处理](https://img-blog.csdnimg.cn/20191205152707596.png)

实现：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>js</title>
  <style>
    body{
      background-color: red;
    }
    .base-coupons {
    width: 300px;
    height: 500px;
    margin: 20% auto;
    /*    重点代码    */
    background: radial-gradient(circle at left bottom, transparent 20px,  white 0) top left / 50% 70% no-repeat,
		        radial-gradient(circle at left top, transparent 20px,  white 0) bottom left /50% 31% no-repeat,
		        radial-gradient(circle at right bottom, transparent 20px, white 0) top right /50% 70% no-repeat,
		        radial-gradient(circle at right top, transparent 20px, white 0) bottom right /50% 31% no-repeat;
    filter: drop-shadow(0 0 10px black);
    border-radius: 10px;
  }

  </style>
</head>
<body>
  <div class="base-coupons">示例</div>
</body>
</html>
```
解析：
![css 类似优惠券邮票那样的内抠圆角样式，内凹圆角处理](https://img-blog.csdnimg.cn/20191205153614380.png)

![css 类似优惠券邮票那样的内抠圆角样式，内凹圆角处理](https://img-blog.csdnimg.cn/20191205153955882.png)

![css 类似优惠券邮票那样的内抠圆角样式，内凹圆角处理](https://img-blog.csdnimg.cn/20191205154114467.png)


---
### 2.邮票如图：
![css 类似优惠券邮票那样的内抠圆角样式，内凹圆角处理](https://img-blog.csdnimg.cn/20191205155930505.png)
实现：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>js</title>
  <style>
    .base-coupons {
    width: 600px;
    height: 300px;
    margin: 250px auto;
    position: relative;
    background: radial-gradient(circle at right top, transparent 10px,  red 0) top left / 30% 51% no-repeat,
      radial-gradient(circle at right bottom, transparent 10px,  red 0) bottom left /30% 51% no-repeat,
      radial-gradient(circle at left top, transparent 10px, blue 0) top right /70% 51% no-repeat,
      radial-gradient(circle at left bottom, transparent 10px, blue 0) bottom right /70% 51% no-repeat;
    filter: drop-shadow(3px 3px 3px rgba(0,0,0,.3));
  }

  .base-coupons::before {
    content: '';
    height: 270px;
    border: 2px dashed white;
    position: absolute;
    left: 30%;
    top: 0;
    bottom: 0;
    margin: auto -2px;
    }

  .base-coupons::after {
    content: '';
    position: absolute;
    height: 100%;
    width:5px;
    top: 0;
    right: -5px;
    background-image: linear-gradient(to bottom, blue 5px, transparent 5px, transparent),
    radial-gradient(10px circle at 5px 10px, transparent 5px, blue 5px);
    background-size: 5px 15px;
  }


  </style>
</head>
<body>
  <div class="base-coupons">示例</div>
</body>
</html>
```


---
当然，也可以使用 `.png` 格式的图片做背景，使用 [filter属性](https://blog.csdn.net/qq_42618566/article/details/104279168) 沿边投影处理




