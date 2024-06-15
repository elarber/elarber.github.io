---
title: 使用node建立http form提交

index_img: https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412001213301.png
lazyload: true
categories:
- node
tags:
- node



---













```javascript
var http = require('http');
var querystring = require('querystring');

var postHTML = `
  <html>
    <head>
      <meta charset="utf-8">
      <title>菜鸟教程 Node.js 实例</title>
    </head>
    <body>
      <form method="post">
      姓名： <input name="name"><br>
      年纪： <input name="age"><br>
      <input type="submit">
      </form>
    </body>
  </html>`;

http.createServer(function (req, res) {
  var body = "";
  req.on('data', function (chunk) {
    console.log(chunk);
    body += chunk;
  });
  req.on('end', function () {
    body = querystring.parse(body);
    console.log(body);
    res.writeHead(200, { 'Content-Type': 'text/html; charset=utf8' });
    if (body.name && body.age) { // 输出提交的数据
      res.write("姓名：" + body.name);
      res.write("<br>");
      res.write("年纪：" + body.age);
    } else {  // 输出表单
      res.write(postHTML);
    }
    res.end();
  });
}).listen(3000);
```



![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412001140645.png)





![](https://raw.githubusercontent.com/chergn/pictures/main/uPic/image-20240412001213301.png)
