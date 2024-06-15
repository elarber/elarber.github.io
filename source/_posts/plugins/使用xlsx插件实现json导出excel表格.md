---
title: 使用xlsx插件实现json导出excel表格

index_img: https://img-blog.csdnimg.cn/c5cd44227fd442d88272a090edc1470d.gif
lazyload: true
categories:
- 前端插件使用
tags:
- xlsx



---













![](https://img-blog.csdnimg.cn/c5cd44227fd442d88272a090edc1470d.gif#pic_center)

[https://blog.csdn.net/qq_42618566/article/details/127978974](https://blog.csdn.net/qq_42618566/article/details/127978974)


```html
<!doctype html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<meta name="viewport"
			content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<script src="https://unpkg.com/xlsx@0.18.5"></script>
		<title>json to excel</title>
	</head>
	<body>
		<button onclick="toExcel()">导出</button>

		<script>
			const demo = [{
					name: "电量",
					cusp: "111",
					peak: "222",
					flat: "333",
					grain: "444"
				},
				{
					name: "电费",
					cusp: "111",
					peak: "222",
					flat: "333",
					grain: "444"
				},
				{
					name: "服务费",
					cusp: "111",
					peak: "222",
					flat: "333",
					grain: "444"
				}
			];

			function toExcel() {
				const fileName = "json导出的例子.xlsx";
				const sheetName = "Sheet 1";

				const excel = XLSX.utils.book_new();
				const data = XLSX.utils.json_to_sheet(demo);


				XLSX.utils.book_append_sheet(excel, data, sheetName);
				XLSX.writeFile(excel, fileName);
			}
		</script>
	</body>
</html>

```
