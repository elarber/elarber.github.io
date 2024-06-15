---
title: js 数组转字符串，字符串转数组

index_img: https://img-blog.csdnimg.cn/20201029100122925.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











#### 数组转字符串
```javascript
var arr=["呀覅发","附件我发我","就让我委","那就按嗯"];
			
console.log(arr.join()); //默认按,分割
console.log(arr.join("-"));  //按-分割
console.log(arr.join("/")); // 按/分割
```


![数组转字符串](https://img-blog.csdnimg.cn/20201029095519564.png#pic_center)


---

#### 字符串转数组

```javascript
var str = "拿出来死啊，忘记烦恼是，积分晚礼服你，忘了粉色浪费你发，阿吉尔菲娜另外恶霸，服务冷风撒，放牛娃";
			
console.log(str.split("，"));
```
![字符串转数组](https://img-blog.csdnimg.cn/20201029100122925.png#pic_center)


