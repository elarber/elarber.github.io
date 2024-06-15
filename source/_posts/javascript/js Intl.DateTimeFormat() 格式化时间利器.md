---
title: js Intl.DateTimeFormat() 格式化时间利器

index_img: https://img-blog.csdnimg.cn/direct/9ee421b3f1dd4224b751f25ec79e10fc.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- 格式化时间



---













![](https://img-blog.csdnimg.cn/direct/9ee421b3f1dd4224b751f25ec79e10fc.png)

# 效果
![](https://img-blog.csdnimg.cn/direct/d11681341a714201bac6d19dbf7c3633.png)

# 案例
```javascript
const options = { year: 'numeric', month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false };
const now = new Intl.DateTimeFormat('zh', options).format(new Date()).replace(/[/]/g,"-")
console.log("当前时间", now);
```


# 配置项：
> [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat#parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat#parameters)
