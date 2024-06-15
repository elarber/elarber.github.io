---
title: js中对数组.map()、some()、every()、find()、filter()、reduce()的使用

index_img: https://img-blog.csdnimg.cn/20210203110909566.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













> ##### every()
> 用于判断数组所有元素是否都符合函数返回的条件

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		var array=[86,3,2,52,1];

		var result=array.every((i)=>{ // i相当于遍历的每条array的下标
			return i>2; // 需返回判断条件
		});
		
		console.log(array);   //为什么还要打印原数组？   因为该every()不会对原数组发生改变
		console.log(result);  // 所以上面用变量接收了，此时打印result变量即可得到结果
	</script>
</body>
</html>
```

![js中对数组.map()、some()、every()、filter()的使用](https://img-blog.csdnimg.cn/20200304221257303.png)


---

> ##### some()
> 用于判断数组所有元素中是否有一条满足函数返回的条件

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		var array=[86,3,2,52,1];

		var result=array.some((i)=>{ // i相当于遍历的每条array的下标
			return i>2; // 需返回判断条件
		});
		
		console.log(array);
		console.log(result);
	</script>
</body>
</html>
```

![js中对数组.map()、some()、every()、filter()的使用](https://img-blog.csdnimg.cn/20200304221550414.png)

---
> ##### find()
> 用于查找数组中第一个满足条件的元素，并返回

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>js find</title>
	</head>
	<body>
		<script type="text/javascript">
			var array=[3,2,52,1];
			
			var result=array.find((i)=>{ // i相当于遍历的每条array的下标
				return i>2; // 需返回满足条件
			});
			
			console.log(array);
			console.log(result);
		</script>
	</body>
</html>
```
![](https://img-blog.csdnimg.cn/20210329111909816.png)


---

> ##### filter()
> 用于过滤数组所有满足条件的元素，并返回
> 和every()有些像，但那是返回 ture或false，而filter()是返回**符合条件的数组**

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		var array=[86,3,2,52,1];

		var result=array.filter((i)=>{ // i相当于遍历的每条array的下标
			return i>2; // 返回符合判断条件的结果
		});
		
		console.log(array);
		console.log(result);
	</script>
</body>
</html>
```
![js中对数组.map()、some()、every()、filter()的使用](https://img-blog.csdnimg.cn/20200304222407611.png)


---

> ##### map()
> 处理数组的每个元素，并返回处理后的数组。


```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		var array=[86,3,2,52,1];

		var result=array.map((i)=>{ // i相当于遍历的每条array的下标
			return i*2; // 需返回处理结果
		});
		
		console.log(array);
		console.log(result);
	</script>
</body>
</html>
```


![js中对数组.map()、some()、every()、filter()的使用](https://img-blog.csdnimg.cn/20200304221928124.png)


---

> ##### reduce()
> 用于累加计算，返回结果
> 接收两个参数：function和params。function有有四个参数total, now, index, array。total是前值和后值得累加值，now是当前值，index索引，array数组自身。后两个非必传。params非必传，传递给函数的初始值

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<script>
		var array=[86,3,2,52,1,55];

		var result=array.reduce((total, now, index, array)=>{
		console.log(total, now, index, array);
			return total + now;
		});
		
		console.log(result);
	</script>
</body>
</html>
```
![](https://img-blog.csdnimg.cn/20210203110909566.png)


---


## 更多：[https://www.runoob.com/jsref/jsref-obj-array.html](https://www.runoob.com/jsref/jsref-obj-array.html)

