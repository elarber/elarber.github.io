---
title: 前端excel带样式导出 exceljs 插件的使用

index_img: https://img-blog.csdnimg.cn/direct/66136ee010964a95a140990b0a330383.png
lazyload: true
categories:
- 前端插件使用
tags:
- exceljs



---













本来用的xlsx和xlsx-style两个插件，过程一步一个坑，到完全能用要消灭好多bug。这时发现了[exceljs](https://www.npmjs.com/package/exceljs)，真香😀

![](https://img-blog.csdnimg.cn/direct/66136ee010964a95a140990b0a330383.png)


# 案例

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>exceljs 使用</title>
	</head>
	<body>
		<button onclick="exporting()">导出</button>



		<script>
			function exporting() {
				// 创建工作簿
				const workbook = new ExcelJS.Workbook()
				// 添加工作表
				const worksheet = workbook.addWorksheet('sheet1')



				// 设置表头
				worksheet.columns = [{
						header: '名次',
						key: 'sort',
						width: 10
					},
					{
						header: '班级',
						key: 'class',
						width: 20
					},
					{
						header: '姓名',
						key: 'name',
						width: 20
					},
					{
						header: '得分',
						key: 'score',
						width: 10
					},
				]

				// 添加表体数据
				worksheet.addRow({
					sort: 1,
					class: '前端三班',
					name: 'Buer',
					score: 99
				})
				worksheet.addRow({
					sort: 2,
					class: '前端一班',
					name: 'Jack',
					score: 86
				})
				worksheet.addRow({
					sort: 3,
					class: '前端一班',
					name: 'Mary',
					score: 58
				})


				// 设置单元格 
				const aCell = worksheet.getCell('A1')
				// 1.边框 https://github.com/exceljs/exceljs/blob/HEAD/README_zh.md#%E8%BE%B9%E6%A1%86
				aCell.border = {
					top: {
						style: 'thin'
					},
					left: {
						style: 'thin'
					},
					bottom: {
						style: 'thin'
					},
					right: {
						style: 'thin'
					},
				}
				// 2.填充 https://github.com/exceljs/exceljs/blob/HEAD/README_zh.md#%E5%A1%AB%E5%85%85
				aCell.fill = {
					type: 'pattern',
					pattern: 'mediumGray',
					fgColor: {
						rgb: '#c2c2c2'
					}
				}

				// 设置行样式 https://github.com/exceljs/exceljs/blob/HEAD/README_zh.md#%E5%AD%97%E4%BD%93
				worksheet.getRow(1).font = {
					bold: true,
				}










				// 导出表格
				workbook.xlsx.writeBuffer().then((buffer) => {
					const blob = new Blob([buffer], {
						type: ''application/vnd.openxmlformats-officedocument.spreadsheetml.sheet''
					})
					const link = document.createElement('a')
					link.href = URL.createObjectURL(blob)
					link.download = '测试' + '.xlsx'
					link.click()
					URL.revokeObjectURL(link.href) // 下载完成释放掉blob对象
				})
			}
		</script>
		<script src="https://cdn.jsdelivr.net/npm/exceljs@4.4.0"></script>
	</body>
</html>
```





> **列宽自适应：**[https://ask.csdn.net/questions/8062252/54484687?spm=1001.2014.3001.5501](https://ask.csdn.net/questions/8062252/54484687?spm=1001.2014.3001.5501)
