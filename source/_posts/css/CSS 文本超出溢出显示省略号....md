---
title: CSS 文本超出溢出显示省略号...

index_img: https://img-blog.csdnimg.cn/20190820175329166.png
lazyload: true
categories:
- css


tags:
- css

---






![](https://img-blog.csdnimg.cn/20190820175230134.png)
![](https://img-blog.csdnimg.cn/20190820175329166.png)
**源码：**




```css
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		p{
		  overflow : hidden;
		  text-overflow: ellipsis;
		  display: -webkit-box;
		  -webkit-line-clamp: 2;         /* 可以显示的行数，超出部分用...表示*/
		  -webkit-box-orient: vertical;
		}
	</style>
</head>
<body>
	<p>因使用了WebKit的CSS扩展属性，该方法适用于WebKit浏览器及移动端；
		注：
		-webkit-line-clamp用来限制在一个块元素显示的文本的行数。 为了实现该效果，它需要组合其他的WebKit属性。常见结合属性：
		display: -webkit-box; 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
		-webkit-box-orient 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。因使用了WebKit的CSS扩展属性，该方法适用于WebKit浏览器及移动端；

		注：
		-webkit-line-clamp用来限制在一个块元素显示的文本的行数。 为了实现该效果，它需要组合其他的WebKit属性。常见结合属性：
		display: -webkit-box; 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
		-webkit-box-orient 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。因使用了WebKit的CSS扩展属性，该方法适用于WebKit浏览器及移动端；

		注：
		-webkit-line-clamp用来限制在一个块元素显示的文本的行数。 为了实现该效果，它需要组合其他的WebKit属性。常见结合属性：
		display: -webkit-box; 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
		-webkit-box-orient 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。
	</p>
</body>
<!--  或者  -->
<script type="text/javascript">
		s = '今天学习任务是总结1、快排代码及思想，2、css实现三角形圆形，3、js和css实现限制显示字数，文字长度超出部分用省略号表示 '
		el = document.getElementByTagName('p');
		n = el.offsetHeight;  //取到当前包裹文本的父级元素的高度， 
		for(i=0; i<s.length; i++) {
		          el.innerHTML = s.substr(0, i);  //表示在for循环中取出长度递增的文段
		          if(n < el.scrollHeight) { 
		          //当前文本高度的内容的高度代表着刚好达到溢出的界限，
		             el.style.overflow = 'hidden';  //将父级元素设置为隐藏
		             el.innerHTML = s.substr(0, i-3) + '...';  //最后三个字
		             break;
		     }
		}
</script>
</html>
```

单行超出：

```css
		.news .panel p {
            overflow: hidden;
            text-overflow:ellipsis;
            white-space: nowrap;
        }
```



