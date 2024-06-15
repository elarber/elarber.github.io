---
title: 原生js手撸乞丐版 vs code

index_img: https://img-blog.csdnimg.cn/direct/94f728e9f0d145089b43f6cb9ccb3059.gif
lazyload: true
categories:
- javascript
tags:
- js
- vs code
- javascript



---













![请添加图片描述](https://img-blog.csdnimg.cn/direct/94f728e9f0d145089b43f6cb9ccb3059.gif)



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>手搓vs code</title>
		<link rel="stylesheet"
			href="http://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.7.0/styles/atom-one-dark.min.css" />
		<style>
			body {
				margin: 0;
			}

			.editer {
				display: flex;
			}

			.directory {
				width: 300px;
				height: 100vh;
				overflow: auto;
				background-color: #252424;
				color: #ffffff;
			}

			.directory .open-btn {
				width: 100%;
				height: 36px;
			}

			.directory .files div {
				margin: 10px 25px;
			}

			.directory .files details {
				margin: 10px 5px;
			}

			.content {
				margin: 0;
				width: -webkit-fill-available;
				height: 100vh;
				overflow: auto;
				background-color: #313131;
			}

			.content .code {
				margin: 0;
				/* width: 100%; */
				/* height: 100%; */
				padding: 0;
				overflow: auto;
				border: none;
				background-color: #313131;
				color: #ffffff;
			}
		</style>
	</head>
	<body>
		<div class="editer">
			<div class="directory">
				<button class="open-btn" onclick="selectedFile()">打开</button>
				<div class="files"></div>
			</div>
			<pre class="content">
				<code class="code language-javaScript"></code>
			</pre>
		</div>



		<script>
			async function selectedFile() {
				try {
					const directories = await showDirectoryPicker()
					// console.log(directories);
					const files = await handleDirectory(directories)
					// console.log(files);

					const filesDOM = document.querySelector(".files");
					renderDirectoryTag(files, filesDOM)
				} catch (e) {
					console.log("您拒绝了访问目录, 授权打开目录才能导入文件");
				}
			};

			// 处理目录资源
			async function handleDirectory(data) {
				// 直接返回句柄
				if (data.kind === "file") {
					return data;
				}
				// 递归处理
				data.children = [];
				for await (const iterator of data.entries()) {
					// console.log(iterator);
					data.children.push(await handleDirectory(iterator[1]))
				}
				return data;
			};

			// 渲染 html
			function renderDirectoryTag(files, filesDOM) {
				// console.log(files, filesDOM);
				for (const index in files.children) {
					const file = files.children[index];
					// console.log(index, file);
					let details;
					if (file.children?.length > 0) {
						details = document.createElement("details")
						details.innerHTML = `<summary>${file.name}</summary>`;
						filesDOM.appendChild(details)
						renderDirectoryTag(file, details)
					} else {
						details = document.createElement("div")
						details.innerHTML = `<span>${file.name}</span>`;
						details.addEventListener('click', ()=>{
							readerFile(file)
						}, true)
					}
					filesDOM.appendChild(details)
				}
			}
			// 读取文件
			async function readerFile(file) {
				// console.log(file);
				const files = await file.getFile()
				// console.log(files);
				const reader = new FileReader();
				reader.readAsText(files, 'utf-8')
				reader.onload = (e) => {
					// console.log(e);
					const codeDOM = document.querySelector(".code");
					codeDOM.innerHTML = e.target.result;
					hljs.highlightBlock();
				}
			}
		</script>

		<script src="http://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.7.0/highlight.min.js"></script>
		<script>
			hljs.highlightAll();
		</script>
	</body>
</html>
```
