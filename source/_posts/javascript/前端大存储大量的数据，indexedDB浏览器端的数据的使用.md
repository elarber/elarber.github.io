---
title: 前端大存储大量的数据，indexedDB浏览器端的数据的使用

index_img: https://img-blog.csdnimg.cn/40ddcd628b974813990ab82e9220574a.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript
- 前端大存储
- indexedDB



---












## 打开数据库，没有的话就会自动创建
打开后会返回有两个事件。  1.`onsuccess`   2.`onerror`

```javascript
// 打开数据库，没有的话就会自动创建
// 打开后会返回有两个事件。  1.onsuccess   2.onerror
const IDB = indexedDB.open('indexeDB-demo');
// 打开数据库成功后自动调用onsuccess事件回调。
IDB.onsuccess = function(e) {
	console.log("success");
};
// 打开数据库失败
IDB.onerror = function(e) {
	console.log(e);
};

// 第一次打开成功后或者版本有变化自动执行以下事件：一般用于初始化数据库。
IDB.onupgradeneeded = function(e) {
	db = e.target.result; // 获取到 indexeDB-demo对应的 IDBDatabase实例,也就是我们的数据库。

	console.log(e);
};
```

![](https://img-blog.csdnimg.cn/40ddcd628b974813990ab82e9220574a.png)


- onsuccess：数据库打开成功或者创建成功后的回调，这里我们将数据库实例返回了出去。
- onerror：数据库打开或创建失败后的回调。
- onupgradeneeded：当数据库版本有变化的时候会执行该函数，比如我们想创建新的存储库（表），就可以在该函数里面操作，更新数据库版本即可。



## 插入数据

