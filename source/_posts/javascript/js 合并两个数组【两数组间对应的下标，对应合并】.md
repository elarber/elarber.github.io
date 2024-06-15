---
title: js 合并两个数组【两数组间对应的下标，对应合并】

index_img: https://img-blog.csdnimg.cn/20190922105359478.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










**如下图两块，对应合并：**
![](https://img-blog.csdnimg.cn/20190922105359478.png)
**将这两个数组合并成：**  日期在前，星期在后，中间用空格隔开
![](https://img-blog.csdnimg.cn/20190922105448643.png)
代码如下：
```
	for(let l in dateData){
      mergeWeekDate.push(dateData[l].substring(5, dateData[l].length) +' '+ weekData[l]);  //  意思就是mergeWeekDate装入dateData[l]和空格和weekData[l]。  substring（）是去掉前5位
    }
```
![](https://img-blog.csdnimg.cn/20190922105943367.png)


