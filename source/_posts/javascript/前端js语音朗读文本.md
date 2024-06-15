---
title: 前端js语音朗读文本

index_img: https://img-blog.csdnimg.cn/dd90d07719a545d09e4ddbf563724a83.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- 语音



---











```html
<!DOCTYPE html>
<html lang="zh">
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<title>语音朗读</title>
	</head>
	<body>
		<textarea id="textarea" rows="20" cols="70"></textarea>
		<button onclick="reading()">朗读</button>

		<script>
			function reading() {
				const value = document.querySelector("#textarea").value;
				if (!value) {
					return alert("填入朗读文本");
				}
				const speech = new SpeechSynthesisUtterance(value);
				speechSynthesis.speak(speech);


				speech.onstart = (e) => {
					console.log("开始读");
				}
				speech.onend = (e) => {
					console.log("读完了");
				}
			}
		</script>
	</body>
</html>
```

![](https://img-blog.csdnimg.cn/dd90d07719a545d09e4ddbf563724a83.png)

打开你的声音听听



> ## SpeechSynthesis实例对象属性
> lang 获取并设置话语的语言
> pitch 获取并设置话语的音调(值越大越尖锐,越低越低沉)
> rate 获取并设置说话的速度(值越大语速越快,越小语速越慢)
> text 获取并设置说话时的文本
> voice 获取并设置说话的声音
> volume 获取并设置说话的音量
> 
> 
> ## SpeechSynthesis方法
> speak() 将对应的实例添加到语音队列中
> cancel() 删除队列中所有的语音.如果正在播放,则直接停止
> pause()暂停语音
> resume() 恢复暂停的语音
> getVoices 获取支持的语言数组. 注意:必须添加在voiceschanged事件中才能生效
> 
> 
> ## 实例对象中的方法
> onstart – 语音合成开始时候的回调
> onpause – 语音合成暂停时候的回调
> onresume – 语音合成重新开始时候的回调
> onend – 语音合成结束时候的回调
> 
>  


