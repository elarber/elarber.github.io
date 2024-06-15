---
title: js区分浏览器关闭 or 刷新

# index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













js浏览器关闭 or 刷新

```html
<!DOCTYPE html>
<html>

<head>
	<meta charset="utf-8">
	<title>浏览器关闭 or 刷新</title>
</head>

<body>
	<input type="button" onclick="disp_confirm()" value="Display a confirm box" />
	<script type="text/javascript">
		function disp_confirm() {
			localStorage.setItem("text", "111111111111111111111111")
		}

		var time = {
			beginTime: 0,//执行onbeforeunload的开始时间
			differTime: 0//时间差
		}
		window.onunload = function () {
			time.differ = new Date().getTime() - time.begin;
			if (time.differ <= 3) {
				localStorage.clear();
			} else {
				console.log("浏览器刷新")
			}
		}
		window.onbeforeunload = function () {
			time.begin = new Date().getTime();
		};
	</script>
</body>

</html>
```
