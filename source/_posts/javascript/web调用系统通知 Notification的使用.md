---
title: web调用系统通知 Notification的使用

index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- Notification



---









# 案例：
```javascript
<!DOCTYPE html>
<html lang="zh-cn">

<head>
  <meta charset="utf-8">
  <title>Notification</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>

<body>
  <script>
    // 检查用户是否同意接受通知
    if (Notification.permission !== "granted") {
      Notification.requestPermission()
    }

    new Notification("同意了，通知一个");
  </script>
</body>

</html>
```


# 效果：
![](https://img-blog.csdnimg.cn/f2c2ebe859154b7bb8f5e00a33c976e6.gif#pic_center)





