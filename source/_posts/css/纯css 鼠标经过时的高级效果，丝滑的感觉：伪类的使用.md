---
title: 纯css 鼠标经过时的高级效果，丝滑的感觉：伪类的使用

index_img: https://img-blog.csdnimg.cn/20191109135720425.gif
lazyload: true
categories:
- css


tags:
- css

---




#### 案例1
![纯css 鼠标经过时的高级效果，丝滑的感觉：伪类的使用](https://img-blog.csdnimg.cn/20191109135720425.gif)

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <style>
        body {
            margin: 0;
            padding: 0;
        }

        button{
            width: 200px;
            height: 50px;
            background-color: green;
            border: 0;
            cursor: pointer;
            color: #FFF;
            font-size: 16px;
            position: relative;
        }

        .button::after {
            content: " ";
            width: 0;
            height: 50px;
            position: absolute;
            left: 50%;
            top: 0%;
            background-color: red;
            opacity: 0;
            transition: all .4s;
        }

        .button2::after {
            content: " ";
            width: 0;
            height: 5px;
            position: absolute;
            left: 50%;
            top: 100%;
            background-color: red;
            transition: all .4s;
        }

        .button:hover::after {
            left: 0%;
            width: 100%;
            opacity: 0.6;
        }

        .button2:hover::after {
            left: 0%;
            width: 100%;
        }
    </style>
</head>

<body>
    <button type="button" class="button">Ripple1</button>
    <button type="button" class="button2">Ripple2</button>
</body>

</html>
```

---

#### 案例2
![纯css 鼠标经过时的高级效果，丝滑的感觉：伪类的使用](https://img-blog.csdnimg.cn/20191116230114479.gif)


```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style>
			#wrap {
			    margin: 20px auto;
			    text-align: center;
			}
			 
			#wrap br {
			    display: none;
			}
			 
			.btn-slide, .btn-slide2 {
			    position: relative;
			    display: inline-block;
			    height: 50px;
			    width: 200px;
			    line-height: 50px;
			    padding: 0;
			    border-radius: 50px;
			    background: #fdfdfd;
			    border: 2px solid #0099cc;
			    margin: 10px;
			    transition: .5s;
			}
			 
			.btn-slide2 {
			    border: 2px solid #efa666;
			}
			 
			.btn-slide:hover {
			    background-color: #0099cc;
			}
			 
			.btn-slide2:hover {
			    background-color: #efa666;
			}
			 
			.btn-slide:hover span.circle, .btn-slide2:hover span.circle2 {
			    right: 100%;
			    margin-right: -45px;
			    background-color: #fdfdfd;
			    color: #0099cc;
			}
			 
			.btn-slide2:hover span.circle2 {
			    color: #efa666;
			}
			 
			.btn-slide:hover span.title, .btn-slide2:hover span.title2 {
			    right: 40px;
			    opacity: 0;
			}
			 
			.btn-slide:hover span.title-hover, .btn-slide2:hover span.title-hover2 {
			    opacity: 1;
			    right: 40px;
			}
			 
			.btn-slide span.circle, .btn-slide2 span.circle2 {
			    display: block;
			    background-color: #0099cc;
			    color: #fff;
			    position: absolute;
			    float: right;
			    margin: 5px;
			    line-height: 42px;
			    height: 40px;
			    width: 40px;
			    top: 0;
			    right: 0;
			    transition: .5s;
			    border-radius: 50%;
			}
			 
			.btn-slide2 span.circle2 {
			    background-color: #efa666;
			}
			 
			.btn-slide span.title,
			  .btn-slide span.title-hover, .btn-slide2 span.title2,
			  .btn-slide2 span.title-hover2 {
			    position: absolute;
			    right: 90px;
			    text-align: center;
			    margin: 0 auto;
			    font-size: 16px;
			    font-weight: bold;
			    color: #30abd5;
			    transition: .5s;
			}
			 
			.btn-slide2 span.title2,
			  .btn-slide2 span.title-hover2 {
			    color: #efa666;
			    right: 80px;
			  }
			 
			.btn-slide span.title-hover, .btn-slide2 span.title-hover2 {
			    right: 80px;
			    opacity: 0;
			}
			 
			.btn-slide span.title-hover, .btn-slide2 span.title-hover2 {
			    color: #fff;
			}
		</style>
	</head>
	<body>
		<div id="wrap">
			<a href="#" class="btn-slide">
			  <span class="circle"><i class="fa fa-rocket"></i></span>
			  <span class="title">火箭</span>
			  <span class="title-hover">带你飞</span>
			</a>
			<a href="#" class="btn-slide2">
			  <span class="circle2"><i class="fa fa-download"></i></span>
			  <span class="title2">登陆</span> 
			  <span class="title-hover2">点击登陆</span>
			</a>
		</div>
	</body>
</html>
```

---

#### 案例3
![纯css 鼠标经过时的高级效果，丝滑的感觉：伪类的使用](https://img-blog.csdnimg.cn/20191121110610125.gif)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style>
			 .underline {
			    display: inline-block;
			    position: relative;
			    color: #0087ca;
			    padding: 10px 0;
			  }
			  .underline::after {
			    content: '';
			    position: absolute;
			    width: 100%;
			    transform: scaleX(0);
			    height: 2px;
			    bottom: 0;
			    left: 0;
			    background-color: #0087ca;
			    transform-origin: bottom right;
			    transition: transform 0.25s ease-out;
			  }
			  .underline:hover::after {
			    transform: scaleX(1);
			    transform-origin: bottom left;
			  }
		</style>
	</head>
	<body>
		<p class="underline">鼠标经过该元素</p>
	</body>
</html>
```


---
#### 案例4
![纯css 鼠标经过时的高级效果，丝滑的感觉：伪类的使用](https://img-blog.csdnimg.cn/20191218155646957.gif)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <style>
    .box{
      position: relative;
      margin: 50px auto;
      width: 50%;
      height: 400px;
      overflow: hidden;
    }
    .box:after{
      position: absolute;
      left: -100%;
      top: 0;
      content: "";     
      width: 30%;
      height: 100%;
      /* Safari 5.1 - 6.0 */
      background: -webkit-linear-gradient(left,rgba(255,255,255,0) 0,rgba(255,255,255,.3) 50%,rgba(255,255,255,0) 100%);
      /* Opera 11.1 - 12.0 */
      background: -o-linear-gradient(left,rgba(255,255,255,0) 0,rgba(255,255,255,.3) 50%,rgba(255,255,255,0) 100%);
      /* Firefox 3.6 - 15 */
      background: -moz-linear-gradient(left,rgba(255,255,255,0) 0,rgba(255,255,255,.3) 50%,rgba(255,255,255,0) 100%);
      /* 标准的语法 */
      background: linear-gradient(to right,rgba(255,255,255,0) 0,rgba(255,255,255,.3) 50%,rgba(255,255,255,0) 100%);
      transform: skewX(-45deg);
      transition: 1s ease;
      }
      .box:hover:after{
        left: 150%;
        transition: 1s ease;
      }
  </style>
</head>
<body>
    <div class="box">
    <img src="2.png" alt="">
  </div>
</body>
</html>
```


#### 拓展
[https://juejin.im/post/6861501624993447950](https://juejin.im/post/6861501624993447950)


