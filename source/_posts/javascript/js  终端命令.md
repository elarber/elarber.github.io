---
title: js  终端命令

index_img: https://img-blog.csdnimg.cn/20200205202039973.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












```javascript
document.execCommand("命令名");
```
例如：
![](https://img-blog.csdnimg.cn/20200205201910493.png)


案例：点击复制文本

```html
<!DOCTYPE html>
<html lang="en">

<head>
 <meta charset="UTF-8">
 <title>测试</title>
</head>

<body>
 <div id="contents" onClick="copit()">66666666666666</div>

 <script type="text/javascript">
  function copit() {
   var contents = document.querySelector("#contents").innerText;
   let storage = document.createElement('input');
   storage.value = contents;
   document.body.appendChild(storage);
   storage.select(); // 选择对象
   document.execCommand("Copy"); // 执行浏览器复制命令
   storage.className = 'storage';
   storage.style.display = 'none';
   alert('复制成功');
  }

 </script>

</body>

</html>
```

![js  命令](https://img-blog.csdnimg.cn/20200205202039973.gif)
