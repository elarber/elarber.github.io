---
title: 超简单的node爬虫小案例

index_img: https://img-blog.csdnimg.cn/direct/0755084eaa6e4abd87994bd08ae9c8df.png
lazyload: true
categories:
- node
tags:
- node
- 爬虫


---













同[前端爬取](https://blog.csdn.net/qq_42618566/article/details/135567283)参数一样，输入三个参数进行爬取

注意点也一样：
注意分页的字段需要在代码里面定制化修改，根据你爬取的接口，他的业务规则改代码中的字段。比如我这里总条数叫total，人家的不一定。返回的数据我这里是data.rows，看看人家的是叫什么字段，改改代码。再比如我这里的分页叫pageNum，人家的可能叫pageNo


![](https://img-blog.csdnimg.cn/direct/0755084eaa6e4abd87994bd08ae9c8df.png)
data目录手动建立上哦，要放爬下来的数据

# 依赖
```json
{
  "dependencies": {
    "axios": "^1.6.5",
    "colors": "^1.4.0",
    "fs": "^0.0.1-security",
    "readline": "^1.3.0"
  }
}

```

# 代码

```javascript
const readline = require("readline");
const axios = require('axios');
const fs = require("fs");
const colors = require('colors');


// 创建询问实例
let RL = readline.createInterface({
    input: process.stdin,
    output: process.stdout
})

// 封装异步询问
function question(question) {
    return new Promise((resolve, reject) => {
        RL.question(`${question}\t`, function (value) {
            return resolve(value);
        })
    })
}


var total = 0;
var pageNum = 1;
var pageSize = 30;
var api = "";
var headers = "";
var params = "";




// 循环异步方法，执行同步结果
(async function () {
    const questions = ["请输入接口：", "请输入请求头：", "请输入参数："];
    for (let i = 0; i < questions.length; i++) {
        const value = await question(questions[i]);
        if (i === 0) {
            api = value;
        } else if (i === 1) {
            headers = value;
        } else {
            params = value;
        }
    }
    RL.close();
})()

// 监听readline关闭，结束终端输入
RL.on("close", function () {
    console.log(`<<<------------------------- 开始爬取 ------------------------->>>\n`.blue);
    // console.log(api, headers, params);
    crawling();
})


// 封装接口请求
async function getData() {
    const response = await axios({
        url: api,
        method: "post",
        headers: {
            "Content-Type": "application/json",
            ...JSON.parse(headers)
        },
        data: JSON.stringify({
            ...JSON.parse(params),
            "pageSize": pageSize,
            "pageNum": pageNum
        })
    })
    return response.data;
}

// 爬取执行入口
async function crawling() {
    const data = await getData();
    console.log(data);
    if (data.code !== 0) {
        console.log('================= 数据读取失败 ================='.red);
        process.exit(0);
    }

    console.log('================= 数据读取成功 ================='.green);
    total = data.total;
    const page = Math.ceil(total / pageSize);
    console.log(`共${page}页`);
    saveFile(data.rows, `第1页`);
    loading();
}

// 持续执行爬取
async function loading() {
    const page = Math.ceil(total / pageSize);
    for (let i = 1; i < page; i++) {
        pageNum++;
        const data = await getData();
        saveFile(data.rows, `第${i + 1}页`);
    }

    console.log(`<<<------------------------- 爬取完毕，已下载数据 ------------------------->>>\n`.bgGreen);
    total = 0;
    pageNum = 1;
    process.exit(0);
}



// 下载json文件
function saveFile(res, name) {
    console.log(`<<<------------------------- 开始写入 ------------------------->>>\n`.blue);
    console.log(name);
    const writerStream = fs.createWriteStream("data/" + name + ".json");
    writerStream.write(JSON.stringify(res));
    writerStream.end();

    writerStream.on('finish', function () {
        console.log(`<<<------------------------- 写入完成 ------------------------->>>\n`.green);
    });
    writerStream.on('error', function (err) {
        console.log(err);
        console.log(`<<<------------------------- 写入错误 ------------------------->>>\n`.red);
        process.exit(0);
    });
}

```
