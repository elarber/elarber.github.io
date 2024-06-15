---
title: 前端图片裁剪 cropperjs的简单使用

index_img: https://img-blog.csdnimg.cn/11358723acc747c681dceca858bad11f.gif
lazyload: true
categories:
- 前端插件使用
tags:
- cropperjs
- 裁剪图片


---











> [https://github.com/fengyuanchen/cropperjs](https://github.com/fengyuanchen/cropperjs)
> [演示](https://fengyuanchen.github.io/cropperjs/)


![](https://img-blog.csdnimg.cn/11358723acc747c681dceca858bad11f.gif#pic_center)




```html
<!DOCTYPE html>
<html lang="zh">
	<head>
		<title>前端图片裁剪 cropperjs</title>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<link rel="stylesheet" href="https://unpkg.com/cropperjs@1.5.12/dist/cropper.css">
	</head>
	<body>
		<input type="file" id="input" accept="image/*">
		<img id="after-image" src="" style="display: block;">
		<button onclick="ok()" style="display: block;">裁剪</button>
		
		<hr />
		处理后：
		<img id="before-image" src="" style="display: block;">





		<script src="https://unpkg.com/cropperjs@1.5.12"></script>
		<script type="text/javascript">
			const Aimage = document.getElementById('after-image');
			let cropper;
			document.getElementById('input').addEventListener('change', (e) => {
				const file = e.target.files[0];

				const reader = new FileReader(); // 创建FileReader对象(文件对象)
				console.log(reader);
				reader.readAsDataURL(file);
				reader.onload = (e) => {
					console.log("读取成功", e.target.result);
					Aimage.src = e.target.result;

					cropper = new Cropper(Aimage, {
						viewMode: 1
					});
				};
			})

			function ok() {
				const Bimage = document.getElementById('before-image');
				Bimage.src = cropper.getCroppedCanvas({
					imageSmoothingQuality: 'high'
				}).toDataURL('image/png')
				console.log("处理后：",Bimage.src);
			}
		</script>
	</body>
</html>
```


