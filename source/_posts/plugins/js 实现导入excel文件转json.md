---
title: js 实现导入excel文件转json

index_img: https://img-blog.csdnimg.cn/062013370c1842b59e7b26747f254377.gif
lazyload: true
categories:
- 前端插件使用
tags:
- exceljs



---











![](https://img-blog.csdnimg.cn/062013370c1842b59e7b26747f254377.gif#pic_center)


```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<meta http-equiv="X-UA-Compatible" content="IE=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<title>excel to json</title>
		<script src="https://unpkg.com/xlsx@0.18.5"></script>
	</head>

	<body>
		<input type="file" onchange="toJSON(this)">


		<script>
			function toJSON(obj) {
				if (!obj.files) {
					return;
				}


				const file = obj.files[0];
				const reader = new FileReader();
				reader.onload = function(e) {
					const excel = XLSX.read(e.target.result, {
						type: 'binary'
					});
					console.log('excel: ', excel);
					
					const json = excel.SheetNames.map(item => {
						return XLSX.utils.sheet_to_json(excel.Sheets[item])
					})
					console.log('JSON: ', json);
				};
				reader.readAsBinaryString(file);
			}
		</script>
</html>

```


