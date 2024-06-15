---
title: js判断当前浏览器是什么浏览器

index_img: https://img-blog.csdnimg.cn/20191029162103610.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













```javascript
		console.log(navigator)
		const explorer = navigator.userAgent;
		var Browser;
		// IE  判断浏览器是否支持ActiveX控件，如果浏览器支持ActiveX控件可以利用,
		if (!!window.ActiveXObject || "ActiveXObject" in window) {
		  Browser = 'ie';
		  console.log("当前浏览器为：IE");
		}
		//IE  documentMode是一个IE的私有属性，在IE8+中被支持。
		if (window.document.documentMode) {
		  Browser = 'ie';
		  console.log("当前浏览器为：IE");
		}
		//firefox 
		else if (explorer.indexOf("Firefox") >= 0) {
		  Browser = 'Firefox';
		  console.log("当前浏览器为：Firefox");
		}
		//Chrome
		else if (explorer.indexOf("Chrome") >= 0) {
		  Browser = 'Chrome';
		  console.log("当前浏览器为：Chrome");
		}
		//Opera
		else if (explorer.indexOf("Opera") >= 0) {
		  Browser = 'Opera';
		  console.log("当前浏览器为：Opera");
		}
		//Safari
		else if (explorer.indexOf("Safari") >= 0) {
		  Browser = 'Safari';
		  console.log("当前浏览器为：Safari");
		}
		//Netscape
		else if (explorer.indexOf("Netscape") >= 0) {
		  Browser = 'Netscape';
		  console.log('当前浏览器为：Netscape');
		}
```


![js判断当前浏览器是什么浏览器](https://img-blog.csdnimg.cn/20191029162103610.gif)