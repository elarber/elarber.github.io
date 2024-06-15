---
title: js原生超好用的数组分类方法Object.groupBy()

index_img: https://img-blog.csdnimg.cn/direct/5fda0272eb1f4f9091416a59634d2086.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










> [这是个新方法，版本高的浏览器才能用](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/groupBy)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
	</head>
	<body>
		<script>
			const inventory = [
			  { name: "芦笋", type: "蔬菜", quantity: 5 },
			  { name: "香蕉", type: "水果", quantity: 0 },
			  { name: "山羊", type: "肉", quantity: 23 },
			  { name: "樱桃", type: "水果", quantity: 5 },
			  { name: "鱼", type: "肉", quantity: 22 },
			];
			console.log(inventory);


			const result = Object.groupBy(inventory, ({ type }) =>{ return type });
			console.log(result);
			
			const demo = Object.groupBy(inventory, ({ quantity })=> {
				return quantity > 5 ? "ok" : "restock";
			});
			console.log(demo);
		</script>
	</body>
</html>
```



![](https://img-blog.csdnimg.cn/direct/5fda0272eb1f4f9091416a59634d2086.png)



