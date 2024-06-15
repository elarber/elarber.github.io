---
title: js 数组中的字符转为数字

index_img: https://img-blog.csdnimg.cn/20190921161122889.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











本来是这样的：

> ["3", "17", "56", "21", "8", "33", "177"]

转化后：
> [3, 17, 56, 21, 8, 33, 177]


---

**方法：**（选其一中）

>  `数组.map(Number)`
       
>JSON.parse('[' + String(数组) + ']')

>eval('[' + String(数组) + ']')


      数组.map((i)=>{
        return parseInt(i)
      })
             

示例：(第一种)
![](https://img-blog.csdnimg.cn/20190921161122889.png)
那么输出结果：

![](https://img-blog.csdnimg.cn/20190921161231826.png)

