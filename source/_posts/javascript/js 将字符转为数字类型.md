---
title: js 将字符转为数字类型

index_img: https://img-blog.csdnimg.cn/20191127111253665.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











>    `Number();` 只支持转换纯数字的字符串，有符号或字母就报 NaN。也可以将布尔类型转换，false转为 0，ture转为 1


> `parseInt();` 只转换整数数字，将多余的字符或小数都会舍掉
   `parseFloat();` 可转换整数和小数

      
      


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JS</title>
</head>
<body>

  <script>
    var array = "66677yi";
    var arrays = "99999";
    var arr = "123.66";

    console.log(Number(arr));
    console.log(Number(array));
    console.log(Number(arrays));
    console.log(parseInt(array));
    console.log(parseInt(arr));
    console.log(parseFloat(arr));
    console.log(parseFloat(array));

    /*  总结：
      
      Number(); 只支持转换纯数字的字符串，有符号或字母就报 NaN 
      parse兄弟：parseInt();和parseFloat();
      parseInt(); 只转换整数数字，将多余的字符或小数都会舍掉
      parseFloat(); 可转换小数
    */
  </script>
</body>
</html>
```

![js 将字符转为数字类型](https://img-blog.csdnimg.cn/20191127111253665.png)

---
##### [js 将字符串转换为布尔值boolean](https://blog.csdn.net/qq_42618566/article/details/104389298)


