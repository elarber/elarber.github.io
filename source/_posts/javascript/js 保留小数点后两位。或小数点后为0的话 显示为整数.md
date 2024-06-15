---
title: js 保留小数点后两位。或小数点后为0的话 显示为整数

# index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











1. `num.toFixed(2)`
	四舍五入
	```javascript
	var num =2.446242342;  
	num = num.toFixed(2); 
	console.log(num); // 2.45
	console.log(typeof num); // string
	```

2. 不四舍五入 向下取整
	
	```javascript
	num = Math.floor(num * 100) / 100;
	console.log(num); //2.44
	console.log(typeof num); // number
	```


3. parseFloat()
	小数点后不为0，就保留2位。否则为整数
	```javascript
	var num =2.446242342;  
	parseFloat(num)
	console.log(parseFloat(num)); // 2.45
	console.log(typeof num); // number

	var num2 =6.00;  
	parseFloat(num2)
	console.log(parseFloat(num2)); // 6
	console.log(typeof num2); // number
	```

