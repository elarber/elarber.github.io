---
title: js的三种for循环：(for)、(for in)、(for of)

index_img: https://img-blog.csdnimg.cn/20200212111432905.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











#### for 循环
通用循环
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
</head>
<body>
<p>点击按钮循环代码块 5 次。</p>
<button onclick="myFunction()">点我</button>
<p id="demo"></p>

<script>
<!DOCTYPE html>
<html>

<head>
 <meta charset="utf-8">
</head>

<body>
 <p>点击按钮循环代码块 5 次。</p>
 <button onclick="test()">点我</button>
 <p id="demo"></p>

 <script>
  var text = "";
  
  function test() {
   for (let i = 0; i < 5; i++) {
    text += `The number is ${i}<br>`;
   }
   /* // 使用 continue 语句，在i等于3时跳过当前循环
    for (i = 0; i < 5; i++) {
        if (i == 3) {
            continue;
        }
        text += `The number is ${i}<br>`;
    }
    */
   /* // 使用 break 语句 在i等于3时跳出当前循环
    for (i = 0; i < 5; i++) {
       if (i == 3) {
           break;
       }
       text += `The number is ${i}<br>`;
   }
   */
  document.getElementById("demo").innerHTML = text;
  }

 </script>

</body>

</html>
```
结果：
![js的三种for循环：(for)、(for in)、(for of)](https://img-blog.csdnimg.cn/20200212111432905.gif)

#### for in 循环
用于循环对象

```html
<!DOCTYPE html>
<html>

<head>
 <meta charset="utf-8">
</head>

<body>
 <p>点击按钮循环对象属性。</p>
 <button onclick="test()">点我</button>
 <p id="demo"></p>

 <script>
  var person = {
    name: "quanyi",
    position: "frontend devloper",
    age: 25
   };
  
  var text = "";
  function test() {
   for (let x in person) {
    text += person[x] + " <br>";
    console.log(x);
   }
   document.getElementById("demo").innerHTML = text;
  }

 </script>

</body>

</html>
```

![js的三种for循环：(for)、(for in)、(for of)](https://img-blog.csdnimg.cn/20200212110820179.gif)

#### for of 循环
遍历字符串
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
</head>
<body>
	<script>
		var string="why give up treatment";
		 for(let i of string){
		 	console.log(i);
		 }
	</script> 
</body>
</html>
```
![js的三种for循环：(for)、(for in)、(for of)](https://img-blog.csdnimg.cn/20200311192535560.png)

