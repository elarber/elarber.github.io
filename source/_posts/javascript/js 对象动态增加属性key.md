---
title: js 对象动态增加属性key

index_img: https://img-blog.csdnimg.cn/20201024152321493.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










语法：
>    `对象[属性] = "值";`  // 在属性的地方可以放变量

**示例：**
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>动态增加key</title>
	</head>
	<body>
		<script type="text/javascript">
			var data = {
				text: "呀呀呀呀呀呀呀呀",
				what: "v恩发了可能八万人",
			};
			for (let i = 1; i <= 10; i++) {
				data["lable" + i] = "值" + i; // 重点重点重点重点重点重点重点
			};
			console.log(data);
		</script>
	</body>
</html>
```

![js 对象动态增加属性key](https://img-blog.csdnimg.cn/20201024152321493.png#pic_center)




