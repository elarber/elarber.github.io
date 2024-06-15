---
title: 前端js压缩图片：compressionjs的使用

index_img: https://img-blog.csdnimg.cn/baaddc910e5b4bfdae28e00c49bfb84b.png
lazyload: true
categories:
- 前端插件使用
tags:
- compressionjs
- 压缩图片


---











>  [compressionjs](https://www.npmjs.com/package/compressorjs)

![](https://img-blog.csdnimg.cn/baaddc910e5b4bfdae28e00c49bfb84b.png)



```html
<!DOCTYPE html>
<html lang="zh">
	<head>
		<title>前端图片压缩 Compressor</title>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
	</head>
	<body>
		<input type="file" id="input" multiple="multiple" accept="image/*">


		<script src="https://unpkg.com/compressorjs@1.1.1"></script>
		<script type="text/javascript">
			window.onload = function() {
				document.getElementById('input').addEventListener('change', (e) => {
					console.log("图片：", e.target.files);

					for (let item of e.target.files) {
						console.log("压缩前：", item);
						new Compressor(item, {
							success(result) {
								console.log("压缩后：", result);



							},
							error(err) {
								console.log(err);
							},
						});
					}
				});
			}
		</script>
	</body>
</html>

```




