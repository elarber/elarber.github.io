---
title: Web Components 原生开发使html组件化模块化

index_img: https://img-blog.csdnimg.cn/dc370edb15f945f8971f26c9947ee6f2.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- 原生组件
- Web Components



---









目录结构：
![](https://img-blog.csdnimg.cn/20210125094842875.png)

入口文件：==index.html==

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>使用组件</title>
		<!-- <link rel="import" href="components/hello-world.html" id="hello-world"> -->
	</head>
	<body>
		<hello-world></hello-world>


		<script type="module" src="./components/hello-world.js"></script>
	</body>
</html>
```

模块文件：

```javascript
// import './header.js' //引入组件

class HelloWorld extends HTMLElement {
	constructor() {
		super();
		const shadowRoot = this.attachShadow({ mode: 'open' });
		shadowRoot.innerHTML = this.template();
	}
	template() {
		return `
			<style>
					h1{
					color: #f00;
					}
			</style>

			<h1>组件元素</h1>
			<!-- <edo-header></edo-header> -->
		`;
	}
	// 生命周期：首次被插入文档DOM时
	connectedCallback() {
		console.log('template element is connected');
	}
	// 生命周期：从文档DOM中删除时
	disconnectedCallback() {
		console.log(1111);
	}
	// 生命周期：被移动到新的文档时
	adoptedCallback() {
		console.log(22222);
	}

	// 生命周期：监听属性变化
	attributeChangedCallback() {
		console.log(3333333);
	}
}
customElements.define('hello-world', HelloWorld);
```
打开：
![](https://img-blog.csdnimg.cn/dc370edb15f945f8971f26c9947ee6f2.png)

效果：
![](https://img-blog.csdnimg.cn/a0105d0f7d724e0e853beeef8ae491d9.png)





