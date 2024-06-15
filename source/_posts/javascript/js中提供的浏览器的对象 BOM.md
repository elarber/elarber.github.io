---
title: js中提供的浏览器的对象 BOM

index_img: https://img-blog.csdnimg.cn/20191115163432200.png
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
    <title>js 对象</title>
</head>
<body>
    <h1>js 对象</h1>
    <script>
    	console.log(window);
        console.log(document);
        console.log(navigator);
        console.log(screen);
        console.log(location);
        console.log(history);
    </script>
</body>
</html>
```
![js中提供的浏览器的对象 BOM](https://img-blog.csdnimg.cn/20200204235253921.png)

---

### window
浏览器的窗口信息
**window对象是顶层对象(核心对象)** 所有 JavaScript 全局对象、函数以及变量均自动成为 window 对象的成员。
例如：

```javascript
    window.document.getElementById("header");
//等同于：
    document.getElementById("header");
```
![js中提供的浏览器的对象 BOM](https://img-blog.csdnimg.cn/20191115133637591.png)

![js中提供的浏览器的对象 BOM](https://img-blog.csdnimg.cn/20191115121030757.png)
例如：

> console.log(window.innerHeight); //获取窗口内部高，去除菜单栏，边框净宽高
> console.log(window.innerWidth); //获取窗口内部宽

---

### 1. document
表示当前的页面的文档
![js中提供的浏览器的对象 BOM](https://img-blog.csdnimg.cn/2020020423515615.png)

例如：

> console.log(document.cookie);  //获取当前页面的cookie信息
> console.log(document.title);  //设置当前页面的标题

---

### 2. navigator
浏览器的所有信息，例如浏览器名称、版本、设置的语言等···
![js中提供的浏览器的对象 BOM](https://img-blog.csdnimg.cn/20191115121051826.png)

例如：

>  console.log(navigator.appVersion);  // 浏览器的版本
>   console.log(navigator.language);  // 浏览器的语言

---


### 3. screen
屏幕的信息
![js中提供的浏览器的对象 BOM](https://img-blog.csdnimg.cn/20191115120957641.png)

例如：
>  console.log(screen.width);  // 显示器屏幕宽度px
>   console.log(screen.colorDepth);  // 颜色位数

---


### 4. location
地址栏中所有的信息
![js中提供的浏览器的对象 BOM](https://img-blog.csdnimg.cn/20191115120932598.png)
例如：
>  console.log(location.href);  // 获取完整url信息
>   console.log(location.pathname);  // 路径

---


### 5. history
保存浏览器的历史记录
![js中提供的浏览器的对象 BOM](https://img-blog.csdnimg.cn/20191115163432200.png)
例如：
>  history.back();  // 
>   history.go();  // 刷新




