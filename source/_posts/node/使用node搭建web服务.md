---
title: 使用node搭建web服务

index_img: https://img-blog.csdnimg.cn/20210706104939857.png
lazyload: true
categories:
- node
tags:
- node



---











![](https://img-blog.csdnimg.cn/2021070610464493.png)



>  安装 `npm install http`



`server.js`写入以下内容：
```javascript
const http = require('http'); // 引入nodeJS内置的网络传输协议http模块
const server = http.createServer(); //建立服务
const fs=require("fs");


//指定端口号
server.listen(9999, function () {
  console.log('Server running at http://127.0.0.1:9999/');
});
//事件响应
server.on("request", function (request, response) {
  //设置响应的头
  response.writeHead(200,{
    "Content-Type":"text/html; charset=utf-8"
  });
  fs.readFile("./index.html","utf-8",function(err,data){
       if(err) {
         console.log("index.html loading is failed :"+err);
       }else{
         response.end(data);  //返回index.html页面
       }
   });
});

```

启动服务看看

![](https://img-blog.csdnimg.cn/20210706104919606.png)

![](https://img-blog.csdnimg.cn/20210706104939857.png)



