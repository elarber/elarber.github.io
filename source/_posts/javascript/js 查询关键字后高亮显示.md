---
title: js 查询关键字后高亮显示

index_img: https://img-blog.csdnimg.cn/20200202031149935.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










## 效果
![](https://img-blog.csdnimg.cn/20200202031149935.gif)


## 源码

```html
<!DOCTYPE html>
<html lang="en">

<head>
 <meta charset="UTF-8">
 <title>测试</title>
</head>

<body>
 <input type="text">
 <button style="margin-right: 80px">查询</button>
 <span style="display: none; color: blue">查出<em></em>条</span>
 <div class="text" style="margin-top: 70px">ECMAScript v3 规定，replace() 方法的参数 replacement 可以是函数而不是字符串。在这种情况下，每个匹配都调用该函数，它返回的字符串将作为替换文本使用。该函数的第一个参数是匹配模式的字符串。接下来的参数是与模式中的子表达式匹配的字符串，可以有 0 个或多个这样的参数。接下来的参数是一个整数，声明了匹配在 stringObject 中出现的位置。最后一个参数是 stringObject 本身。stringObject 的 replace() 方法执行的是查找并替换的操作。它将在 stringObject 中查找与 regexp 相匹配的子字符串，然后用 replacement 来替换这些子串。如果 regexp 具有全局标志 g，那么 replace() 方法将替换所有匹配的子串。否则，它只替换第一个匹配子串。replacement 可以是字符串，也可以是函数。如果它是字符串，那么每个匹配都将由字符串替换。但是 replacement 中的 $ 字符具有特定的含义。如下表所示，它说明从模式匹配得到的字符串将用于替换。</div>

 <script>
  var text = document.querySelector(".text");
  var inp = document.querySelector("input");
  const btn = document.querySelector("button");
  btn.onclick = () => {
   if (text.innerText.indexOf(inp.value) != -1) {
    text.innerHTML = text.innerText.replace(new RegExp(inp.value, 'g'), `<b style='background-color:red; color:white;'>${inp.value}</b>`); // 通过正则全局匹配关键字，查出来的文字进行高亮替换
    // 查出来的数量
    document.querySelector("span").style.display = "unset";
    document.querySelector("em").innerText = document.querySelectorAll("b").length;
   } else {
    // 清除上次的查询记录
    let Btags = document.querySelectorAll("b");
    for(let i=0; i<Btags.length; i++){
     Btags[i].style.cssText = "background-color:transparent; color: unset; font-weight: unset;";
    }
    document.querySelector("em").innerText = 0;  // 查出来的数量归零
    alert(`无${inp.value}查询字段`);
   }
  };
 </script>
</body>

</html>
```





