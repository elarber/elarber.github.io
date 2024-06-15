---
title: web Worker前端多线程任务执行

index_img: https://img-blog.csdnimg.cn/717604368d8a4edd8996fa2b9ef34fcc.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- web Worker



---











[https://developer.mozilla.org/zh-CN/docs/Web/API/Worker](https://developer.mozilla.org/zh-CN/docs/Web/API/Worker)

> 就是单独去执行一个任务，不影响主线程的任何操作


# 实现过程
## 目录结构
![](https://img-blog.csdnimg.cn/f7b7faccc3fa4c65b261e2f2875025a2.png)

## 主线程

```html
<!DOCTYPE html>
<html lang="zh-cn">

<head>
  <meta charset="utf-8">
  <title>worker</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>

<body>

  <p>工作： <output id="result"></output></p>
  <button onclick="startWorker()">开始工作</button>
  <button onclick="stopWorker()">停止工作</button>
  <hr />
  <input type="text">
  <script>
    var W;

    function startWorker() {
      W = new Worker("./worker.js");
      console.log(W);
      W.onmessage = function (event) {
        console.log(event);
        document.getElementById("result").innerHTML = event.data;
      };
    }



    function stopWorker() {
      W.terminate();
      W = undefined;
    }
  </script>
</body>

</html>
```

## 子线程
worker.js
```javascript
var i = 0;
setInterval(() => {
  i = i + 1;
  postMessage(i);
}, 1000);
```

# 效果展示

![](https://img-blog.csdnimg.cn/717604368d8a4edd8996fa2b9ef34fcc.gif#pic_center)


