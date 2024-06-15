---
title: js操作css变量（属性）

index_img: https://img-blog.csdnimg.cn/20200820164327655.gif
lazyload: true
categories:
- css


tags:
- css

---



![前端页面一键切换主题色](https://img-blog.csdnimg.cn/20200820164327655.gif#pic_center)



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title></title>
		<style type="text/css">
			:root {
				--bg: white;
			}

			body {
				background-color: var(--bg);
			}
		</style>
	</head>
	<body>
		<button type="button" id="red">红</button>
		<button type="button" id="blue">蓝</button>
		<button type="button" id="green">绿</button>


		<script type="text/javascript">
			["red", "blue", "green"].forEach(value => {
				const btn = document.getElementById(`${value}`);
				btn.addEventListener("click", () => {
					document.body.style.setProperty("--bg", value);
				});
			});
		</script>
	</body>
</html>
```



