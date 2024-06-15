---
title: 前端使用printJS插件 执行浏览器打印

index_img: 
lazyload: true
categories:
- 前端插件使用
tags:
- printJS



---












# 案例
```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<meta http-equiv="X-UA-Compatible" content="IE=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<title>打印</title>
	</head>

	<body>
		<button onclick="printing()">打印</button>
		<div class="is-print" style="width: 800px;">
			<p>1、刚才做了一个风险非常大的投资，要是成功了，一下就能挣几个亿，要是失败了，我这两块钱就打了水漂了。</p>
			<p>2、当你生活不顺心的时候，不要慌。看看你的钱包和存款，哭出来就好了。</p>
			<p>3、我与我的床坠入了爱河，我们对彼此而言，都非常的完美。但闹钟并不这么想，那个妒忌心重的贱货。</p>
			<p>4、我曾天真地以为金钱是万能的，后来才发现，金钱不是万能的，是无所不能的。</p>
			<p>5、家长永远分不清解释和顶嘴，你解释就是顶嘴，你再说一句就是抬扛。</p>
			<p>6、我相亲了一个女孩，我妈特喜欢，我爸也很喜欢，最后认她做干女儿了，还说我配不上她。</p>
			<p>7、有的女生像莲花，出水芙蓉。有的女生像牡丹，高贵典雅。有的女生像梅花，高冷孤傲。而你像多肉，胖嘟嘟、圆滚滚。</p>
			<p>8、命里有时终须瘦，命里无时胖成球，今朝有酒今朝醉，明日更肥明日忧。</p>
			<p>9、一个男人拼命挣钱却不注意健康，等于是在给另一个男人打工！一个女人拼命省钱却不注意修养，是在给另一个女人腾地方。</p>
			<p>10、你如果真觉得我哪里不对，请一定要告诉我，反正我也不会改，你可千万不要憋出病来呀。</p>
			<p>11、朋友说我有双下巴了，都是经常低头刷手机导致的。从那之后，每次刷手机我都举高高地往上看。没想到，一个月之后我有了抬头纹。</p>
			<p>12、小时候被奶奶叫龟孙子，稍微长大点被叫兔崽子，如今却沦为一只单身狗，我这一辈子简直就是一部禽兽史！</p>
			<p>13、如果你实在没朋友，就去给喜欢的人表白，她会提出跟你当朋友的。</p>
			<p>14、失败是成功之母，那成功之父是谁呢？向我转账十元，你就是成功支付！</p>
			<p>15、别人分手了可以一个人去巴黎，而我分手了只能去楼下的牛肉面馆，吃一碗六块钱的牛肉面，还不敢加蛋。</p>
		</div>
	</body>


	<script src="https://cdn.jsdelivr.net/npm/print-js@1.6.0"></script>
	<script>
		function printing() {
			const element=document.querySelector(".is-print");
			printJS({
				// maxWidth: "1000", // 要大于被打印的根容器宽度
				maxWidth: window.innerWidth,
				type: "html",
				printable: element,
				targetStyles: ["*"],
			});
		}
	</script>
</html>
```


# 配置
|  参数 | 默认值 | 说明 |
|--|--|--|
|  printable:	  |  null	  |  文档来源：pdf或图像的url，html元素的id或json数据的对象  |  
|  type:	  |  PDF	  |  可打印类型。可用的打印选项包括：pdf，html，image，json和raw-html。  |  
|  header:	  |  null	  |  用于HTML，Image或JSON打印的可选标头。它将放在页面顶部。此属性将接受文本或原始HTML  |  
|  headerStyle:	  |  'font-weight：300;'	  |  要应用于标题文本的可选标题样式  |  
|  maxWidth:	  |  800	  |  最大文档宽度（像素）。根据需要更改此项。在打印HTML，图像或JSON时使用。  |  
|  css:	  |  null	  |  这允许我们传递一个或多个应该应用于正在打印的html的css文件URL。值可以是包含单个URL的字符串，也可以是包含多个URL的数组。  |  
|  style:	  |  null	  |  这允许我们传递一个字符串，该字符串应该应用于正在打印的html。  |  
|  scanStyles:  |  	true	  |  设置为false时，库不会处理应用于正在打印的html的样式。使用css参数时很有用。  |  
|  targetStyle:	  |  null	  |  默认情况下，在打印HTML元素时，库仅处理某些样式。此选项允许您传递要处理的样式数组。例如：['padding-top'，'border-bottom']  |  
|  targetStyles:	  |  null	  |  与targetStyle相同，这将处理任何一系列样式。例如：['border'，'padding']，将包括'border-bottom'，'border-top'，'border-left'，'border-right'，'padding-top'等。你也可以传递['*']来处理所有样式  |  
|  ignoreElements:	  |  []	  |  接受打印父html元素时应忽略的html的id数组。  |  
|  properties:	  |  null	  |  在打印JSON时使用。这些是对象属性名称。  |  
|  gridHeaderStyle:	  |  'font-weight：bold;'	  |  打印JSON数据时网格标题的可选样式。  |  
|  gridStyle:	  |  'border:   1px solid lightgray; margin-bottom: -1px;'	  |  打印JSON数据时网格行的可选样式  |  
|  repeatTableHeader:	  |  true	  |  在打印JSON数据时使用。设置为时false，数据表标题仅显示在第一页中。  |  
|  showModal:	  |  null	  |  启用此选项可在检索或处理大型PDF文件时显示用户反馈  |  
|  modalMessage:	  |  'Retrieving Document...'	  |  当向用户显示的消息showModal被设定为true。  |  
|  onLoadingStart:	  |  null	  |  加载PDF时要执行的功能  |  
|  onLoadingEnd:	  |  null	  |  加载PDF后要执行的功能  |  
|  documentTitle:	  |  'Document'	  |  打印html，image或json时，它将显示为文档标题。如果用户尝试将打印作业保存为pdf文件，它也将是文档的名称。  |  
|  fallbackPrintable:  |  	null	  |  打印pdf时，如果浏览器不兼容（检查浏览器兼容性表），库将在新选项卡中打开pdf。这允许您传递要打开的不同pdf文档，而不是传递给printable的原始文档。如果您在备用pdf文件中注入javascript，这可能很有用。  |  
|  onPdfOpen :	  |  null	  |  打印pdf时，如果浏览器不兼容（检查浏览器兼容性表），库将在新选项卡中打开pdf。可以在此处传递回调函数，这将在发生这种情况时执行。在您想要处理打印流程，更新用户界面等的某些情况下，它可能很有用。  |  
|  onPrintDialogClose:	  |  null  |  	关闭浏览器打印对话框后执行回调功能  |  
|  onError:	  |    |  error => throw error	发生错误时要执行的回调函数。  |  
|  base64:	  |  false  |  	在打印作为base64数据传递的PDF文档时使用  |  





