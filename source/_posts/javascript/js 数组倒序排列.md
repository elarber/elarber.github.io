---
title: js 数组倒序排列

index_img: https://img-blog.csdnimg.cn/20191121171256183.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













#### 1.使用reverse()函数：
```javascript
	var array=['我','喜','欢','你'];

    array.reverse();  // 输出： ["你", "欢", "喜", "我"]
```

#### 2.循环遍历一一使其倒序：

```javascript
    var array=['我','喜','欢','你'];
    var temp;
    for(let i=0; i<array.length/2; i++){
      temp=array[i];
      array[i]=array[array.length-1-i];
      array[array.length-1-i]=temp;
    }
    console.log(array);  // 输出： ["你", "欢", "喜", "我"]
```

![js 数组倒序排列](https://img-blog.csdnimg.cn/20191121171256183.png)


延申：
字符串倒序排列：

```javascript
var string="Hello World"
    var reverse=string.split("").reverse().join(""); //split()将字符串按特定的方式分割重组为一个数组   reverse()用于颠倒数组中元素的顺序join()   将数组按特定的方式重组为一个字符串
    console.log(reverse);     // 输出：dlroW olleH
```

![js 数组倒序排列](https://img-blog.csdnimg.cn/20200127223422642.png)
