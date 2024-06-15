---
title: css选择前几个元素或者后几个元素

index_img: https://img-blog.csdnimg.cn/20200818113631736.png
lazyload: true
categories:
- css


tags:
- css

---




![css选择前几个元素或者后几个元素](https://img-blog.csdnimg.cn/20200818113631736.png#pic_center)


```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title></title>
		<style type="text/css">
			#nth-test div:nth-child(-n + 4) {
				background-color: red;
			}
		</style>
	</head>
	<body>
		<div id="nth-test">
			<div>1</div>
			<div>2</div>
			<div>3</div>
			<div>4</div>
			<div>5</div>
			<div>6</div>
			<div>7</div>
		</div>
	</body>
</html>
```
选前四个：

```css
#nth-test div:nth-child(-n + 4) {
	background-color: red;
}
```
![css选择前几个元素或者后几个元素](https://img-blog.csdnimg.cn/20200818114141705.png#pic_center)



选弟3个往后的：

```css
#nth-test div:nth-child(n + 3) {
	background-color: red;
}
```
![css选择前几个元素或者后几个元素](https://img-blog.csdnimg.cn/20200818114121550.png#pic_center)



选偶数元素：

```javascript
#nth-test div:nth-child(2n) {
	background-color: red;
}
```
![css选择前几个元素或者后几个元素](https://img-blog.csdnimg.cn/20200818113954116.png#pic_center)


选基数元素：

```css
#nth-test div:nth-child(2n+1) {
	background-color: red;
}
```

![css选择前几个元素或者后几个元素](https://img-blog.csdnimg.cn/20200818114032946.png#pic_center)




