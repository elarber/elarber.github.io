---
title: 前端使用sm2、sm3加密解密 案例

index_img: 
lazyload: true
categories:
- 前端插件使用
tags:
- sm-crypto



---











安装：
` npm install --save sm-crypto `


引入：
```javascript
const sm2 = require('sm-crypto').sm2
const cipherMode = 1 // 1 - C1C3C2，0 - C1C2C3，默认为1
```

加密：

```javascript
let encryptData = sm2.doEncrypt(msgString, publicKey, cipherMode) // 加密结果
conso.log("加密结果：",encryptData);
```
解密：

```javascript
let decryptData sm2.doDecrypt(encryptData, privateKey, cipherMode) // 解密结果
conso.log("解密结果：",encryptData);
```


---

#### npm：[https://www.npmjs.com/package/sm-crypto](https://www.npmjs.com/package/sm-crypto)

