---
title: js 使浏览器进入全屏，F11效果

index_img: https://img-blog.csdnimg.cn/20191020122459187.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













![](https://img-blog.csdnimg.cn/20191020122459187.gif)


```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>js进入全屏</title>
</head>

<body>
    <button id='btn'>进入全屏</button>
    <div id="content" style="background:yellow;width:500px;height:500px;">
        <div>测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容测试内容</div>
        <a href="#" id="quite" class="btn">退出全屏</a>
    </div>


    <script>
        // 定义进入全屏
        function fullScreen(el) {
            var rfs = el.requestFullScreen || el.webkitRequestFullScreen || el.mozRequestFullScreen || el.msRequestFullScreen,
                wscript
            if (typeof rfs != "undefined" && rfs) {
                rfs.call(el);
                return;
            }
            if (typeof window.ActiveXObject != "undefined") {
                wscript = new ActiveXObject("WScript.Shell");
                if (wscript) {
                    wscript.SendKeys("{F11}");
                }
            }
        }
        // 定义退出全屏
        function exitFullScreen(el) {
            var el = document,
                cfs = el.cancelFullScreen || el.webkitCancelFullScreen || el.mozCancelFullScreen || el.exitFullScreen, wscript;
            if (typeof cfs != "undefined" && cfs) {
                cfs.call(el);
                return;
            }
            if (typeof window.ActiveXObject != "undefined") {
                wscript = new ActiveXObject("WScript.Shell");
                if (wscript != null) {
                    wscript.SendKeys("{F11}");
                }
            }
        }
        // 调用全屏功能
        var btn = document.getElementById('btn');
        var content = document.getElementById('content');
        btn.onclick = function () {
            fullScreen(content);
        }
        var quite = document.getElementById('quite');
        quite.onclick = function () {
            exitFullScreen();
        }
    </script>
</body>

</html>
```

