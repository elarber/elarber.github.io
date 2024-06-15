---
title: npm发布自己的公网包步骤详解

index_img: https://img-blog.csdnimg.cn/45951ea351ce4cfd96d1f693755d0841.png
lazyload: true
categories:
- 前端周边
tags:
- npm
- 公网发包



---












# 初始化项目

1. 比如我，创建了code-transfor-text_vue项目
![](https://img-blog.csdnimg.cn/020becc7c88d42cd9a9ac559a14a5eac.png)

![](https://img-blog.csdnimg.cn/63d4b6d00a444078a0b36e1914cef1f9.png)

2. 根目录初始化git
```bash
git init .
```
![](https://img-blog.csdnimg.cn/aa1d36c288764ac09be1259941a783e3.png)



3. 建立开源协议
给项目根目录手动创建LICENSE文件文件，没有后缀名
```bash
MIT License

Copyright (c) 2023 quanyi

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```
注意吧你的`Copyright (c) 2023 quanyi`改成你的时间和名字
![](https://img-blog.csdnimg.cn/352a7a35218b48b0ba075e2848e08703.png)



4. 项目基本搭建完毕，开始你的功能开发吧
![](https://img-blog.csdnimg.cn/ef49675035e0416da896bd6762c1cfcc.png)


5. 功能开发中，建立实时本地软链接进行测试
```bash
npm link
```
会在全局包生成个临时的软链接
![](https://img-blog.csdnimg.cn/050c22765c5643c98aeda31a2c3db577.png)

有了软链接后，在你测试的项目里与软链接达成连接
```bash
npm link 包名
```
![](https://img-blog.csdnimg.cn/151129c48a494130a477fd9bf9e295d9.png)


然后就是在你测试的项目里import

```javascript
import CodeTransforText from "code-transfor-text_vue"



Vue.use(CodeTransforText)
```
使用试试看


6. 测试完毕没问题记得解除你测试项目里的软链接连接
```bash
npm unlink 包名
```
![](https://img-blog.csdnimg.cn/f6ee6ea556b94691884b7ac3308d7bd2.png)

同时存在全局包的软链接记得删除：

![](https://img-blog.csdnimg.cn/5f388752c6c14abe8a711f95e6a78f47.png)



一切准备就绪，可以发布了



7. 如果包比较大想要打包一下，使用该步骤
项目根目录创建`webpack.config.js`文件，写入：

```javascript
const path = require('path');

module.exports = {
  mode: 'production',
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'index.js',
    library: 'CodeTransforText', // 全局挂载包的引用名
    libraryTarget: 'umd', //通用模式：支持用户通过es、common.js、AMD的方式引入npm包
    globalObject: 'this' // 为 webpack 4 新增属性，需要指定 global 的值为 ’this‘，否则会为默认值 ’self‘，无法在 nodejs 环境中使用。
  }
}
```
`package.json`文件配置scripts：

```javascript
"scripts": {
   "build": "webpack"
 },
```
![](https://img-blog.csdnimg.cn/dc6e604f82ad4148b51f5d2844863684.png)


那么此时给项目执行打包
```bash
npm run build
```

可以得出dist/index.js:
![](https://img-blog.csdnimg.cn/215e515c81e24c8080415c4d6dd59a53.png)































# 发布到npm
如果没有npm账号就先[注册npm账号](https://www.npmjs.com/signup)
1. 有的话就登录
```bash
npm login https://www.npmjs.com
```
![](https://img-blog.csdnimg.cn/0817b69e01d845919f40aec7b9c8db38.png)





2. 发布
```bash
npm publish
```
![](https://img-blog.csdnimg.cn/903e66daa6094d6097f1a8918259b608.png)


网络稍有延迟，稍到npm你的账户上看看
![](https://img-blog.csdnimg.cn/45951ea351ce4cfd96d1f693755d0841.png)

# 使用
那么现在就可以下载了
```bash
npm install code-transfor-text_vue
```
![](https://img-blog.csdnimg.cn/d476bc9f09e4468f81275cf0d1fe3c1a.png)












