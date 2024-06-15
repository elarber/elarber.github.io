---
title: js 禁止页面打开查看源码

index_img: https://img-blog.csdnimg.cn/20191019211111599.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












能够查看页面源码的无非就是右击的`保存`、`检查`、`查看页面源代码`和`相应的快捷键`（Ctrl+S、Ctrl+Shift+I 、Shift+F10和Ctrl+U）`F12`
![](https://img-blog.csdnimg.cn/20191019211111599.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
 <meta charset="UTF-8">
 <title>屏蔽F12、Ctrl+U、Ctrl+Shift+I、右击</title>
</head>

<body>
 <div>
  测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试
 </div>



 <script type="text/javascript">
  window.onload = function() {
   //屏蔽键盘事件
   document.onkeydown = (e)=> {
    console.log(e);
    if (e.keyCode == 123) { // 屏蔽F12
     return false;
    } else if ((e.ctrlKey) && (e.shiftKey) && (e.keyCode == 73)) { // 屏蔽Ctrl+Shift+I
     return false;
    } else if ((e.shiftKey) && (e.keyCode == 121)) { // 屏蔽Shift+F10
     return false;
    } else if ((e.ctrlKey) && (e.keyCode == 85)) { // 屏蔽Ctrl+U
     return false;
    } else if ((e.ctrlKey) && (e.keyCode == 83)) { // 屏蔽Ctrl+S
     return false;
    }
   };
   //屏蔽鼠标右击
   document.oncontextmenu = ()=> {
    return false;
   }
  }

 </script>
</body>

</html>
```

