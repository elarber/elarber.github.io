---
title: js 对比两个数组是否相同

index_img: https://img-blog.csdnimg.cn/74a4f06fb41a4195b93003a287a12829.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title></title>
	</head>
	<body>
		<script type="text/javascript">
			var a = ["13", "3123", "3131", "431321", "343123"];
			var b = ["343123", "13", "3123", "3131", "431321"];



// func(a,b)   用a的第一个元素和b的所有元素从左到右依次进行比较，找到相同元素就将a的这个元素和b的这个元素删除掉，接着用a的第二个元素和b的所有元素从左到右依次比较，相同元素就从a和b中删除掉，最后看a和b中 有没有多余的元素
			function same(aa, bb) {
				let cc = [...bb];
				for (let item in aa) {
					for (let it in cc) {
						if (aa[item] === cc[it]) {
							cc.splice(it, 1)
							// console.log(cc);
						}
					}
				}
				return cc.length < 1 ? true : false;
			}

			let result = same(a, b);
			console.log(result);
		</script>
	</body>
</html>

```

![](https://img-blog.csdnimg.cn/74a4f06fb41a4195b93003a287a12829.png)

