---
title: js 原生请求fetch和ajax

index_img: https://img-blog.csdnimg.cn/20201027111756972.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













#### 第一种：`XMLHttpRequest`实例

![js 原生AJAX请求数据](https://img-blog.csdnimg.cn/20191022143848652.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<title>AJAX请求</title>
</head>

<body>
	<div id="myDiv">
		<h2>使用 AJAX 修改该文本内容</h2>
	</div>
	<button type="button" onclick="loadXMLDoc()">修改内容</button>

	<script>
		function loadXMLDoc() {
			var xmlhttp;
			if (window.XMLHttpRequest) {
				xmlhttp = new XMLHttpRequest();  //  IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
			}
			else {
				xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");  // IE6, IE5 浏览器执行代码
			}
			xmlhttp.onreadystatechange = function () {
				if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
					document.getElementById("myDiv").innerHTML = xmlhttp.responseText;
					console.log(xmlhttp)
				}
			}
			/* 	// GET请求：
				xmlhttp.open("GET", "https://www.apiopen.top/journalismApi", true); // 第一个值：请求方式，第二个值：请求的接口，第三个值：是否异步请求
				xmlhttp.send(); */

			// 或者POST请求，请使用 setRequestHeader() 来添加 HTTP 头。然后在 send() 方法中规定您希望发送的数据：
			xmlhttp.open("POST", "https://www.apiopen.top/journalismApi", true);
			xmlhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
			xmlhttp.send("name=全易 & position=前端开发");
		}
	</script>
</body>

</html>
```


![js 原生AJAX请求数据](https://img-blog.csdnimg.cn/20191022144134455.gif)
![js 原生AJAX请求数据](https://img-blog.csdnimg.cn/20191022150127916.png)



拓展：[https://blog.csdn.net/sinat_35861727/article/details/78809986](https://blog.csdn.net/sinat_35861727/article/details/78809986)


---

第二种：js原生fatch函数
![](https://img-blog.csdnimg.cn/2021042517363140.png)


```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title></title>
	</head>
	<body>
		<button type="button" class="btn">获取token</button>

		<script>
			const btn = document.querySelector(".btn");
			btn.onclick = function() {
				fetch('https://mamsc.sgcc.com/router/aaaaaa', {
					method: 'POST',
					body: JSON.stringify({
						key: "8e15edc35cb68460d4jn08b840f62791",
						serviceId: "55442aaea86f7bb410a77326770e24be",
						account: "13611260499",
						password: "BD2B1D3B0A688CE2130A0BB2802195E3"
					}),
					headers: {
						"Content-Type": "application/x-www-form-urlencoded; application/json; text/plain; charset=UTF-8",
					},
				}).then(res => {
					console.log(res)
				});
			}
		</script>
	</body>
</html>
```

![js原生fatch函数](https://img-blog.csdnimg.cn/20201027111756972.png#pic_center)

![js原生fatch函数](https://img-blog.csdnimg.cn/20201027111833704.png#pic_center)


