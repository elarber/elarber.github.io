---
title: js 改变数组中每条对象的属性名

index_img: https://img-blog.csdnimg.cn/20191203130640174.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---














#### 一、改变一个属性名：
数据量少可以，多了比较耗性能

![js 改变数组中每条对象的属性名](https://img-blog.csdnimg.cn/20191128094229789.png)

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
      
		//将其转为字符串：JSON.parse()，替换day为date： replace()，再转为数据格式：JSON.stringify()
    	console.log(JSON.parse(JSON.stringify(json).replace(/day/g,"date")));
  </script>
</body>
</html>
```

效果：
![js 改变数组中每条对象的属性名](https://img-blog.csdnimg.cn/20191128094309543.png)
其实该方法也可以改变多个属性名：
![js 改变数组中每条对象的属性名](https://img-blog.csdnimg.cn/20191203132520305.png)


---

#### 二、改变多个属性名：

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
          day: '2018-12-26 14:31:55',
          address:'大北京'
        },
        {
          day: '2018-12-27 14:31:55',
          address:'深圳'
        },
        {
          day: '2018-12-28 14:31:55',
          address:'伦敦'
        },
        {
          day: '2019-12-29 14:31:55',
          address:'海南岛'
        }
      ];


      let newJson = [];  // 声明个变量，用于装改变属性名的数据
      for(let i in json){
        newJson.push({
          date:json[i].day，
          ads:json[i].address
        })
      }
      console.log(newJson);
  </script>
</body>
</html>
```
![js 改变数组中每条对象的属性名](https://img-blog.csdnimg.cn/20191203130640174.png)


延申：[对象动态增加属性：https://blog.csdn.net/qq_42618566/article/details/109260169](https://blog.csdn.net/qq_42618566/article/details/109260169)