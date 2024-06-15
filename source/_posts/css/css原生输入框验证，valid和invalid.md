---
title: css原生输入框验证，valid和invalid

index_img: /img/articles/
lazyload: true
categories:
- css


tags:
- css

---








![css原生输入框验证，:valid和:invalid](https://img-blog.csdnimg.cn/20200319102836669.gif)

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<style>
	input{
	  display: block;
	  padding: 0 20px;
	  outline: none;
	  border: 1px solid #ccc;
	  width: 150px;
	  height: 40px;
	  transition: all 300ms;
	}
	/*input内容合法时：边框颜色是绿色*/
	input:valid {
	  border-color: green;
	  box-shadow: inset 5px 0 0 green;
	}
	/* input内容非法时：边框颜色是红色*/
	input:invalid {
	  border-color: red;
	  box-shadow: inset 5px 0 0 red;
	}
	button{
	  width: 190px;
	  height: 40px;
	  background-color: green;
	  color: white;
	  margin-top: 20px;
	}
</style>
<body>
	<form>
		<input type="text" maxlength="11" placeholder="请输入手机号码" pattern="^1[3456789]\d{9}$" required>
		<button type="submit">提交</button>
	</form>
</body>
</html>
```



