---
title: js 读取.txt文件【FileReader实例的使用】

index_img: https://img-blog.csdnimg.cn/20200411134237892.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












![js 读取.txt文件](https://img-blog.csdnimg.cn/20200411134237892.gif#pic_center)


##### 文件处理方法：
`FileReader` 的实例拥有 4 个方法，其中 3 个用以读取文件，另一个用来中断读取。下面的表格列出了这些方法以及他们的参数和功能，需要注意的是 ，无论读取成功或失败，方法并不会返回读取结果，这一结果存储在 result属性中。
| 函数 | 参数 | 描述 |
|:--|:--|:--|
| readAsBinaryString | file | 将文件读取为二进制编码 |
| readAsText | file,编码规则 | 将文件读取为文本 |
| readAsDataURL | file | 将文件读取为DataURL |
| abort | none | 终端读取操作 |

1. **readAsText**：该方法有两个参数，其中第二个参数是文本的编码方式，默认值为 UTF-8。这个方法非常容易理解，将文件以文本方式读取，读取的结果即是这个文本文件中的内容。
2. **readAsBinaryString**：该方法将文件读取为二进制字符串，通常我们将它传送到后端，后端可以通过这段字符串存储文件。
3. **readAsDataURL**：这是例子程序中用到的方法，该方法将文件读取为一段以 data: 开头的字符串，这段字符串的实质就是 Data URL，Data URL是一种将小文件直接嵌入文档的方案。这里的小文件通常是指图像与 html 等格式的文件。

##### 事件处理状态
| 事件 | 描述 |
|:--|:--|
|onabort |	中断|
|onerror |出错|
|onloadstart| 开始|
|onprogress |正在读取|
|onload 	|成功读取|
|onloadend 	|读取完成，无论成功失败|

文件一旦开始读取，无论成功或失败，实例的 result 属性都会被填充。如果读取失败，则 result 的值为 null ，否则即是读取的结果，绝大多数的程序都会在成功读取文件的时候，抓取这个值。

```javascript
reader.onload = function() {
    this.result;
}
```

---

#### 例子：
只能读取`.txt`文件，别的文件会乱码
```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<title>读取文件</title>
</head>

<body>
	<input type="file" id="select-input" />
	<div id="content"></div>
	<img id="picture" src="">
	
	
	<script>
		document.getElementById("select-input").addEventListener("change", (e) =>{
			//获取选择的文件对象
			let file = e.target.files[0];
			// 检测浏览器对FileReader的支持
			if(window.FileReader) {
			    // 创建FileReader对象(文件对象)
				const reader = new FileReader();


				/*----------    6种事件模型    ---------*/
				// 开始读取时：
				reader.onloadstart = function(e) {
					console.log("开始读取", e);
				};
				// 正在读取：
				reader.onprogress = function(e) {
					console.log("正在读取",e);
				};
				// 读取出错时：
				reader.onerror = function(e) {
					console.log("读取出错",e);
				};
				// 读取中断时：
				reader.onabort = function(e) {
					console.log("读取中断",e);
				};
				// 读取成功时：
				reader.onload = function(e) {
					console.log("读取成功",e);
					if(/image\/\w+/.test(file.type)){
					    document.getElementById("picture").src = e.target.result;
					}else{
						// 输出文件
						document.getElementById("content").innerText = e.target.result;
					};
					
				};
				// 读取完成，无论成功失败：
				reader.onloadend = function(e) {
					console.log("读取完成，无论成功失败",e);

				};



				/*-------  4种文件读功能(方法、函数)  ------*/
			/*	reader.readAsText(file,"utf-8");
			  	reader.readAsBinaryString(file);  	// 将文件读取为二进制编码
				reader.readAsDataURL(file);  		// 将文件读取为DataURL
				reader.readAsText(none);  			// 终端读取操作 			*/

				
				if(/image\/\w+/.test(file.type)){
					    reader.readAsDataURL(file);
				}else{
					// 输出文件
					reader.readAsText(file,"utf-8");
				};
			}else {
			    alert("Not supported by your browser!");
			};
		}, false);
	</script>
</body>

</html>
```



