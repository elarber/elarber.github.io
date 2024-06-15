---
title: node 实现简单爬取文字

index_img: https://img-blog.csdnimg.cn/20200412144544720.png
lazyload: true
categories:
- node
tags:
- node
- 爬虫


---









首先看我的目录结构：
![node 实现简单爬取文字](https://img-blog.csdnimg.cn/20200412144308389.png)

#### index.js代码如下：

```javascript
const cheerio = require('cheerio');
const http = require('http');
const iconv = require('iconv-lite');
const fs = require("fs");
const colors = require('colors');

// 爬取和存入
http.get('http://www.shuoshuodaitupian.com/', function (sres) {
  var chunks = []; // 用来装得到的HTML
  sres.on('data', function (chunk) {
    chunks.push(chunk);
    console.log('<<<------------------------------- 得到html ------------------------------->>>\n'.green);
    console.log("html:\n", chunks.toString(),"\n"); // 输出得到的html看看
  });
  sres.on('end', function () {
    var titles = []; // 用来装摘取的目标元素
    var html = iconv.decode(Buffer.concat(chunks), 'utf-8');
    var $ = cheerio.load(html, {
      decodeEntities: false
    });
    $('#snsBox .item').each(function (index, element) {
      var $element = $(element);
      titles.push({
        text: $element.text()
      });
    });
    console.log('<<<------------------------------- 摘取目标元素完毕 ------------------------------->>>\n'.green);

    /*-------------    存下来     --------------*/
    console.log("目标元素:\n", titles,"\n");
    var writerStream = fs.createWriteStream('data.json');
    writerStream.write(JSON.stringify(titles), 'UTF8');
    writerStream.end();
    // 处理流事件 --> data, end, and error
    writerStream.on('finish', function () {
      console.log('<<<------------------------------- 写入完成 ------------------------------->>>\n'.green);
    });
    writerStream.on('error', function (err) {
      console.log(err.stack);
    });
  });
});
```


#### server.js代码如下：
```javascript
const express = require('express');
const fs = require("fs");
const colors = require('colors');


//-------------    写接口，暴露数据     --------------
// 读取已有的数据
const data = fs.readFileSync('E:/My/nodeJS/capture/data.json').toString();
console.log(data,"\n");
//接口暴露
const app = express();
app.get('/api/data', function (req, res) {
   res.send(data);
});
const server = app.listen(9999, function () {
  console.log("接口地址为：","http://9999/api/data".green);
});
```


**需知：依赖模块没有安装的执行npm安装下**
![node 实现简单爬取文字](https://img-blog.csdnimg.cn/20200412144544720.png)

![node 实现简单爬取文字](https://img-blog.csdnimg.cn/20200412144557165.png)


##### github地址：[https://github.com/frontend-cherry/nodeJS](https://github.com/frontend-cherry/nodeJS)



![node 实现简单爬取文字](https://img-blog.csdnimg.cn/20200501100452773.gif)




