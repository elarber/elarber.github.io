---
title: 项目引入腾讯QQ的登陆

index_img: https://img-blog.csdnimg.cn/20210406101200484.gif
lazyload: true
categories:
- 前端插件使用
tags:
- QQ登陆



---











![](https://img-blog.csdnimg.cn/20210406101200484.gif#pic_center)


#### 使用文档：[https://wiki.connect.qq.com/js_sdk%e4%bd%bf%e7%94%a8%e8%af%b4%e6%98%8e](https://wiki.connect.qq.com/js_sdk%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)

1. 引入QQ提供的依赖：[https://connect.qq.com/qc_jssdk.js](https://connect.qq.com/qc_jssdk.js)
2. 代码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title></title>
	</head>
	<body>
		<span id="login_btn">登陆</span>


		<script src="./qc_jssdk.js" data-appid="你的appid" data-redirecturi="登陆后的回调"></script>
		<script type="text/javascript">
			QC.Login({
				btnId: 'login_btn'
			})
		</script>
	</body>
</html>
```


