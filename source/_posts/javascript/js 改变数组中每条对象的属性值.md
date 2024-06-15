---
title: js 改变数组中每条对象的属性值

index_img: https://img-blog.csdnimg.cn/20191128094753796.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










![js 改变数组中每条对象的属性值](https://img-blog.csdnimg.cn/2019112809473815.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>js</title>
</head>
<body>
  
  <script>
    var json = [
        {
          day: '2018-12-26 14:31:55'
        },
        {
          day: '2018-12-27 14:31:55'
        },
        {
          day: '2018-12-28 14:31:55'
        },
        {
          day: '2019-12-29 14:31:55'
        }
      ];



    for(let i in json){
      json[i].day=json[i].day.slice(0,10);  // 去掉时间，保留日期
    }
    console.log(json);
  </script>
</body>
</html>
```


效果：
![js 改变数组中每条对象的属性值](https://img-blog.csdnimg.cn/20191128094753796.png)


